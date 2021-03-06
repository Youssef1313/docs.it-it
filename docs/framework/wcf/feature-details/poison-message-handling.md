---
title: Gestione dei messaggi non elaborabili
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: 3eba16097648bee1ea80cf62ab3bca900ddf6280
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837350"
---
# <a name="poison-message-handling"></a>Gestione dei messaggi non elaborabili
Un *messaggio non elaborabile* è un messaggio che ha superato il numero massimo di tentativi di recapito all'applicazione. Questa situazione può insorgere quando un'applicazione basata sulla coda non è in grado di elaborare un messaggio a causa di errori. Per far fronte a richieste di affidabilità, un'applicazione in coda riceve messaggi nell'ambito di una transazione. Se la transazione nella quale è stato ricevuto un messaggio in coda viene interrotta, il messaggio resta nella coda, quindi viene eseguito un nuovo tentativo nell'ambito di una nuova transazione. Se il problema che ha determinato l'interruzione della transazione non viene risolto, l'applicazione ricevente può rimanere bloccata in una successione continua di ricezioni e interruzioni dello stesso messaggio fino al raggiungimento del numero massimo di tentativi di recapito. Ne consegue l'impossibilità di elaborare il messaggio.  
  
 Un messaggio può diventare non elaborabile per varie ragioni. Le cause più comuni sono specifiche dell'applicazione. Ad esempio, se un'applicazione legge un messaggio da una coda ed esegue alcune operazioni di elaborazione del database, è possibile che non riesca a ottenere un blocco per il database, causando l'interruzione della transazione. A causa dell'interruzione della transazione del database, il messaggio rimane nella coda e l'applicazione è costretta a rileggerlo una seconda volta e ad eseguire un altro tentativo di acquisire un blocco sul database. I messaggi, inoltre, possono diventare non elaborabili se contengono informazioni non valide. Un ordine di acquisto, ad esempio, potrebbe contenere un numero cliente non valido. In questi casi è possibile che l'applicazione interrompa a ragione la transazione determinando la trasformazione del messaggio in messaggio non elaborabile.  
  
 In rari casi è possibile che i messaggi non vengano inviati all'applicazione. Il livello Windows Communication Foundation (WCF) potrebbe rilevare un problema con il messaggio, ad esempio se il frame del messaggio non è corretto, le credenziali del messaggio non sono collegate o un'intestazione azione non valida. In questi casi l'applicazione non riceve mai il messaggio ma quest'ultimo, pur diventando non elaborabile, può essere elaborato manualmente.  
  
## <a name="handling-poison-messages"></a>Gestione di messaggi non elaborabili  
 In WCF la gestione dei messaggi non elaborabili fornisce un meccanismo in base al quale un'applicazione ricevente gestisce i messaggi che non possono essere inviati all'applicazione o i messaggi inviati all'applicazione, ma che non vengono elaborati a causa di un errore specifico dell'applicazione motivi. La gestione dei messaggi non elaborabili è configurata in base alle proprietà seguenti in ogni associazione in coda disponibile:  
  
- `ReceiveRetryCount`. Valore integer che indica il numero massimo di tentativi di recapito di un messaggio dalla coda dell'applicazione all'applicazione. Il valore predefinito è 5. È sufficiente nei casi in cui un tentativo immediato corregge il problema, ad esempio con un deadlock temporaneo su un database.  
  
- `MaxRetryCycles`. Valore integer che indica il numero massimo di cicli di ripetizione. Un ciclo di ripetizione consiste nel trasferimento di un messaggio dalla coda dell'applicazione alla coda secondaria dei tentativi e, dopo un intervallo di tempo configurabile, dalla coda secondaria dei tentativi alla coda dell'applicazione per tentare di nuovo il recapito. Il valore predefinito è 2. In Windows Vista, il messaggio viene tentato al massimo (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) volte. `MaxRetryCycles` viene ignorato in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- `RetryCycleDelay`. Intervallo di tempo tra cicli di ripetizione. Il valore predefinito è 30 minuti. `MaxRetryCycles` e `RetryCycleDelay` forniscono insieme un meccanismo per risolvere il problema con un nuovo tentativo eseguito dopo un certo tempo. È ad esempio in grado di gestire un set di righe bloccate in un commit di transazioni in sospeso di SQL Server.  
  
