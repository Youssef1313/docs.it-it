---
title: Gestione degli errori
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: f6c0d676a37648678b2b726a46a6238ccc1b3331
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004882"
---
# <a name="error-handling-in-windows-communication-foundation-wcf"></a>Gestione degli errori in Windows Communication Foundation (WCF)

Sono disponibili molti modi per progettare una soluzione di gestione degli errori o delle eccezioni impreviste rilevate in un servizio. Sebbene non esistano soluzioni di gestione degli errori singole "corrette" o "procedure consigliate", esistono più percorsi validi da considerare. Si consiglia in genere di implementare una soluzione ibrida che combina più approcci dall'elenco seguente, a seconda della complessità dell'implementazione WCF, del tipo e della frequenza delle eccezioni, della natura gestita e non gestita del eccezioni ed eventuali requisiti di traccia, registrazione o criteri associati.

Queste soluzioni sono descritte in maggiore dettaglio nella parte restante di questa sezione.

## <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise Library

Il blocco applicativo di gestione delle eccezioni della Microsoft Enterprise Library facilita l'implementazione di modelli di progettazione comuni e la creazione di una strategia coerente per elaborare le eccezioni che si verificano in tutti i livelli dell'architettura di un'applicazione aziendale. È progettato per supportare il codice tipico contenuto nelle istruzioni catch dei componenti di un'applicazione. Anziché ripetere questo codice (ad esempio il codice che registra le informazioni sulle eccezioni) in blocchi catch identici in tutta l'applicazione, il blocco applicativo di gestione delle eccezioni permette agli sviluppatori di incapsulare questa logica sotto forma di gestori riusabili delle eccezioni.

Nella libreria è incluso un gestore di eccezioni del contratto di errore pronto all'uso. Questo gestore di eccezioni è progettato per l'utilizzo in base ai limiti del servizio WCF e genera un nuovo contratto di errore dall'eccezione.

Scopo dei blocchi applicativi è incorporare procedure consigliate di uso comune e offrire un approccio comune per la gestione delle eccezioni nell'intera applicazione. D'altra parte, anche i gestori degli errori e i contratti di errore sviluppati in modo personalizzato possono essere molto utili. I gestori di errori personalizzati, ad esempio, offrono un'ottima opportunità per promuovere automaticamente tutte le eccezioni a FaultExceptions e anche per aggiungere funzionalità di registrazione all'applicazione.

