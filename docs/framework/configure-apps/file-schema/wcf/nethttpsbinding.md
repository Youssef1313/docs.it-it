---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 4e15a52603df12ea3e1332efcf707f7d0c389976
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430253"
---
# <a name="nethttpsbinding"></a>\<netHttpsBinding >
Rappresenta un'associazione che può essere utilizzata da un servizio Windows Communication Foundation (WCF) per configurare ed esporre endpoint in grado di comunicare tramite HTTPS. Nel caso di un contratto duplex, verrà usato Web Sockets. In caso contrario, verrà usato HTTPS.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpsBinding** >  

## <a name="syntax"></a>Sintassi  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
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
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`allowCookies`|Valore booleano che indica se il client accetta cookie e li propaga alle richieste future. Il valore predefinito è `false`.<br /><br /> È possibile usare questa proprietà quando si interagisce con servizi Web ASMX che usano cookie. In questo modo i cookie restituiti dal server vengono copiati automaticamente in tutte le richieste client future per quel servizio.|  
|`bypassProxyOnLocal`|Valore booleano che indica se ignorare il server proxy per indirizzi locali. Il valore predefinito è `false`.<br /><br /> Una risorsa Internet è locale se dispone di un indirizzo locale. Un indirizzo locale è quello che si trova nello stesso computer, nella rete LAN o Intranet locale ed è identificato, sintatticamente, dalla mancanza di un punto (.) come negli URI "http://webserver/" e "http://localhost/".<br /><br /> L'impostazione di questo attributo determina se gli endpoint configurati con BasicHttpBinding usano il server proxy quando accedono alle risorse locali. Se questo attributo è `true`, le richieste alle risorse Internet locali non usano il server proxy. Quando l'attributo è impostato su `true`, usare il nome host invece di localhost se si desidera che i client passino da un proxy per comunicare con servizi nello stesso computer.<br /><br /> Se questo attributo è `false`, tutte le richieste Internet vengono effettuate tramite il server proxy.|  
|`closeTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`hostNameComparisonMode`|Specifica la modalità di confronto del nome host HTTP usata per analizzare gli URI. L'attributo è di tipo <xref:System.ServiceModel.HostNameComparisonMode>, che indica se il nome host viene usato per raggiungere il servizio in caso di corrispondenza nell'URI. Il valore predefinito è <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, che ignora il nome host nella corrispondenza.|  
|`maxBufferPoolSize`|Valore intero che specifica la quantità massima di memoria allocata al gestore dei buffer dei messaggi che riceve i messaggi dal canale. Il valore predefinito è 524.288 (0x80000) byte.<br /><br /> Il gestore dei buffer usa un pool di buffer per ridurre al minimo il costo legato all'utilizzo dei buffer. I buffer sono necessari per elaborare i messaggi provenienti dal servizio quando arrivano dal canale. Se la memoria nel pool di buffer non è sufficiente per elaborare il carico dei messaggi, il gestore dei buffer deve allocare altra memoria dall'heap CLR, aumentando l'overhead della procedura di Garbage Collection. Se la quantità di memoria aggiuntiva allocata in questo modo è notevolmente elevata, ciò significa che le dimensioni del pool di buffer sono troppo ridotte e che per migliorare le prestazioni è possibile allocare più risorse a tale pool mediante l'aumento del limite specificato da questo attributo.|  
|`maxBufferSize`|Un valore intero che specifica la dimensione massima, in byte, di un buffer che memorizza i messaggi mentre vengono elaborati per un endpoint configurato con questa associazione. L'impostazione predefinita è 65.536 byte.|  
|`maxReceivedMessageSize`|Numero intero positivo che definisce la dimensione massima del messaggio, incluse le intestazioni, che può essere ricevuto in canale configurato con questa associazione. Il mittente riceve un errore SOAP se il messaggio è troppo grande per il destinatario. Il destinatario elimina il messaggio e crea una voce dell'evento nel registro di traccia. L'impostazione predefinita è 65.536 byte.|  
|`messageEncoding`|Definisce il codificatore usato per codificare il messaggio SOAP. Di seguito vengono elencati i valori validi:<br /><br /> -Text: usa un codificatore di messaggi di testo.<br />-MTOM: usare un codificatore Message Transmission Organization Mechanism 1,0 (MTOM).<br /><br /> Il valore predefinito è Text. L'attributo è di tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Stringa che contiene il nome della configurazione dell'associazione. Questo valore deve essere univoco perché viene usato per identificare l'associazione. A partire da .NET Framework 4, le associazioni e i comportamenti non devono avere un nome. Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`proxyAddress`|URI che contiene l'indirizzo del proxy HTTP. Se `useSystemWebProxy` è impostato su `true`, questa impostazione deve essere `null`. Il valore predefinito è `null`.|  
|`receiveTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:10:00.|  
|`sendTimeout`|Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio. Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>. L'impostazione predefinita è 00:01:00.|  
|`textEncoding`|Imposta la codifica del set di caratteri da usare per l'emissione dei messaggi nell'associazione. Di seguito vengono elencati i valori validi:<br /><br /> -BigEndianUnicode: codifica BigEndian Unicode.<br />-Unicode: codifica a 16 bit.<br />-UTF8: codifica a 8 bit<br /><br /> Il valore predefinito è UTF8. L'attributo è di tipo <xref:System.Text.Encoding>.|  
|`transferMode`|Valore <xref:System.ServiceModel.TransferMode> valido che specifica se i messaggi vengono memorizzati nel buffer o inviati nel flusso in una richiesta o una risposta.|  
|`useDefaultWebProxy`|Valore booleano che specifica se il proxy HTTP configurato automaticamente del sistema deve essere usato, se disponibile. Il valore predefinito è `true`.|  
|||  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[> di sicurezza \<](security-of-nethttpbinding.md)|Definisce le impostazioni di sicurezza per l'associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>. |  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definisce i vincoli sulla complessità dei messaggi SOAP che possono essere elaborati dagli endpoint configurati con questa associazione. L'elemento è di tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[associazioni di \<>](bindings.md)|Questo elemento contiene una raccolta di associazioni standard e personalizzate.|  
  
