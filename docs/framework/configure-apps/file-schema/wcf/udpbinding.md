---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429839"
---
# <a name="udpbinding"></a><span data-ttu-id="dc9ba-101">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="dc9ba-101">\<udpBinding></span></span>
<span data-ttu-id="dc9ba-102">Elemento di configurazione usato per configurare <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="dc9ba-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc9ba-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dc9ba-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dc9ba-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dc9ba-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="dc9ba-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dc9ba-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding>**</span><span class="sxs-lookup"><span data-stu-id="dc9ba-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9ba-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dc9ba-107">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc9ba-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="dc9ba-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dc9ba-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc9ba-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="dc9ba-110">Attributes</span></span>  
  
|<span data-ttu-id="dc9ba-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="dc9ba-111">Attribute</span></span>|<span data-ttu-id="dc9ba-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc9ba-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="dc9ba-113">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dc9ba-114">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dc9ba-115">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="dc9ba-116">Valore integer che specifica la lunghezza della cronologia dei messaggi duplicati.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="dc9ba-117">Valore intero che specifica la quantità massima di memoria allocata al gestore dei buffer dei messaggi che riceve i messaggi dal canale.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="dc9ba-118">Il valore predefinito è 524.288 (0x80000) byte.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="dc9ba-119">Un valore intero che specifica la dimensione massima, in byte, di un buffer che memorizza i messaggi mentre vengono elaborati per un endpoint configurato con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="dc9ba-120">L'impostazione predefinita è 65.536 byte.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="dc9ba-121">Valore integer che specifica il numero massimo di messaggi ricevuti ma non ancora rimossi dalla coda di input per una singola istanza di canale.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="dc9ba-122">Numero intero positivo che definisce la dimensione massima del messaggio, incluse le intestazioni, che può essere ricevuto in canale configurato con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="dc9ba-123">Il mittente riceve un errore SOAP se il messaggio è troppo grande per il destinatario.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="dc9ba-124">Il destinatario elimina il messaggio e crea una voce dell'evento nel registro di traccia.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="dc9ba-125">L'impostazione predefinita è 65.536 byte.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="dc9ba-126">Valore integer che specifica il numero massimo di messaggi da ritrasmettere.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="dc9ba-127">Valore integer che specifica l'ID multicast dell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="dc9ba-128">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dc9ba-129">Questo valore deve essere univoco perché viene usato per identificare l'associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dc9ba-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dc9ba-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ba-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="dc9ba-132">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dc9ba-133">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dc9ba-134">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-134">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="dc9ba-135">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dc9ba-136">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dc9ba-137">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-137">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="dc9ba-138">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dc9ba-139">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dc9ba-140">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-140">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="dc9ba-141">Imposta la codifica del set di caratteri da usare per l'emissione dei messaggi nell'associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-141">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="dc9ba-142">Di seguito vengono elencati i valori validi:</span><span class="sxs-lookup"><span data-stu-id="dc9ba-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc9ba-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="dc9ba-144">-   Unicode: 16-bit encoding.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-144">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="dc9ba-145">-   UTF8: 8-bit encoding</span><span class="sxs-lookup"><span data-stu-id="dc9ba-145">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="dc9ba-146">L'impostazione predefinita è UTF8.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-146">The default is UTF8.</span></span> <span data-ttu-id="dc9ba-147">L'attributo è di tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-147">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="dc9ba-148">Valore timespan che specifica durata (TTL, Time To Live) dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-148">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc9ba-149">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="dc9ba-149">Child Elements</span></span>  
  
|<span data-ttu-id="dc9ba-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc9ba-150">Element</span></span>|<span data-ttu-id="dc9ba-151">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc9ba-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc9ba-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dc9ba-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="dc9ba-153">Definisce i vincoli sulla complessità dei messaggi SOAP che possono essere elaborati dagli endpoint configurati con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dc9ba-154">L'elemento è di tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc9ba-155">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="dc9ba-155">Parent Elements</span></span>  
  
|<span data-ttu-id="dc9ba-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc9ba-156">Element</span></span>|<span data-ttu-id="dc9ba-157">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc9ba-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc9ba-158">\<bindings></span><span class="sxs-lookup"><span data-stu-id="dc9ba-158">\<bindings></span></span>](bindings.md)|<span data-ttu-id="dc9ba-159">Questo elemento contiene una raccolta di associazioni standard e personalizzate.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc9ba-160">Note</span><span class="sxs-lookup"><span data-stu-id="dc9ba-160">Remarks</span></span>  
 <span data-ttu-id="dc9ba-161">UdpBinding consente ai servizi WCF di comunicare tramite trasporto UDP.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="dc9ba-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc9ba-163">Esempio</span><span class="sxs-lookup"><span data-stu-id="dc9ba-163">Example</span></span>  
 <span data-ttu-id="dc9ba-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span><span class="sxs-lookup"><span data-stu-id="dc9ba-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="dc9ba-165">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dc9ba-165">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="dc9ba-166">Associazioni</span><span class="sxs-lookup"><span data-stu-id="dc9ba-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dc9ba-167">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="dc9ba-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dc9ba-168">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="dc9ba-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dc9ba-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="dc9ba-169">\<binding></span></span>](bindings.md)
