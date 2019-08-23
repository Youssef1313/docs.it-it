---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 7f4bde18876c5e65adf3da100f180b9b18892d98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933094"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="853eb-101">\<netHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="853eb-101">\<netHttpsBinding></span></span>
<span data-ttu-id="853eb-102">Rappresenta un'associazione che può essere utilizzata da un servizio Windows Communication Foundation (WCF) per configurare ed esporre endpoint in grado di comunicare tramite HTTPS.</span><span class="sxs-lookup"><span data-stu-id="853eb-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="853eb-103">Nel caso di un contratto duplex, verrà usato Web Sockets. In caso contrario, verrà usato HTTPS.</span><span class="sxs-lookup"><span data-stu-id="853eb-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="853eb-104">Elemento radice</span><span class="sxs-lookup"><span data-stu-id="853eb-104">Root Element</span></span>  
<span data-ttu-id="853eb-105">Elemento Next</span><span class="sxs-lookup"><span data-stu-id="853eb-105">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="853eb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="853eb-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="853eb-107">Type</span><span class="sxs-lookup"><span data-stu-id="853eb-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="853eb-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="853eb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="853eb-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="853eb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="853eb-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="853eb-110">Attributes</span></span>  
  
|<span data-ttu-id="853eb-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="853eb-111">Attribute</span></span>|<span data-ttu-id="853eb-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="853eb-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="853eb-113">Valore booleano che indica se il client accetta cookie e li propaga alle richieste future.</span><span class="sxs-lookup"><span data-stu-id="853eb-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="853eb-114">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="853eb-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="853eb-115">È possibile usare questa proprietà quando si interagisce con servizi Web ASMX che usano cookie.</span><span class="sxs-lookup"><span data-stu-id="853eb-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="853eb-116">In questo modo i cookie restituiti dal server vengono copiati automaticamente in tutte le richieste client future per quel servizio.</span><span class="sxs-lookup"><span data-stu-id="853eb-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="853eb-117">Valore booleano che indica se ignorare il server proxy per indirizzi locali.</span><span class="sxs-lookup"><span data-stu-id="853eb-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="853eb-118">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="853eb-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="853eb-119">Una risorsa Internet è locale se dispone di un indirizzo locale.</span><span class="sxs-lookup"><span data-stu-id="853eb-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="853eb-120">Un indirizzo locale è uno nello stesso computer, la LAN o Intranet locale ed è identificato, sintatticamente, dalla mancanza di un punto (.) come negli URI "http://webserver/" e "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="853eb-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="853eb-121">L'impostazione di questo attributo determina se gli endpoint configurati con BasicHttpBinding usano il server proxy quando accedono alle risorse locali.</span><span class="sxs-lookup"><span data-stu-id="853eb-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="853eb-122">Se questo attributo è `true`, le richieste alle risorse Internet locali non usano il server proxy.</span><span class="sxs-lookup"><span data-stu-id="853eb-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="853eb-123">Quando l'attributo è impostato su `true`, usare il nome host invece di localhost se si desidera che i client passino da un proxy per comunicare con servizi nello stesso computer.</span><span class="sxs-lookup"><span data-stu-id="853eb-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="853eb-124">Se questo attributo è `false`, tutte le richieste Internet vengono effettuate tramite il server proxy.</span><span class="sxs-lookup"><span data-stu-id="853eb-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="853eb-125">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="853eb-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="853eb-126">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="853eb-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="853eb-127">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="853eb-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="853eb-128">Specifica la modalità di confronto del nome host HTTP usata per analizzare gli URI.</span><span class="sxs-lookup"><span data-stu-id="853eb-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="853eb-129">L'attributo è di tipo <xref:System.ServiceModel.HostNameComparisonMode>, che indica se il nome host viene usato per raggiungere il servizio in caso di corrispondenza nell'URI.</span><span class="sxs-lookup"><span data-stu-id="853eb-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="853eb-130">Il valore predefinito è <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, che ignora il nome host nella corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="853eb-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="853eb-131">Valore intero che specifica la quantità massima di memoria allocata al gestore dei buffer dei messaggi che riceve i messaggi dal canale.</span><span class="sxs-lookup"><span data-stu-id="853eb-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="853eb-132">Il valore predefinito è 524.288 (0x80000) byte.</span><span class="sxs-lookup"><span data-stu-id="853eb-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="853eb-133">Il gestore dei buffer usa un pool di buffer per ridurre al minimo il costo legato all'utilizzo dei buffer.</span><span class="sxs-lookup"><span data-stu-id="853eb-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="853eb-134">I buffer sono necessari per elaborare i messaggi provenienti dal servizio quando arrivano dal canale.</span><span class="sxs-lookup"><span data-stu-id="853eb-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="853eb-135">Se la memoria nel pool di buffer non è sufficiente per elaborare il carico dei messaggi, il gestore dei buffer deve allocare altra memoria dall'heap CLR, aumentando l'overhead della procedura di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="853eb-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="853eb-136">Se la quantità di memoria aggiuntiva allocata in questo modo è notevolmente elevata, ciò significa che le dimensioni del pool di buffer sono troppo ridotte e che per migliorare le prestazioni è possibile allocare più risorse a tale pool mediante l'aumento del limite specificato da questo attributo.</span><span class="sxs-lookup"><span data-stu-id="853eb-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="853eb-137">Un valore intero che specifica la dimensione massima, in byte, di un buffer che memorizza i messaggi mentre vengono elaborati per un endpoint configurato con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="853eb-138">L'impostazione predefinita è 65.536 byte.</span><span class="sxs-lookup"><span data-stu-id="853eb-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="853eb-139">Numero intero positivo che definisce la dimensione massima del messaggio, incluse le intestazioni, che può essere ricevuto in canale configurato con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="853eb-140">Il mittente riceve un errore SOAP se il messaggio è troppo grande per il destinatario.</span><span class="sxs-lookup"><span data-stu-id="853eb-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="853eb-141">Il destinatario elimina il messaggio e crea una voce dell'evento nel registro di traccia.</span><span class="sxs-lookup"><span data-stu-id="853eb-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="853eb-142">L'impostazione predefinita è 65.536 byte.</span><span class="sxs-lookup"><span data-stu-id="853eb-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="853eb-143">Definisce il codificatore usato per codificare il messaggio SOAP.</span><span class="sxs-lookup"><span data-stu-id="853eb-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="853eb-144">Di seguito vengono elencati i valori validi:</span><span class="sxs-lookup"><span data-stu-id="853eb-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="853eb-145">Testo Utilizzare un codificatore di messaggi di testo.</span><span class="sxs-lookup"><span data-stu-id="853eb-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="853eb-146">MTOM Utilizzare un codificatore Message Transmission Organization Mechanism 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="853eb-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="853eb-147">L'impostazione predefinita è Text.</span><span class="sxs-lookup"><span data-stu-id="853eb-147">The default is Text.</span></span> <span data-ttu-id="853eb-148">L'attributo è di tipo <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="853eb-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="853eb-149">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="853eb-150">Questo valore deve essere univoco perché viene usato per identificare l'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="853eb-151">Ciascuna associazione è provvista di un attributo `name` e `namespace` che insieme la identificano in modo univoco nei metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="853eb-151">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="853eb-152">In aggiunta, il nome è univoco fra associazioni dello stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="853eb-152">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="853eb-153">A partire da [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], non è necessario che le associazioni e i comportamenti dispongano di un nome.</span><span class="sxs-lookup"><span data-stu-id="853eb-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="853eb-154">Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="853eb-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="853eb-155">Specifica lo spazio dei nomi XML dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-155">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="853eb-156">Il valore predefinito è "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="853eb-156">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="853eb-157">Ciascuna associazione è provvista di un attributo `name` e `namespace` che insieme la identificano in modo univoco nei metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="853eb-157">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="853eb-158">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="853eb-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="853eb-159">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="853eb-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="853eb-160">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="853eb-160">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="853eb-161">URI che contiene l'indirizzo del proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="853eb-161">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="853eb-162">Se `useSystemWebProxy` è impostato su `true`, questa impostazione deve essere `null`.</span><span class="sxs-lookup"><span data-stu-id="853eb-162">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="853eb-163">Il valore predefinito è `null`.</span><span class="sxs-lookup"><span data-stu-id="853eb-163">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="853eb-164">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="853eb-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="853eb-165">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="853eb-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="853eb-166">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="853eb-166">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="853eb-167">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="853eb-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="853eb-168">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="853eb-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="853eb-169">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="853eb-169">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="853eb-170">Imposta la codifica del set di caratteri da usare per l'emissione dei messaggi nell'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="853eb-171">Di seguito vengono elencati i valori validi:</span><span class="sxs-lookup"><span data-stu-id="853eb-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="853eb-172">BigEndianUnicode Codifica BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="853eb-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="853eb-173">Unicode codifica a 16 bit.</span><span class="sxs-lookup"><span data-stu-id="853eb-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="853eb-174">UTF8 codifica a 8 bit</span><span class="sxs-lookup"><span data-stu-id="853eb-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="853eb-175">L'impostazione predefinita è UTF8.</span><span class="sxs-lookup"><span data-stu-id="853eb-175">The default is UTF8.</span></span> <span data-ttu-id="853eb-176">L'attributo è di tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="853eb-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="853eb-177">Valore <xref:System.ServiceModel.TransferMode> valido che specifica se i messaggi vengono memorizzati nel buffer o inviati nel flusso in una richiesta o una risposta.</span><span class="sxs-lookup"><span data-stu-id="853eb-177">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="853eb-178">Valore booleano che specifica se il proxy HTTP configurato automaticamente del sistema deve essere usato, se disponibile.</span><span class="sxs-lookup"><span data-stu-id="853eb-178">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="853eb-179">Il valore predefinito è `true`.</span><span class="sxs-lookup"><span data-stu-id="853eb-179">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="853eb-180">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="853eb-180">Child Elements</span></span>  
  