- `ReceiveErrorHandling`. Enumerazione che indica l'azione da intraprendere per un messaggio non recapitato dopo il numero massimo di tentativi. I valori possono essere Errore, Rilascia, Rifiuta e Sposta. L'opzione predefinita è Errore.  
  
- Errore. Viene inviato un errore al listener che ha determinato l'errore di `ServiceHost`. È necessario che il messaggio venga rimosso dalla coda dell'applicazione da un meccanismo esterno perché l'applicazione possa continuare a elaborare i messaggi in coda.  
  
- Elimina. Il messaggio non elaborabile viene eliminato e non verrà mai recapitato all'applicazione. Se a questo punto la proprietà `TimeToLive` del messaggio è scaduta, è possibile che il messaggio venga visualizzato nella coda dei messaggi non recapitabili del mittente. In caso contrario, il messaggio non viene visualizzato mai. L'opzione indica che l'utente non ha specificato l'operazione da eseguire in caso di perdita del messaggio.  
  
- Rifiuta. Questa opzione è disponibile solo in Windows Vista. Viene indicato a MSMQ di inviare al gestore code mittente un acknowledgement negativo che indichi che l'applicazione non è in grado di ricevere il messaggio. Il messaggio viene inserito nella coda di messaggi non recapitabili del gestore code mittente.  
  
- Sposta. Questa opzione è disponibile solo in Windows Vista. Il messaggio non elaborabile viene spostato in una coda di messaggi non elaborabili per l'elaborazione successiva da parte di un'applicazione di gestione apposita. La coda di messaggi non elaborabili è una coda secondaria della coda dell'applicazione. Un'applicazione per la gestione di messaggi non elaborabili può essere un servizio WCF che legge i messaggi dalla coda non elaborabile. La coda non elaborabile è una coda secondaria della coda dell'applicazione e può essere risolta come NET. MSMQ://\<*nome computer*>/*applicationQueue*;p Baptiste Oison, dove *nome-* computer è il nome del computer in cui risiede la coda e *applicationQueue* è il nome della coda specifica dell'applicazione.  
  
 Di seguito è indicato il numero massimo di tentativi di recapito possibili per un messaggio:  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) in Windows Vista.  
  
- (ReceiveRetryCount + 1) in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
> Non vengono eseguiti altri tentativi per i messaggi recapitati correttamente.  
  
 Per tenere traccia del numero di tentativi di lettura di un messaggio, Windows Vista mantiene una proprietà durevole del messaggio che conta il numero di interruzioni e una proprietà del conteggio di spostamento che conta il numero di volte in cui il messaggio si sposta tra la coda dell'applicazione e le code secondarie. Il canale WCF utilizza questi per calcolare il numero di tentativi di ricezione e il numero di cicli di ripetizione. In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], il numero di interruzioni viene mantenuto in memoria dal canale WCF e viene reimpostato in caso di errore dell'applicazione. Inoltre, il canale WCF può conservare i conteggi delle interruzioni per un massimo di 256 messaggi in memoria in qualsiasi momento. Se viene letto il 257° messaggio, il messaggio più vecchio viene eliminato dal conteggio.  
  
 Le proprietà del numero di interruzioni e del numero di spostamenti sono a disposizione dell'operazione del servizio mediante il contesto dell'operazione. Nell'esempio di codice seguente viene spiegato come accedervi.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF fornisce due associazioni in coda standard:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Associazione .NET Framework adatta per l'esecuzione di comunicazioni basate su coda con altri endpoint WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Associazione idonea per la comunicazione con applicazioni di accodamento messaggi esistenti.  
  