Per ulteriori informazioni, vedere [Microsoft Enterprise Library](https://docs.microsoft.com/previous-versions/msp-n-p/ff632023(v=pandp.10)).

## <a name="dealing-with-expected-exceptions"></a>Gestione delle eccezioni previste

La linea di condotta appropriata consiste nell'intercettare le eccezioni previste in ogni operazione o punto di estendibilità pertinente, decidere se è possibile eseguire il ripristino da e restituire l'errore personalizzato appropriato in FaultException @ no__t-0T >.
  
## <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Gestione di eccezioni impreviste tramite un IErrorHandler

Per gestire le eccezioni impreviste, la procedura consigliata consiste nell'"hook" di un IErrorHandler. I gestori di errori intercettano solo le eccezioni a livello di runtime WCF (il livello "modello di servizio"), non a livello di canale. L'unico modo per collegare un oggetto IErrorHandler a livello di canale consiste nel creare un canale personalizzato, soluzione non consigliabile nella maggior parte degli scenari.

Un'eccezione imprevista non è in genere né un'eccezione irreversibile né un'eccezione di elaborazione; è invece un'eccezione imprevista dell'utente. Un'eccezione irreversibile, ad esempio un'eccezione di memoria insufficiente, che in genere viene gestita automaticamente dal [gestore di eccezioni del modello di servizio](xref:System.ServiceModel.Dispatcher.ExceptionHandler) , in genere non può essere gestita normalmente e l'unico motivo per gestire tale eccezione potrebbe essere registrazione aggiuntiva o per restituire un'eccezione standard al client. Un'eccezione di elaborazione si verifica nell'elaborazione del messaggio, ad esempio a livello di serializzazione, di codificatore o di formattatore, e non può essere gestita con IErrorHandler, poiché in genere avviene troppo presto o troppo tardi nell'elaborazione perché il gestore possa intervenire. Analogamente, le eccezioni di trasporto non possono essere gestite a livello di IErrorHandler.

Con IErrorHandler è possibile controllare in modo esplicito il comportamento dell'applicazione quando viene generata un'eccezione. È possibile:  

1. Decidere se inviare o meno un errore al client.

2. Sostituire un'eccezione con un errore.

3. Sostituire un errore con un altro errore.

4. Eseguire la registrazione o la traccia.

5. Eseguire altre attività personalizzate.

È possibile installare un gestore degli errori personalizzato aggiungendolo alla proprietà ErrorHandlers dei dispatcher del canale per il servizio.  I gestori degli errori possono essere più di uno, nel qual caso vengono chiamati nell'ordine in cui vengono aggiunti alla raccolta.

IErrorHandler.ProvideFault determina il messaggio di errore inviato al client. Questo metodo viene chiamato indipendentemente dal tipo di eccezione generata da un'operazione nel servizio. Se non viene eseguita alcuna operazione, WCF presuppone il comportamento predefinito e continua come se non fossero presenti gestori degli errori personalizzati.

Un caso in cui è possibile usare questo approccio è quando si desidera creare una posizione centrale per la conversione delle eccezioni in errori prima che vengano inviate al client (assicurandosi che l'istanza non venga eliminata e il canale non passi in stato di errore).

Il metodo IErrorHandler.HandleError in genere viene usato per implementare comportamenti correlati agli errori, quali la registrazione degli errori, le notifiche di sistema, l'arresto dell'applicazione e così via. IErrorHandler.HandleError può essere chiamato in più punti nel servizio e, a seconda di dove viene generato l'errore, il metodo HandleError può essere chiamato o meno dallo stesso thread dell'operazione; non è possibile assicurare che questo avvenga sempre.

## <a name="dealing-with-exceptions-outside-wcf"></a>Gestione delle eccezioni all'esterno di WCF

Spesso possono verificarsi eccezioni di configurazione, eccezioni di stringhe di connessione al database e altre simili eccezioni nel contesto di un'applicazione WCF, ma non causate dal modello di servizio o dal servizio Web in sé. Queste eccezioni sono eccezioni "normali" esterne al servizio Web e devono essere gestite in modo analogo alle altre eccezioni esterne nell'ambiente da gestire.

## <a name="tracing-exceptions"></a>Traccia delle eccezioni

La traccia è l'unica posizione "catch-all" in cui è possibile che vengano visualizzate tutte le eccezioni. Per altre informazioni sulla traccia e la registrazione delle eccezioni, vedere Traccia e registrazione.

## <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Errori del modello URI quando si usano WebGetAttribute e WebInvokeAttribute

Con gli attributi WebGet e WebInvoke è possibile specificare un modello URI in cui eseguire il mapping dei componenti dell'indirizzo di richiesta ai parametri dell'operazione. Ad esempio, il modello URI "previsioni/{regione}/{città}" esegue il mapping dell'indirizzo di richiesta in token letterali, un parametro denominato regione e un parametro denominato città. Questi parametri possono quindi essere associati in base al nome ad alcuni dei parametri formali dell'operazione.

I parametri di modello vengono visualizzati sotto forma di stringhe nell'URI mentre i parametri formali di un contratto tipizzato possono essere non di tipo stringa. Pertanto, è necessario effettuare una conversione prima che l'operazione possa essere richiamata. È disponibile una [tabella dei formati di conversione](wcf-web-http-programming-model-overview.md) .

Tuttavia, se la conversione ha esito negativo non è possibile segnalare all'operazione che si è verificato un errore. La conversione dei tipi si manifesta invece sotto forma di errore di invio.

Un errore di invio di conversione dei tipi può essere analizzato in modo analogo a molti altri tipi di errori di invio installando un gestore degli errori. Il punto di estendibilità di IErrorHandler viene chiamato per gestire le eccezioni a livello di servizio. Da quel punto è possibile scegliere la risposta da inviare al chiamante ed eseguire eventuali attività personalizzate e di creazione di rapporti.

## <a name="see-also"></a>Vedere anche

- [Programmazione WCF di base](../basic-wcf-programming.md)
