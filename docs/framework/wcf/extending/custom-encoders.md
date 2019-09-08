---
title: Codificatori personalizzati
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 586207af0bfbe106512dfb61ee7439d4f5ce64c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797210"
---
# <a name="custom-encoders"></a>Codificatori personalizzati
In questo argomento verranno illustrate le procedure per creare codificatori personalizzati.  
  
 In Windows Communication Foundation (WCF) si utilizza un' *associazione* per specificare come trasferire i dati attraverso una rete tra endpoint. Un'associazione è costituita da una sequenza di *elementi di associazione*. Un'associazione include elementi di associazione di protocollo facoltativi, ad esempio sicurezza, un elemento di associazione del *codificatore di messaggi* obbligatorio e un elemento di associazione del trasporto obbligatorio. Un codificatore di messaggi è rappresentato da un elemento di associazione di codifica dei messaggi. In WCF sono inclusi tre codificatori di messaggi: Binary, MTOM (Message Transmission Optimization Mechanism) e Text.  
  
 Un elemento di associazione di codifica dei messaggi serializza un oggetto <xref:System.ServiceModel.Channels.Message> in uscita e lo passa al trasporto oppure riceve dal trasporto il formato serializzato di un messaggio e lo passa al livello protocollo o, se non è presente, all'applicazione.  
  
 I codificatori di messaggi trasformano le istanze <xref:System.ServiceModel.Channels.Message> da e in una rappresentazione di trasmissione. Anche se si ritiene che i codificatori risiedano sopra il livello trasporto nello stack del canale, essi risiedono all'interno del livello trasporto. I trasporti (ad esempio HTTP) formattano il messaggio in base ai requisiti dello standard di trasporto. I codificatori (ad esempio Text/XML) si limitano a codificare il messaggio.  
  
 Quando si esegue la connessione a un client o server esistente, può non essere possibile scegliere un determinato tipo di codifica dei messaggi. Tuttavia, i servizi WCF possono essere resi accessibili tramite più endpoint, ognuno con un codificatore di messaggi diverso. Quando un singolo codificatore non include tutti i destinatari del servizio, è consigliabile esporre il servizio su più endpoint. Le applicazioni client potranno quindi scegliere l'endpoint più appropriato. L'utilizzo di più endpoint consente di combinare i vantaggi di differenti codificatori di messaggi con altri elementi di associazione.  
  
