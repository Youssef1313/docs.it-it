---
title: <basicHttpContextBinding>
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: 05c863cf7649546745db270a4b3ac0c638083a85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919870"
---
# <a name="basichttpcontextbinding"></a>\<basicHttpContextBinding>
Specifica un'associazione che fornisce il contesto di scambio dell'associazione <xref:System.ServiceModel.BasicHttpBinding> mediante l'abilitazione dei cookie HTTP come meccanismo di scambio.  
  
 \<system.ServiceModel>  
\<Binding >  
\<basicHttpContextBinding>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<basicHttpContextBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`allowCookies`|Valore booleano che indica se il client accetta cookie e li propaga alle richieste future. Il valore predefinito è `false`.<br /><br /> È possibile usare questa proprietà quando si interagisce con servizi Web ASMX che usano cookie. In questo modo i cookie restituiti dal server vengono copiati automaticamente in tutte le richieste client future per quel servizio.|  
|`bypassProxyOnLocal`|Valore booleano che indica se ignorare il server proxy per indirizzi locali. Il valore predefinito è `false`.<br /><br /> Una risorsa Internet è locale se dispone di un indirizzo locale. Un indirizzo locale è uno nello stesso computer, la LAN o Intranet locale ed è identificato, sintatticamente, dalla mancanza di un punto (.) come negli URI "http://webserver/" e "http://localhost/".<br /><br /> L'impostazione di questo attributo determina se gli endpoint configurati con BasicHttpBinding usano il server proxy quando accedono alle risorse locali. Se questo attributo è `true`, le richieste alle risorse Internet locali non usano il server proxy. Quando l'attributo è impostato su `true`, usare il nome host invece di localhost se si desidera che i client passino da un proxy per comunicare con servizi nello stesso computer.<br /><br /> Se questo attributo è `false`, tutte le richieste Internet vengono effettuate tramite il server proxy.|  
|`closeTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`envelopeVersion`|Specifica la versione di SOAP usata per i messaggi elaborati da questa associazione. L'unico valore valido è Soap11.|  
|`hostNameComparisonMode`|Specifica la modalità di confronto del nome host HTTP usata per analizzare gli URI. L'attributo è di tipo <xref:System.ServiceModel.HostNameComparisonMode>, che indica se il nome host viene usato per raggiungere il servizio in caso di corrispondenza nell'URI. Il valore predefinito è <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, che ignora il nome host nella corrispondenza.|  
|`maxBufferPoolSize`|Valore intero che specifica la quantità massima di memoria allocata al gestore dei buffer dei messaggi che riceve i messaggi dal canale. Il valore predefinito è 524.288 (0x80000) byte.<br /><br /> Il gestore dei buffer usa un pool di buffer per ridurre al minimo il costo legato all'utilizzo dei buffer. I buffer sono necessari per elaborare i messaggi provenienti dal servizio quando arrivano dal canale. Se la memoria nel pool di buffer non è sufficiente per elaborare il carico dei messaggi, il gestore dei buffer deve allocare altra memoria dall'heap CLR, aumentando l'overhead della procedura di Garbage Collection. Se la quantità di memoria aggiuntiva allocata in questo modo è notevolmente elevata, ciò significa che le dimensioni del pool di buffer sono troppo ridotte e che per migliorare le prestazioni è possibile allocare più risorse a tale pool mediante l'aumento del limite specificato da questo attributo.|  
|`maxBufferSize`|Un valore intero che specifica la dimensione massima, in byte, di un buffer che memorizza i messaggi mentre vengono elaborati per un endpoint configurato con questa associazione. L'impostazione predefinita è 65.536 byte.|  
|`maxReceivedMessageSize`|Numero intero positivo che definisce la dimensione massima del messaggio, incluse le intestazioni, che può essere ricevuto in canale configurato con questa associazione. Il mittente riceve un errore SOAP se il messaggio è troppo grande per il destinatario. Il destinatario elimina il messaggio e crea una voce dell'evento nel registro di traccia. L'impostazione predefinita è 65.536 byte.|  
|`messageEncoding`|Definisce il codificatore usato per codificare il messaggio SOAP. Di seguito vengono elencati i valori validi:<br /><br /> Testo Utilizzare un codificatore di messaggi di testo.<br />MTOM Utilizzare un codificatore Message Transmission Organization Mechanism 1,0 (MTOM).<br /><br /> L'impostazione predefinita è Text. L'attributo è di tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|Specifica la versione del messaggio usata dai client e dai servizi configurati con l'associazione. L'attributo è di tipo <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Stringa che contiene il nome della configurazione dell'associazione. Questo valore deve essere univoco perché viene usato per identificare l'associazione. Ciascuna associazione è provvista di un attributo `name` e `namespace` che insieme la identificano in modo univoco nei metadati del servizio. In aggiunta, il nome è univoco fra associazioni dello stesso tipo. A partire da [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], non è necessario che le associazioni e i comportamenti dispongano di un nome. Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Specifica lo spazio dei nomi XML dell'associazione. Il valore predefinito è "http://tempuri.org/Bindings". Ciascuna associazione è provvista di un attributo `name` e `namespace` che insieme la identificano in modo univoco nei metadati del servizio.|  
|`openTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`proxyAddress`|URI che contiene l'indirizzo del proxy HTTP. Se `useSystemWebProxy` è impostato su `true`, questa impostazione deve essere `null`. Il valore predefinito è `null`.|  
|`receiveTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:10:00.|  
|`sendTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`textEncoding`|Imposta la codifica del set di caratteri da usare per l'emissione dei messaggi nell'associazione. Di seguito vengono elencati i valori validi:<br /><br /> BigEndianUnicode Codifica BigEndian Unicode.<br />Unicode codifica a 16 bit.<br />UTF8 codifica a 8 bit<br /><br /> L'impostazione predefinita è UTF8. L'attributo è di tipo <xref:System.Text.Encoding>.|  
|`transferMode`|Valore <xref:System.ServiceModel.TransferMode> valido che specifica se i messaggi vengono memorizzati nel buffer o inviati nel flusso in una richiesta o una risposta.|  
|`useDefaultWebProxy`|Valore booleano che specifica se il proxy HTTP configurato automaticamente del sistema deve essere usato, se disponibile. Il valore predefinito è `true`.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Definisce le impostazioni di sicurezza per l'associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definisce i vincoli sulla complessità dei messaggi SOAP che possono essere elaborati dagli endpoint configurati con questa associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Questo elemento contiene una raccolta di associazioni standard e personalizzate.|  
  
## <a name="remarks"></a>Note  
 Questo elemento di associazione fornisce un livello di protezione e un meccanismo di scambio come parte del contesto per `BasicHttpBinding`.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.BasicHttpContextBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [Associazioni](../../../wcf/bindings.md)
- [Configurazione di associazioni fornite dal sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Uso di associazioni per configurare servizi e client](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
- [\<basicHttpBinding>](basichttpbinding.md)