> [!NOTE]
> È possibile modificare le proprietà in questi binding in base ai requisiti del servizio WCF. L'intero meccanismo di gestione dei messaggi non elaborabili è locale nell'applicazione ricevente. A meno che l'applicazione ricevente non venga arrestata e non venga inviato un acknowledgment negativo al mittente, il processo è invisibile all'applicazione mittente. In questo caso il messaggio viene spostato nella coda dei messaggi non recapitabili del mittente.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Procedura consigliata: gestione di MsmqPoisonMessageException  
 Quando il servizio stabilisce che un messaggio non è elaborabile, il trasporto in coda genera un'eccezione <xref:System.ServiceModel.MsmqPoisonMessageException> contenente il `LookupId` del messaggio non elaborabile.  
  
 Un'applicazione ricevente può implementare l'interfaccia <xref:System.ServiceModel.Dispatcher.IErrorHandler> per gestire qualsiasi errore che l'applicazione richieda. Per ulteriori informazioni, vedere [estensione del controllo sulla gestione degli errori e creazione di report](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 L'applicazione potrebbe richiedere una forma di gestione automatica dei messaggi non elaborabili per spostare tali messaggi in una coda apposita affinché il servizio possa accedere al resto dei messaggi presenti nella coda. L'unico scenario in cui viene utilizzato il meccanismo di gestione degli errori per rimanere in attesa delle eccezioni di messaggi non elaborabili si verifica quanto la proprietà <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> è impostata su <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Nell'esempio di messaggio non elaborabile per Accodamento messaggi 3.0 viene illustrato questo comportamento. Di seguito vengono descritti i passaggi necessari per gestire i messaggi non elaborabili, comprese le procedure consigliate:  
  
1. Assicurarsi che le impostazioni dei messaggi non elaborabili rispettino i requisiti dell'applicazione. Quando si utilizzano le impostazioni, assicurarsi di comprendere le differenze tra le funzionalità di Accodamento messaggi in Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. Se necessario, implementare `IErrorHandler` per gestire gli errori di messaggi non elaborabili. Poiché l'impostazione di `ReceiveErrorHandling` su `Fault` richiede un meccanismo manuale per rimuovere dalla coda il messaggio non elaborabile o per correggere un problema collegato esterno, l'utilizzo tipico consiste nell'implementare `IErrorHandler` quando `ReceiveErrorHandling` è impostato su `Fault`, come illustrato nel codice seguente.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Creare un attributo `PoisonBehaviorAttribute` che possa essere utilizzato dal comportamento del servizio. Il comportamento installa `IErrorHandler` nel dispatcher. Vedere l'esempio di codice seguente.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Assicurarsi che il servizio sia annotato con l'attributo del comportamento non elaborabile.  

 Inoltre, se `ReceiveErrorHandling` è impostato su `Fault`, in `ServiceHost` si verificherà un errore in presenza di un messaggio non elaborabile. È possibile associare l'evento di errore e arrestare il servizio, adottare azioni correttive e riavviare. Ad esempio, è possibile notare `LookupId` in <xref:System.ServiceModel.MsmqPoisonMessageException> propagato in `IErrorHandler` e quando si verifica un errore nell'host del servizio, è possibile utilizzare l'API `System.Messaging` per ricevere il messaggio dalla coda tramite `LookupId`, rimuovere il messaggio dalla coda e archiviarlo in un archivio esterno o in un'altra coda. È quindi possibile riavviare il `ServiceHost` per riprendere l'elaborazione normale. La [gestione dei messaggi non elaborabili in MSMQ 4,0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) illustra questo comportamento.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Timeout della transazione e messaggi non elaborabili  
 È possibile che si verifichi una classe di errori tra il canale del trasporto in coda e il codice utente. Gli errori possono essere rilevati da livelli intermedi, ad esempio il livello di sicurezza del messaggio o la logica di invio del servizio. Ad esempio, un certificato X.509 mancante rilevato nel livello di sicurezza SOAP e un'azione mancante sono casi in cui il messaggio viene inviato all'applicazione. In queste situazioni, il messaggio viene eliminato dal modello del servizio. Poiché il messaggio viene letto in una transazione per la quale non può essere fornito alcun risultato, la transazione alla fine scade, viene interrotta e il messaggio viene nuovamente inserito nella coda. In altre parole, per una determinata classe di errori, la transazione non viene immediatamente interrotta ma resta in attesa fino al timeout della transazione. È possibile modificare il timeout della transazione per un servizio utilizzando <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Per modificare il timeout della transazione a livello di computer, modificare il file Machine. config e impostare il timeout della transazione appropriato. È importante notare che, a seconda del timeout impostato nella transazione, la transazione alla fine viene interrotta e torna alla coda e il relativo numero di interruzioni viene incrementato. Il messaggio diventerà non elaborabile e verranno eseguite le azioni di eliminazione appropriate in base alle impostazioni dell'utente.  
  
