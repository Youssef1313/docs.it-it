---
title: Canale locale
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714891"
---
# <a name="local-channel"></a>Canale locale
Il canale locale è un canale di trasporto Windows Communication Foundation (WCF) usato per la comunicazione all'interno dello stesso dominio applicazione. È utile negli scenari in cui il client e il servizio sono in esecuzione nello stesso dominio applicazione e l'overhead dello stack di canali WCF tipico (serializzazione e deserializzazione di messaggi) deve essere evitato.  
  
## <a name="demonstrates"></a>Dimostrazione  
 Canale locale  
  
## <a name="discussion"></a>Discussione  
 L'esempio è costituito da due file di progetto:  
  
- **LocalChannel**: rappresentazione a livello di codice del canale locale all'interno del dominio dell'applicazione corrente. In questo progetto il componente di invio posiziona il messaggio in una coda in memoria e il componente ricevente rimuovere il messaggio dalla coda per riceverlo.  
  
- **ClientAndService**: questo progetto ospita un servizio in un'applicazione console e quindi esegue un client per chiamare il servizio dall'interno dello stesso dominio applicazione.  
  
 Per aumentare la velocità, la progettazione del canale locale ignora sia lo stack di canali che il processo di serializzazione. Il canale di trasporto locale viene implementato usando una coda per il trasporto delle chiamate al servizio dal client al servizio e per restituire il valore al client. Anziché parametri di serializzazione e valori restituiti, nell'esempio vengono copiati gli oggetti.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio  
  
1. Compilare ed eseguire la soluzione LocalChannel.  
  
2. L'host del servizio viene iniziato e il client chiama il servizio usando il canale locale. Viene visualizzata una finestra della console contenente i risultati della chiamata al servizio.  
  
> [!IMPORTANT]
> È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi. Questo esempio si trova nella directory seguente.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
