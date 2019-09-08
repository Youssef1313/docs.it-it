---
title: Associazioni personalizzate
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797228"
---
# <a name="custom-bindings"></a>Associazioni personalizzate

Quando una delle associazioni fornite dal sistema non soddisfa i requisiti del servizio è possibile utilizzare la classe <xref:System.ServiceModel.Channels.CustomBinding>. Tutte le associazioni sono costruite a partire da un set ordinato di elementi di associazione. Le associazioni personalizzate possono essere compilate a partire da un set di elementi di associazione forniti dal sistema oppure possono includere elementi di associazione personalizzati definiti dall'utente. È ad esempio possibile utilizzare elementi di associazione personalizzati per consentire l'utilizzo di nuovi trasporti o codificatori presso un endpoint di servizio. Per esempi funzionanti, vedere [esempi di associazioni personalizzate](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Per ulteriori informazioni, vedere [ \<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).

## <a name="construction-of-a-custom-binding"></a>Costruzione di un'associazione personalizzata

Un'associazione personalizzata viene costruita utilizzando il costruttore <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> a partire da una raccolta di elementi di associazione contenuti in uno stack ordinato nel modo seguente:

- All'inizio si trova un oggetto <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> facoltativo che consente la propagazione delle transazioni.

- Segue quindi un oggetto <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> facoltativo che oltre a una sessione fornisce meccanismi di ordinamento in conformità a quanto definito nella specifica WS-ReliableMessaging. Una sessione può coinvolgere intermediari SOAP e di trasporto.

- Segue quindi un oggetto <xref:System.ServiceModel.Channels.SecurityBindingElement> facoltativo che fornisce alcune funzionalità di sicurezza, fra cui: autorizzazione, autenticazione, protezione e riservatezza.

- La successiva è una classe <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> facoltativa che fornisce la possibilità di avere due modalità comunicazione duplex con un protocollo di trasporto che non supporta a livello nativo la comunicazione duplex, ad esempio il protocollo HTTP.

- La successiva è una classe <xref:System.ServiceModel.Channels.OneWayBindingElement> facoltativa che fornisce comunicazione unidirezionale.

- Il successivo è un elemento di associazione di sicurezza di flusso facoltativo che può essere uno degli elementi seguenti.

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Segue quindi un elemento di associazione obbligatorio di codifica dei messaggi. È possibile utilizzare un codificatore di messaggi personalizzato oppure scegliere fra le tre associazioni di codifica dei messaggi seguenti:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

Segue infine un elemento di trasporto obbligatorio. È possibile utilizzare il proprio trasporto o uno degli elementi di associazione di trasporto seguenti Windows Communication Foundation (WCF) fornisce:

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

Nella tabella seguente viene fornito un riepilogo delle opzioni per ogni livello.

|Livello|Opzioni|Obbligatoria|
|-----------|-------------|--------------|
|Transazioni|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|No|
|Affidabilità|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|No|
|Security|<xref:System.ServiceModel.Channels.SecurityBindingElement>|No|
|Codifica|Testo, binario, MTOM (Message Transmission Optimization Mechanism, meccanismo di ottimizzazione della trasmissione dei messaggi), personalizzato|Sì|
|Trasporto|TCP, HTTP, HTTPS, pipe con nome (anche noto come IPC), Peer-to-peer (P2P), sistema di accodamento dei messaggi (anche noto come MSMQ), personalizzato|Yes|

È inoltre possibile definire elementi di associazione personalizzati e inserirli tra i livelli appena elencati.

## <a name="see-also"></a>Vedere anche

- [Panoramica della creazione di endpoint](../endpoint-creation-overview.md)
- [Uso di associazioni per configurare servizi e client](../using-bindings-to-configure-services-and-clients.md)
- [Associazioni fornite dal sistema](../system-provided-bindings.md)
- [Procedura: Personalizzare un'associazione fornita dal sistema](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [Associazione personalizzata](../samples/custom-binding.md)
