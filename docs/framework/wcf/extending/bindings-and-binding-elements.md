---
title: Associazioni ed elementi di associazione
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: d4d69495c1ae19b6799fdb9981f6b332cc2580d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795847"
---
# <a name="bindings-and-binding-elements"></a>Associazioni ed elementi di associazione
Le associazioni sono raccolte di elementi di configurazione speciali, denominati *elementi di associazione*, che vengono valutati dal runtime del servizio ogni volta che viene costruito un endpoint client o di servizio. Il tipo e l'ordine degli elementi di un'associazione determinano la scelta e l'ordine di sovrapposizione dei canali di protocollo e di trasporto dello stack di canali di un endpoint.  
  
 Le associazioni, specialmente le associazioni fornite dal sistema, in genere presentano diverse proprietà di configurazione che riflettono le proprietà degli elementi di associazione incapsulati che più di frequente vengono modificate.  
  
 Ogni associazione deve contenere un solo elemento di associazione di trasporto. Ogni elemento di associazione di trasporto implica un elemento di associazione di codifica dei messaggi predefinito. Per eseguire l'override di questo elemento è possibile aggiungere all'associazione un unico elemento di associazione di codifica dei messaggi. Oltre agli elementi di associazione di trasporto e di codifica, l'associazione può contenere un numero qualsiasi di elementi di associazione di protocollo per soddisfare i requisiti di funzionalità di un servizio nonché per consentire l'invio di messaggi SOAP fra endpoint. Per informazioni dettagliate, vedere [utilizzo delle associazioni per configurare servizi e client](../using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Estensione delle associazioni e degli elementi di associazione  
 Windows Communication Foundation (WCF) include associazioni fornite dal sistema che coprono un'ampia gamma di scenari. Per ulteriori informazioni, vedere [binding forniti dal sistema](../system-provided-bindings.md). In alcuni casi, tuttavia, è necessario creare e utilizzare un'associazione non inclusa in WCF. Negli scenari seguenti occorre creare una nuova associazione.  
  
- Esigenza di utilizzare un nuovo elemento di associazione, ad esempio di trasporto, di codifica o di protocollo. In questo scenario è necessario creare una nuova associazione contenente l'elemento di associazione desiderato. Ad esempio, se si aggiunge un elemento di trasporto UDP `UdpTransportBindingElement` personalizzato occorre creare una nuova associazione per utilizzarlo. Per informazioni sull'esecuzione di questo comportamento mediante <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> il tipo, vedere [associazioni personalizzate](custom-bindings.md).  
  
- Configurazione di elementi di associazione esistenti in modo che le associazioni fornite dal sistema non espongano proprietà pubbliche. Ad esempio, per modificare l'ordine di esecuzione delle operazioni di firma e crittografia è necessario creare una nuova associazione. Per informazioni sull'esecuzione di questo comportamento, [vedere Procedura: Personalizzare un'associazione](how-to-customize-a-system-provided-binding.md)fornita dal sistema.  
  
- Creazione di associazioni standard aziendali che espongono soltanto opzioni di configurazione specifiche. Ad esempio, per creare una versione aziendale dell'associazione <xref:System.ServiceModel.WSHttpBinding> in cui non sia consentito disattivare la protezione è possibile creare una nuova associazione che funziona come l'associazione <xref:System.ServiceModel.WSHttpBinding> ma in cui la protezione sia sempre attiva. Per informazioni dettagliate, vedere [creazione di associazioni definite dall'utente](creating-user-defined-bindings.md).  
  
- Personalizzazione di metadati, quasi sempre allo scopo di configurare o utilizzare un determinato elemento di associazione personalizzato. Per ulteriori informazioni sul supporto dei metadati per associazioni ed elementi di associazione, vedere [supporto di configurazione e metadati](configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Canali, associazioni ed elementi di associazione  
 Le associazioni e gli elementi di associazione rappresentano la connessione tra il modello di programmazione delle applicazioni, che comprende attributi e comportamenti, e il modello di canale, che comprende le factory e i listener, i codificatori di messaggi e le implementazioni di trasporto e di protocollo. In genere gli elementi di associazione e le associazioni vengono implementate per consentire al livello applicazione di utilizzare i canali.  
  
 Il livello di canale scambia messaggi con il livello di servizio e trasporta tali messaggi fra gli endpoint. In un client, il livello di canale è uno stack di channel factory che creano canali per un endpoint di rete. In un servizio, il livello di canale è uno stack di listener di canale che accettano i canali ricevuti presso un endpoint di rete.  
  
 Esistono due tipi generali di canali: canali di protocollo e canali di trasporto. I canali di trasporto sono responsabili per la trasmissione effettiva di un messaggio da un endpoint di rete a un altro. I canali di trasporto devono presentare un codificatore di messaggi predefinito e devono essere in grado di utilizzare un codificatore di messaggi alternativo fornito tramite un elemento di associazione di codifica. Un codificatore di messaggi è responsabile per la trasformazione di un messaggio <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> in una rappresentazione di trasmissione e viceversa. I canali di protocollo sono responsabili per l'implementazione di protocolli a livello SOAP, ad esempio WS-Security o WS-ReliableMessaging.  
  
 Il requisito fondamentale dei canali di trasporto e di protocollo è implementare le interfacce di canale necessarie. Per creare un livello di canale funzionante è necessario associare a queste interfacce vari elementi, fra cui factory e listener. Per usare le implementazioni del canale da WCF, è necessario che siano presenti elementi di associazione <xref:System.ServiceModel.Channels.BindingElement> derivati da per ogni canale e che sia presente un elemento di estensione di binding correlato da includere nei file di configurazione che deriva da <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Come menzionato in precedenza, gli elementi di associazione dei codificatori di messaggi nonché le implementazioni di canali di protocollo e di trasporto possono essere sovrapposti allo scopo di creare uno stack di canali. Il meccanismo utilizzato per organizzare tali elementi in un set ordinato è l'associazione. Le associazioni e gli elementi di associazione rappresentano la connessione fra il modello di programmazione delle applicazioni e il modello di canale. Le implementazioni di canale personalizzate possono essere utilizzate direttamente dal codice. Tuttavia, tali implementazioni possono essere utilizzate dal modello di programmazione del livello di servizio soltanto se i codificatori, i trasporti e i protocolli vengono implementati come elementi di associazione.  
  
 Per informazioni dettagliate sullo sviluppo di canali e sui relativi elementi di associazione, vedere [estensione del livello del canale](extending-the-channel-layer.md).
