---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: 2ee9a715929641abc605a31ac00fb154b863cc8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935842"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
Specifica i valori predefiniti usati per iniziare un servizio di conversazione protetta.  
  
 \<system.serviceModel>  
\<Binding >  
\<customBinding>  
\<binding>  
\<security>  
\<secureConversationBootstrap>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|facoltativo. Valore booleano che specifica se è possibile usare un token serializzato nella risposta. Il valore predefinito è `false`. Se si usa un'associazione duplice, l'impostazione assume `true` come valore predefinito e qualsiasi impostazione effettuata sarà ignorata.|  
|`authenticationMode`|Specifica la modalità di autenticazione SOAP usata tra l'iniziatore e il risponditore.<br /><br /> L'impostazione predefinita è sspiNegotiated.<br /><br /> L'attributo è di tipo <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Il gruppo di algoritmi di sicurezza definisce vari algoritmi, fra cui gli algoritmi Canonicalization, Digest, KeyWrap, Signature, Encryption e KeyDerivation. Ciascuno dei gruppi di algoritmi di sicurezza definisce valori per questi parametri diversi. La sicurezza basata su messaggi è ottenuta usando questi algoritmi.<br /><br /> Questo attributo viene usato con una piattaforma differente che usa un set di algoritmi diverso da quello predefinito. Quando si apportano modifiche a questa impostazione, è necessario essere consapevoli dei punti di forza e dei punti di debolezza degli algoritmi pertinenti. L'attributo è di tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Il valore predefinito è `Basic256`.|  
|`includeTimestamp`|Valore booleano che specifica se in ogni messaggio vengono inclusi gli indicatori di data e ora. Il valore predefinito è `true`.|  
|`keyEntropyMode`|Specifica la modalità di calcolo delle chiavi per la sicurezza dei messaggi. Le chiavi possono essere basate solo sul materiale della chiave client, solo sul materiale della chiave del servizio o su una combinazione di entrambi. I valori validi sono:<br /><br /> ClientEntropy La chiave della sessione è basata sul materiale della chiave fornito dal client.<br />ServerEntropy La chiave della sessione è basata sul materiale della chiave fornito dal servizio.<br />CombineEntropy La chiave della sessione è basata sul materiale della chiave fornita dal client e dal servizio.<br /><br /> L'impostazione predefinita è CombinedEntropy.<br /><br /> L'attributo è di tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Imposta l'ordine nel quale gli algoritmi di sicurezza a livello di messaggio vengono applicati al messaggio. Di seguito vengono elencati i valori validi:<br /><br /> -   SignBeforeEncrypt: Prima firmare, quindi crittografare.<br />-   SignBeforeEncryptAndEncryptSignature: Firmare, crittografare e crittografare la firma.<br />EncryptBeforeSign Crittografa prima di tutto, quindi firma.<br /><br /> SignBeforeEncryptAndEncryptSignature è il valore predefinito se si usano i certificati reciproci con WS-Security 1.1.  SignBeforeEncrypt è l'impostazione predefinita con WS-Security 1.0.<br /><br /> L'attributo è di tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Imposta la versione di WS-Security da usare. Di seguito vengono elencati i valori validi:<br /><br /> -   WSSecurityJan2004<br />-   WSSecurityXXX2005<br /><br /> L'impostazione predefinita è WSSecurityXXX2005. L'attributo è di tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Valore booleano che specifica se le chiavi possono essere derivate dalle chiavi di prova originali. Il valore predefinito è `true`.|  
|`requireSecurityContextCancellation`|Valore booleano che specifica se il contesto di sicurezza deve essere annullato e terminato nel caso in cui non sia più richiesto. Il valore predefinito è `true`.|  
|`requireSignatureConfirmation`|Valore booleano che specifica se la conferma della firma WS-Security è attivata. Quando è impostato su `true`, le firme del messaggio vengono confermate dal responder. Il valore predefinito è `false`.<br /><br /> La conferma della firma è usata per confermare che la risposta del servizio sia completamente compatibile con una richiesta.|  
|`securityHeaderLayout`|Specifica l'ordine degli elementi nell'intestazione di sicurezza. I valori validi sono:<br /><br /> Strict. Gli elementi vengono aggiunti all'intestazione di sicurezza secondo il principio generale di "dichiarazione prima dell'uso".<br />LAX. Gli elementi vengono aggiunti all'intestazione di sicurezza in qualsiasi ordine conforme alla specifica WSS: SOAP Message Security.<br />- LaxWithTimestampFirst. Gli elementi vengono aggiunti all'intestazione di sicurezza in qualsiasi ordine conforme alla specifica WSS: SOAP Message Security, con la differenza che il primo elemento dell'intestazione di sicurezza deve essere un elemento wsse:Timestamp.<br />- LaxWithTimestampLast. Gli elementi vengono aggiunti all'intestazione di sicurezza in qualsiasi ordine conforme alla specifica WSS: SOAP Message Security, con la differenza che l'ultimo elemento dell'intestazione di sicurezza deve essere un elemento wsse:Timestamp.<br /><br /> L'impostazione predefinita è Strict.<br /><br /> L'elemento è di tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Specifica un token corrente rilasciato. L'elemento è di tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Specifica le impostazioni di sicurezza di un client locale per questa associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Specifica le impostazioni di sicurezza di un servizio locale per questa associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Specifica le opzioni di sicurezza di un'associazione personalizzata.|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associazioni](../../../wcf/bindings.md)
- [Estensione delle associazioni](../../../wcf/extending/extending-bindings.md)
- [Associazioni personalizzate](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Procedura: Creare un'associazione personalizzata usando SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Sicurezza delle associazioni personalizzate](../../../wcf/samples/custom-binding-security.md)