## <a name="sessions-and-poison-messages"></a>Sessioni e messaggi non elaborabili  
 Una sessione subisce le stesse procedure di ripetizione e gestione di messaggi non elaborabili di un messaggio singolo. Le proprietà elencate in precedenza per i messaggi non elaborabili sono applicabili all'intera sessione. Ciò significa che l'intera sessione verrà ripetuta e verrà inserita in una coda finale di messaggi non elaborabili o nella coda di messaggi non recapitabili del mittente se il messaggio verrà rifiutato.  
  
## <a name="batching-and-poison-messages"></a>Batch e messaggi non elaborabili  
 Se un messaggio diventa non elaborabile e fa parte di un batch, viene eseguito il rollback dell'intero batch e il canale riprende a leggere i messaggi uno alla volta. Per ulteriori informazioni sulla suddivisione in batch, vedere [invio in batch di messaggi in una transazione](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Gestione di messaggi non elaborabili per messaggi di una coda non elaborabile  
 La gestione di messaggi non elaborabili non termina quando un messaggio viene inserito nella coda di messaggi non elaborabili. I messaggi presenti nella coda di messaggi non elaborabili devono comunque essere letti e gestiti. È possibile utilizzare un sottoinsieme di impostazioni della gestione di messaggi non elaborabili durante la lettura di messaggi dalla coda secondaria non elaborabile finale. Le impostazioni applicabili sono `ReceiveRetryCount` e `ReceiveErrorHandling`. È possibile impostare `ReceiveErrorHandling` su Drop, Reject o Fault. `MaxRetryCycles` viene ignorato e viene generata un'eccezione se `ReceiveErrorHandling` è impostato su Move.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Differenze tra Windows Vista, Windows Server 2003 e Windows XP  
 Come notato più indietro, non tutte le impostazioni della gestione di messaggi non elaborabili sono valide per [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Le seguenti differenze principali tra Accodamento messaggi in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)]e Windows Vista sono rilevanti per la gestione dei messaggi non elaborabili:  
  
- Accodamento messaggi in Windows Vista supporta le code secondarie, mentre [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] non supportano le code secondarie. Le code secondarie vengono utilizzate nella gestione dei messaggi non elaborabili. Le code di tentativi e la coda non elaborabile sono code secondarie della coda dell'applicazione creata in base alle impostazioni di gestione dei messaggi non elaborabili. `MaxRetryCycles` stabilisce il numero delle code secondarie dei tentativi che verranno create. Di conseguenza, in caso di esecuzione in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] o [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` viene ignorato e `ReceiveErrorHandling.Move` non è consentito.  
  
- Accodamento messaggi in Windows Vista supporta il riconoscimento negativo, mentre [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] non lo sono. Un negative acknowledgment dal gestore delle code ricevente determina l'inserimento, da parte del gestore delle code mittente, del messaggio respinto nella coda dei messaggi non recapitabili. Per questa ragione, `ReceiveErrorHandling.Reject` non è consentito con [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Accodamento messaggi in Windows Vista supporta una proprietà del messaggio che mantiene il conteggio del numero di tentativi di recapito dei messaggi. Questa proprietà del numero di interruzioni non è disponibile in [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF mantiene il conteggio delle interruzioni in memoria, pertanto è possibile che questa proprietà non contenga un valore accurato quando lo stesso messaggio viene letto da più di un servizio WCF in una farm.  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica delle code](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Differenze nelle funzionalità di accodamento in Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Specifica e gestione degli errori in contratti e servizi](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