|<span data-ttu-id="853eb-181">Elemento</span><span class="sxs-lookup"><span data-stu-id="853eb-181">Element</span></span>|<span data-ttu-id="853eb-182">Descrizione</span><span class="sxs-lookup"><span data-stu-id="853eb-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="853eb-183">\<security></span><span class="sxs-lookup"><span data-stu-id="853eb-183">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="853eb-184">Definisce le impostazioni di sicurezza per l'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="853eb-185">L'elemento è di tipo <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="853eb-185">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="853eb-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="853eb-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="853eb-187">Definisce i vincoli sulla complessità dei messaggi SOAP che possono essere elaborati dagli endpoint configurati con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-187">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="853eb-188">L'elemento è di tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="853eb-188">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="853eb-189">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="853eb-189">Parent Elements</span></span>  
  
|<span data-ttu-id="853eb-190">Elemento</span><span class="sxs-lookup"><span data-stu-id="853eb-190">Element</span></span>|<span data-ttu-id="853eb-191">Descrizione</span><span class="sxs-lookup"><span data-stu-id="853eb-191">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="853eb-192">\<bindings></span><span class="sxs-lookup"><span data-stu-id="853eb-192">\<bindings></span></span>](bindings.md)|<span data-ttu-id="853eb-193">Questo elemento contiene una raccolta di associazioni standard e personalizzate.</span><span class="sxs-lookup"><span data-stu-id="853eb-193">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="853eb-194">Note</span><span class="sxs-lookup"><span data-stu-id="853eb-194">Remarks</span></span>  
 <span data-ttu-id="853eb-195">NetHttpsBinding usa HTTPS come trasporto per l'invio di messaggi.</span><span class="sxs-lookup"><span data-stu-id="853eb-195">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="853eb-196">Nel caso di un contratto duplex, verrà usato Web Sockets.</span><span class="sxs-lookup"><span data-stu-id="853eb-196">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="853eb-197">Se si usa un contratto richiesta-risposta, NetHttpsBinding si comporta come BasicHttpsBinding con un codificatore binario.</span><span class="sxs-lookup"><span data-stu-id="853eb-197">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="853eb-198">Per impostazione predefinita, la sicurezza è disattivata, ma è possibile aggiungerla impostando l'attributo mode dell' `None` [ \<elemento figlio Security >](security-of-basichttpbinding.md) su un valore diverso da.</span><span class="sxs-lookup"><span data-stu-id="853eb-198">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="853eb-199">Per impostazione predefinita usa una codifica dei messaggi "Text" e una codifica del testo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="853eb-199">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="853eb-200">Esempio</span><span class="sxs-lookup"><span data-stu-id="853eb-200">Example</span></span>  
 <span data-ttu-id="853eb-201">Nell'esempio seguente è dimostrato l'uso di <xref:System.ServiceModel.NetHttpBinding> che fornisce la comunicazione HTTPS e la massima interoperabilità con servizi Web di prima e seconda generazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-201">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="853eb-202">L'associazione è specificata nei file di configurazione per il client e il servizio.</span><span class="sxs-lookup"><span data-stu-id="853eb-202">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="853eb-203">Il tipo di associazione specificato usando l'attributo `binding` dell'elemento `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="853eb-203">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="853eb-204">Se si desidera configurare l'associazione di base e modificare alcune delle relative impostazioni, è necessario definire una configurazione di associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-204">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="853eb-205">L'endpoint deve fare riferimento alla configurazione di associazione tramite il nome usando l'attributo `bindingConfiguration` dell'elemento `<endpoint>`, come è illustrato nel seguente codice di configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="853eb-205">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="853eb-206">Esempio</span><span class="sxs-lookup"><span data-stu-id="853eb-206">Example</span></span>  
 <span data-ttu-id="853eb-207">A partire da [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], non è necessario che le associazioni e i comportamenti dispongano di un nome.</span><span class="sxs-lookup"><span data-stu-id="853eb-207">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="853eb-208">La funzionalità dell'esempio precedente può essere eseguita rimuovendo il bindingConfiguration dall'indirizzo endpoint e il nome dall'associazione.</span><span class="sxs-lookup"><span data-stu-id="853eb-208">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="853eb-209">Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="853eb-209">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853eb-210">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="853eb-210">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="853eb-211">Associazioni</span><span class="sxs-lookup"><span data-stu-id="853eb-211">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="853eb-212">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="853eb-212">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="853eb-213">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="853eb-213">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="853eb-214">\<binding></span><span class="sxs-lookup"><span data-stu-id="853eb-214">\<binding></span></span>](../../../misc/binding.md)
