---
title: 'Procedura: abilitare la persistenza per i flussi di lavoro e i relativi servizi'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460888"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Procedura: abilitare la persistenza per i flussi di lavoro e i relativi servizi

In questo argomento viene descritto come abilitare la persistenza dei flussi di lavoro e dei servizi flusso di lavoro.

## <a name="enable-persistence-for-workflows"></a>Abilitare la persistenza dei flussi di lavoro

È possibile associare un archivio di istanze a un **WorkflowApplication** usando la proprietà <xref:System.Activities.WorkflowApplication.InstanceStore%2A> della classe <xref:System.Activities.WorkflowApplication>. Il metodo <xref:System.Activities.WorkflowApplication.Persist%2A> salva o rende persistente un flusso di lavoro nell'archivio di istanze associato all'applicazione. Il metodo <xref:System.Activities.WorkflowApplication.Unload%2A> rende persistente un flusso di lavoro nell'archivio di istanze, quindi scarica l'istanza dalla memoria. Il metodo **Load** carica un flusso di lavoro in memoria usando i dati del flusso di lavoro archiviati nell'archivio di persistenza dell'istanza.

Il metodo di **salvataggio permanente** esegue i passaggi seguenti:

1. Sospende l'utilità di pianificazione del flusso di lavoro e attende finché il flusso di lavoro non entra nello stato inattivo.

2. Rende persistente o salva il flusso di lavoro nell'archivio di persistenza.

3. Riprende l'utilità di pianificazione del flusso di lavoro.

 Il metodo **unload** esegue i passaggi seguenti:

1. Sospende l'utilità di pianificazione del flusso di lavoro e attende finché il flusso di lavoro non entra nello stato inattivo.

2. Rende persistente o salva il flusso di lavoro nell'archivio di persistenza.

3. Elimina l'istanza del flusso di lavoro nella memoria.

Entrambi i metodi di **salvataggio permanente** e di **scaricamento** si bloccherà mentre un flusso di lavoro si trova in un'area di non salvataggio permanente finché il flusso di lavoro non esce dall'area di non salvataggio permanente. Il metodo continua l'operazione di persistenza o di scarico una volta completata l'area di non persistenza. Se l'area di non persistenza non viene completata prima della scadenza del timeout, o se il processo di persistenza impiega molto tempo, verrà generata un'eccezione TimeoutException.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Abilitare la persistenza dei servizi flusso di lavoro nel codice

Il membro **DurableInstancingOptions** della classe <xref:System.ServiceModel.WorkflowServiceHost> dispone di una proprietà denominata **InstanceStore** che è possibile utilizzare per associare un archivio di istanze a **WorkflowServiceHost**.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Quando l'oggetto **WorkflowServiceHost** viene aperto, la persistenza viene abilitata automaticamente se **DurableInstancingOptions. InstanceStore** non è null.

In genere, un comportamento del servizio fornisce l'archivio di istanze concrete da usare con un host del servizio flusso di lavoro usando la proprietà **InstanceStore** . Ad esempio, SqlWorkflowInstanceStoreBehavior crea un'istanza di **SqlWorkflowInstanceStore**, la configura e la assegna a **DurableInstancingOptions. InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Abilitare la persistenza per i servizi flusso di lavoro tramite un file di configurazione dell'applicazione.

È possibile abilitare la persistenza usando un file di configurazione dell'applicazione tramite l'aggiunta al file app.config o web.config del codice riportato di seguito:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
