---
title: <security> di <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399791"
---
# <a name="security-of-ws2007httpbinding"></a>\<> di sicurezza \<di WS2007HttpBinding >
Rappresenta le impostazioni di sicurezza utilizzate con [ \<](ws2007httpbinding.md) l'elemento di > WS2007HttpBinding.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Binding >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ws2007HttpBinding**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> di sicurezza**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`mode`|Opzionale. Specifica il tipo di sicurezza applicata. Il valore predefinito è `Message`.<br /><br /> L'attributo è di tipo <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Attributo mode  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`None`|La sicurezza è disabilitata.|  
|`Transport`|La sicurezza è fornita mediante HTTPS. Il servizio deve essere configurato con certificati Secure Sockets Layer (SSL). Il messaggio è interamente protetto usando HTTPS e il servizio viene autenticato dal client usando il certificato SSL del servizio. L'autenticazione client viene controllata tramite l' `ClientCredentials` attributo [ \<dell'elemento Transport >](transport-of-ws2007httpbinding.md) .|  
|`Message`|La sicurezza è fornita mediante la sicurezza dei messaggi SOAP. Per impostazione predefinita, il corpo SOAP viene crittografato e firmato. Questa modalità offre varie funzionalità: è ad esempio possibile stabilire se le credenziali del servizio sono disponibili per i client fuori banda nonché specificare il gruppo di algoritmi da usare e il livello di protezione da applicare al corpo del messaggio tramite la proprietà <xref:System.ServiceModel.Security.SecurityMessageProperty>. L'autenticazione client viene eseguita una volta per ogni sessione e i risultati vengono memorizzati nella cache per la durata della sessione.|  
|`TransportWithMessageCredential`|In questa modalità, HTTPS fornisce l'integrità, la riservatezza e l'autenticazione server e client, mentre la sicurezza dei messaggi SOAP fornisce l'autenticazione client. Per impostazione predefinita, l'autenticazione client viene eseguita una volta per ogni sessione e i risultati vengono memorizzati nella cache per la durata della sessione.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|Definisce le impostazioni di sicurezza del trasporto. Questo elemento corrisponde al tipo <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>. Queste impostazioni vengono applicate solo quando la modalità è impostata su Transport.|  
|[\<> messaggi](message-of-ws2007httpbinding.md)|Definisce le impostazioni di sicurezza per il messaggio. Questo elemento corrisponde al tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>. Queste impostazioni non vengono applicate quando la modalità è impostata su Transport.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|Associazione protetta per applicazioni di trasporto HTTP.|  
  
## <a name="remarks"></a>Note  
 Questo elemento è progettato per essere interoperabile con i servizi che implementano le specifiche WS-*. La sicurezza basata sul trasporto di questa associazione è SSL (Secure Sockets Layer) su HTTP, ovvero HTTPS.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Protezione di servizi e client](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associazioni](../../../wcf/bindings.md)
- [Configurazione di associazioni fornite dal sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Uso di associazioni per configurare servizi e client](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