## <a name="remarks"></a>Note  
 NetHttpsBinding usa HTTPS come trasporto per l'invio di messaggi. Nel caso di un contratto duplex, verrà usato Web Sockets.  Se si usa un contratto richiesta-risposta, NetHttpsBinding si comporta come BasicHttpsBinding con un codificatore binario.  
  
 Per impostazione predefinita, la sicurezza è disattivata, ma è possibile aggiungerla impostando l'attributo mode dell'elemento figlio [\<security >](security-of-basichttpbinding.md) su un valore diverso da `None`. Per impostazione predefinita usa una codifica dei messaggi "Text" e una codifica del testo UTF-8.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è dimostrato l'uso di <xref:System.ServiceModel.NetHttpBinding> che fornisce la comunicazione HTTPS e la massima interoperabilità con servizi Web di prima e seconda generazione. L'associazione è specificata nei file di configurazione per il client e il servizio. Il tipo di associazione specificato usando l'attributo `binding` dell'elemento `<endpoint>`. Se si desidera configurare l'associazione di base e modificare alcune delle relative impostazioni, è necessario definire una configurazione di associazione. L'endpoint deve fare riferimento alla configurazione di associazione tramite il nome usando l'attributo `bindingConfiguration` dell'elemento `<endpoint>`, come è illustrato nel seguente codice di configurazione del servizio.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>Esempio  
 A partire da .NET Framework 4, le associazioni e i comportamenti non devono avere un nome. La funzionalità dell'esempio precedente può essere eseguita rimuovendo il bindingConfiguration dall'indirizzo endpoint e il nome dall'associazione.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Associazioni](../../../wcf/bindings.md)
- [Configurazione di associazioni fornite dal sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Uso di associazioni per configurare servizi e client](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Binding \<>](bindings.md)