## <a name="system-provided-encoders"></a>Codificatori forniti dal sistema  
 In WCF sono disponibili diverse associazioni fornite dal sistema progettate per coprire gli scenari di applicazione più comuni. Ognuna di queste associazioni combina un trasporto, un codificatore di messaggi e altre opzioni (ad esempio quelle relative alla protezione). In questo argomento viene descritto come estendere `Text`i `Binary`codificatori `MTOM` di messaggi, e inclusi in WCF oppure creare un codificatore personalizzato. Il codificatore dei messaggi di testo supporta sia la codifica XML semplice che le codifiche SOAP. La modalità di codifica XML semplice del codificatore dei messaggi di testo è denominata POX (Plain Old XML) per distinguerla dalla codifica SOAP basata su testo.  
  
 Per ulteriori informazioni sulle combinazioni di elementi di associazione forniti dalle associazioni fornite dal sistema, vedere la sezione corrispondente in scelta di [un trasporto](../feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Come usare i codificatori forniti dal sistema  
 Una codifica viene aggiunta a un'associazione usando una classe derivata da <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 In WCF sono disponibili i seguenti tipi di elementi di associazione <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> derivati dalla classe che è in grado di fornire per la codifica di testo, binaria e MTOM (Message Transmission Optimization Mechanism):  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Il codificatore più interoperativo, ma il meno efficiente, per i messaggi XML. In genere un servizio Web o un client di servizio Web è in grado di comprendere codice XML in formato testo. La trasmissione di grandi blocchi di dati binari in formato testo non è tuttavia efficiente.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Rappresenta l'elemento di associazione che specifica la codifica dei caratteri e la versione dei messaggi utilizzati per i messaggi XML basati su binari. Si tratta di una scelta più efficiente tra le opzioni di codifica, ma la meno interoperativa, perché è supportata solo dagli endpoint WCF.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Rappresenta l'elemento di associazione che specifica la codifica dei caratteri e la versione dei messaggi utilizzati per un messaggio utilizzando una codifica Message Transmission Optimization Mechanism (MTOM). MTOM è una tecnologia efficiente per la trasmissione di dati binari nei messaggi di WCF. Il codificatore MTOM cerca un equilibrio tra efficienza e interoperabilità. La codifica MTOM trasmette la maggior parte del codice XML in formato testo, ma ottimizza grandi blocchi di dati binari trasmettendoli senza introdurre modifiche e senza convertirli in formato testo.  
  
 L'elemento di associazione crea una classe <xref:System.ServiceModel.Channels.MessageEncoderFactory>di tipo Text, Binary o MTOM. La factory crea un'istanza <xref:System.ServiceModel.Channels.MessageEncoderFactory> di tipo Text, Binary o MTOM. In genere è presente una sola istanza. Se tuttavia vengono usate le sessioni, a ogni sessione può essere fornito un codificatore diverso. In questo modo il codificatore dei messaggi in formato binario è in grado di coordinare dizionari dinamici (vedere Infrastruttura XML).  
  
 I metodi <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> e <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> rappresentano il nucleo centrale dei codificatori. I metodi consentono la lettura di un messaggio da un flusso o da una matrice <xref:System.Byte>. Le matrici di byte vengono usate quando il trasporto viene eseguito in modalità di memorizzazione nel buffer. I messaggi vengono sempre scritti in flussi. Se deve memorizzare il messaggio nel buffer, il trasporto fornisce un flusso che esegue la memorizzazione nel buffer.  
  
 Gli altri membri usano contenuto, tipi di supporto e proprietà <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A> di supporto. Il trasporto chiama questi metodi di codifica per verificare se il messaggio in ingresso può essere decodificato dal codificatore o per determinare se il messaggio in uscita è valido per questo codificatore.  
  
 Ognuna delle tre implementazioni del codificatore aggiunge proprietà attinenti alle codifiche specifiche ed è completamente configurabile. I codificatori espongono inoltre quote di lettore che hanno impostazioni predefinite protette. Per una descrizione delle quote, vedere Infrastruttura XML.  
  
## <a name="features-of-system-provided-encoders"></a>Funzionalità dei codificatori forniti dal sistema  
 I codificatori di sistema forniscono una serie di funzionalità.  
  
### <a name="pooling"></a>Pooling  
 Ognuna delle implementazioni del codificatore tenta di eseguire il massimo numero possibile di operazioni pooling. La riduzione delle allocazioni è la misura più comunemente adottata per migliorare le prestazioni del codice gestito. Per eseguire queste operazioni di pooling le implementazioni usano la classe `SynchronizedPool`. Il file C# contiene una descrizione delle ottimizzazioni aggiuntive usate da questa classe.  
  
 Le istanze <xref:System.Xml.XmlDictionaryReader> e <xref:System.Xml.XmlDictionaryWriter> vengono inserite nel pool e reinizializzate per impedire l'allocazione di nuove istanze per ogni messaggio. Per i lettori, un callback `OnClose` richiede il lettore quando viene chiamato `Close()`. Il codificatore ricicla inoltre alcuni oggetti di stato dei messaggi usati durante la costruzione dei messaggi. Le dimensioni di questi pool sono configurabili mediante le proprietà `MaxReadPoolSize` e `MaxWritePoolSize` in ognuna delle tre classi derivata da <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Codifica binaria  
 Quando la codifica binaria usa sessioni, la stringa del dizionario dinamica deve essere comunicata al destinatario del messaggio. Questa operazione viene eseguita anteponendo al messaggio le stringhe del dizionario dinamiche. Il destinatario rimuove le stringhe, le aggiunge alla sessione ed elabora il messaggio. Perché le stringhe del dizionario vengano passate correttamente è necessario che il trasporto venga memorizzato nel buffer.  
  
 Le stringhe vengono aggiunte al messaggio da un metodo `AddSessionInformationToMessage` interno. Questo metodo aggiunge le stringhe in formato UTF-8 davanti al messaggio precedute dalla relativa lunghezza. All'intera intestazione del dizionario viene quindi anteposta la lunghezza dei relativi dati. L'operazione inversa viene eseguita da un metodo `ExtractSessionInformationFromMessage` interno.  
  
 Oltre a elaborare chiavi di dizionario dinamiche, i messaggi con sessione memorizzati nel buffer vengono ricevuti in modo univoco. Anziché creare un lettore sul documento ed elaborarlo, il codificatore binario usa la classe `MessagePatterns` interna per scomporre il flusso binario. L'idea è che la maggior parte dei messaggi disponga di un determinato set di intestazioni che vengono visualizzate in un determinato ordine quando vengono generate da WCF. Il sistema del modello divide in due il messaggio in base a quanto previsto. In caso di esito positivo, inizializza un oggetto <xref:System.ServiceModel.Channels.MessageHeaders> senza analizzare il codice XML. In caso contrario ricorre al metodo standard.  
  
### <a name="mtom-encoding"></a>Codifica MTOM  
 La classe <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> dispone di una proprietà di configurazione aggiuntiva denominata <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. Questa proprietà impone un limite massimo alla quantità di dati che è consentito memorizzare nel buffer durante il processo di lettura di un messaggio. In alcuni casi gli Infoset XML (insiemi di informazioni XML) o altre parti MIME devono essere memorizzati nel buffer per riunire tutte le parti MIME in un unico messaggio.  
  
 Per usare correttamente il protocollo HTTP, la classe del codificatore di messaggi MTOM interna fornisce alcune API interne per il metodo `GetContentType` (interno) e `WriteMessage`, un metodo pubblico che può essere sottoposto a override. Per garantire che i valori dell'intestazione HTTP concordino con i valori delle intestazioni MIME deve verificarsi un numero maggiore di comunicazioni.  
  
 Internamente, il codificatore di messaggi MTOM utilizza i reader di testo di WCF ed è simile al codificatore di testo. La differenza principale risiede nel fatto che il codificatore MTOM ottimizza grandi blocchi di oggetti binari o BLOB (Binary Large Object) non convertendoli nella codifica Base 64 prima che vengano integrati nei byte del messaggio. Questi oggetti BLOB rimangono invece estratti e vengono denominati allegati MIME.  
  
## <a name="writing-your-own-encoder"></a>Creazione di un codificatore personalizzato  
 Per implementare un codificatore di messaggi personalizzato, è necessario fornire implementazioni personalizzate delle classi base astratte seguenti:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder>  
  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 La conversione dalla rappresentazione in memoria di un messaggio a una rappresentazione che può essere scritta in un flusso viene incapsulata all'interno della classe <xref:System.ServiceModel.Channels.MessageEncoder> che funziona come una factory per i lettori e i writer XML che supportano tipi specifici di codifiche XML.  
  
- I metodi principali di questa classe di cui è necessario eseguire l'override sono:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> che accetta un oggetto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> e lo scrive in un oggetto <xref:System.IO.Stream>.  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> che accetta un oggetto <xref:System.IO.Stream> e una dimensione di intestazione massima e restituisce un oggetto <xref:System.ServiceModel.Channels.Message>.  
  
 È il codice scritto in questi metodi che gestisce la conversione tra il protocollo di trasporto standard e la codifica personalizzata.  
  
 Successivamente sarà necessario codificare una classe factory che crei il codificatore personalizzato. Eseguire l'override di <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> per restituire un'istanza del codificatore <xref:System.ServiceModel.Channels.MessageEncoder> personalizzato.  
  
 Associare quindi il codificatore <xref:System.ServiceModel.Channels.MessageEncoderFactory> personalizzato allo stack dell'elemento di associazione usato per configurare il servizio o il client eseguendo l'override del metodo <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> per restituire un'istanza di questa factory.  
  
 Con WCF sono disponibili due esempi che illustrano questo processo con il codice di esempio: [Codificatore di messaggi personalizzato: Codificatore](../samples/custom-message-encoder-custom-text-encoder.md) di testo [personalizzato e codificatore di messaggi personalizzato: Codificatore](../samples/custom-message-encoder-compression-encoder.md)di compressione.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Panoramica dell'architettura di trasferimento dati](../feature-details/data-transfer-architectural-overview.md)
- [Scelta di un codificatore di messaggi](../feature-details/choosing-a-message-encoder.md)
- [Scelta di un trasporto](../feature-details/choosing-a-transport.md)
