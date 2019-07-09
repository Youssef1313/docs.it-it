---
title: Istanze del flusso di lavoro non persistenti
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 315d791585ace6ce4adf281abbba0a4c8c72d75a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663040"
---
# <a name="non-persisted-workflow-instances"></a>Istanze del flusso di lavoro non persistenti

Quando viene creata una nuova istanza di un flusso di lavoro che mantiene persistente lo stato in <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, nell'host del servizio viene creata una voce per il servizio specifico nell'archivio di istanze. Successivamente, quando l'istanza del flusso di lavoro viene resa persistente per la prima volta, in <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> viene archiviato lo stato dell'istanza corrente. Se il flusso di lavoro è ospitato nel servizio Attivazione processo Windows, anche i dati della distribuzione del servizio vengono scritti nell'archivio di istanze quando l'istanza è stata resa persistente per la prima volta.

Fino a quando non è stata resa persistente l'istanza del flusso di lavoro, è in un **non persistenti** dello stato. In questo stato non è possibile recuperare l'istanza del flusso di lavoro dopo un riciclo del dominio applicazione oppure un errore dell'host o del computer.

## <a name="the-non-persisted-state"></a>Stato non persistente

Le istanze del flusso di lavoro durevoli che non sono ancora state rese persistenti rimangono in uno stato non persistente nei casi seguenti:

- L'host del servizio si arresta in modo anomalo prima che l'istanza del flusso di lavoro venga resa persistente per la prima volta. L'istanza rimane nell'archivio di istanze e non viene recuperata. In caso di arrivo di un messaggio correlato, l'istanza del flusso di lavoro diventa nuovamente attiva.

- Si verifica un'eccezione dell'istanza del flusso di lavoro prima che questa venga resa persistente per la prima volta. A seconda dell'elemento <xref:System.Activities.UnhandledExceptionAction> restituito, possono verificarsi gli scenari seguenti.

  - <xref:System.Activities.UnhandledExceptionAction> è impostato su <xref:System.Activities.UnhandledExceptionAction.Abort>: Quando si verifica un'eccezione, informazioni sulla distribuzione di servizio viene scritto nell'archivio di istanze e l'istanza del flusso di lavoro viene scaricata dalla memoria. L'istanza del flusso di lavoro rimane in uno stato non persistente e non può essere ricaricata.

  - <xref:System.Activities.UnhandledExceptionAction> è impostato su <xref:System.Activities.UnhandledExceptionAction.Cancel> o <xref:System.Activities.UnhandledExceptionAction.Terminate>: Quando si verifica un'eccezione, informazioni sulla distribuzione di servizio vengono scritte nell'archivio di istanze e lo stato dell'istanza attività è impostato su <xref:System.Activities.ActivityInstanceState.Closed>.

Per ridurre il rischio di incontrare istanze del flusso di lavoro scaricate e non persistenti, si consiglia di rendere persistente il flusso di lavoro nelle fasi iniziali del ciclo di vita.

## <a name="detection-and-removal-of-non-persisted-instances"></a>Rilevamento e rimozione di istanze non persistenti

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> non rimuove alcuna istanza del flusso di lavoro non persistente dall'archivio di istanze né rimuove alcun proprietario del blocco scaduto a cui sono associate istanze del flusso di lavoro non persistenti.

Si consiglia all'amministratore di verificare periodicamente nell'archivio di istanze la presenza di istanze non persistenti. Gli amministratori possono rimuovere tali istanze dall'archivio finché sono certi che il flusso di lavoro specifico non riceverà messaggi correlati. Ad esempio, se l'istanza è presente nel database da diversi mesi e si è a conoscenza che il flusso di lavoro ha in genere una durata di alcuni giorni, è possibile presupporre con sicurezza che si tratta di un'istanza non inizializzata che si era arrestata in modo anomalo.

Per trovare istanze non persistenti nell'archivio di istanze del flusso di lavoro di SQL, è possibile usare le query SQL seguenti:

- Questa query trova tutte le istanze che non sono state rese persistenti e restituisce l'ID e l'ora di creazione (ora UTC) relativi.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- Questa query trova tutte le istanze che non sono state rese persistenti e che non sono caricate e restituisce l'ID e l'ora di creazione (ora UTC) relativi.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- Questa query trova tutte le istanze sospese che non sono state rese persistenti e restituisce l'ID, l'ora di creazione (ora UTC), il motivo della sospensione e il nome dell'eccezione relativi.

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

È necessario prestare attenzione quando si eliminano istanze non persistenti. In generale, è consigliabile rimuovere le istanze non persistenti create da <xref:System.ServiceModel.Activities.WorkflowServiceHost> che sono sospese o non caricate. Tali istanze specifiche possono essere eliminate dall'archivio rimuovendole dalla visualizzazione `[System.Activities.DurableInstancing].[Instances]` tramite il comando SQL seguente, sostituendo l'ID istanza corretto.

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> Non è consigliabile rimuovere tutte le istanze non persistenti perché potrebbero venire incluse istanze appena create non ancora rese persistenti.
