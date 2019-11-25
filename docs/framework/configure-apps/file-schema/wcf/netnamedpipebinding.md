---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139476"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="6b6fa-101">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="6b6fa-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="6b6fa-102">Definisce un'associazione che è protetta, affidabile, ottimizzata per le comunicazioni tra processi nel computer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="6b6fa-103">Per impostazione predefinita, genera uno stack di comunicazione in fase di esecuzione con WS-ReliableMessaging per affidabilità, sicurezza del trasporto per la sicurezza del trasferimento, named pipe per il recapito dei messaggi e codifica binaria dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="6b6fa-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b6fa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b6fa-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b6fa-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b6fa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="6b6fa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="6b6fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**NetNamedPipeBinding** ></span><span class="sxs-lookup"><span data-stu-id="6b6fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6fa-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6b6fa-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b6fa-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6b6fa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6b6fa-110">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b6fa-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="6b6fa-111">Attributes</span></span>  
  
|<span data-ttu-id="6b6fa-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="6b6fa-112">Attribute</span></span>|<span data-ttu-id="6b6fa-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6b6fa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b6fa-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="6b6fa-114">closeTimeout</span></span>|<span data-ttu-id="6b6fa-115">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6b6fa-116">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b6fa-117">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b6fa-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="6b6fa-118">hostNameComparisonMode</span></span>|<span data-ttu-id="6b6fa-119">Specifica la modalità di confronto del nome host HTTP usata per analizzare gli URI.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6b6fa-120">L'attributo è di tipo <xref:System.ServiceModel.HostNameComparisonMode>, che indica se il nome host viene usato per raggiungere il servizio in caso di corrispondenza nell'URI.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6b6fa-121">Il valore predefinito è <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, che ignora il nome host nella corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="6b6fa-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6b6fa-122">maxBufferPoolSize</span></span>|<span data-ttu-id="6b6fa-123">Numero intero che specifica la dimensione del pool di buffer massima per questa associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6b6fa-124">Il valore predefinito è 524.288 byte (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="6b6fa-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="6b6fa-125">Molte parti di Windows Communication Foundation (WCF) usano buffer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6b6fa-126">La creazione e l'eliminazione definitiva dei buffer a ogni uso sono operazioni onerose, analogamente a quelle di Garbage Collection dei buffer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6b6fa-127">Quando si usa un pool di buffer è possibile prelevare un buffer dal pool, usarlo e, al termine delle operazioni, riporlo nel pool.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6b6fa-128">In questo modo è possibile evitare il sovraccarico dovuto alla creazione e all'eliminazione definitiva dei buffer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6b6fa-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="6b6fa-129">maxBufferSize</span></span>|<span data-ttu-id="6b6fa-130">Numero intero positivo che specifica la dimensione massima, in byte, del buffer usato per archiviare messaggi in memoria.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="6b6fa-131">Se il buffer è pieno, i dati in eccesso rimangono nel socket sottostante fino a che non è di nuovo disponibile spazio nel buffer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="6b6fa-132">Questo valore non può essere inferiore a `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="6b6fa-133">Il valore predefinito è 65536.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-133">The default is 65536.</span></span> <span data-ttu-id="6b6fa-134">Per ulteriori informazioni, vedere <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="6b6fa-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="6b6fa-135">maxConnections</span></span>|<span data-ttu-id="6b6fa-136">Numero intero che specifica il numero massimo di connessioni in uscita e in ingresso che il servizio creerà e accetterà.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="6b6fa-137">Le connessioni in ingresso e in uscita vengono conteggiate in base a un limite distinto specificato da questo attributo.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="6b6fa-138">Le connessioni in ingresso eccedenti il limite vengono messe in coda finché non è disponibile uno spazio inferiore al limite.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6b6fa-139">Le connessioni in uscita eccedenti il limite vengono messe in coda finché non è disponibile uno spazio inferiore al limite.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6b6fa-140">Il valore predefinito è 10.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-140">The default is 10.</span></span>|  
|<span data-ttu-id="6b6fa-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6b6fa-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="6b6fa-142">Integer positivo che specifica la dimensione massima del messaggio, incluse le intestazioni, che è possibile ricevere su un canale configurato con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6b6fa-143">Il mittente di un messaggio che supera questo limite riceverà un errore SOAP.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="6b6fa-144">Il destinatario elimina il messaggio e crea una voce dell'evento nel registro di traccia.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6b6fa-145">Il valore predefinito è 65536.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-145">The default is 65536.</span></span>|  
|<span data-ttu-id="6b6fa-146">name</span><span class="sxs-lookup"><span data-stu-id="6b6fa-146">name</span></span>|<span data-ttu-id="6b6fa-147">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6b6fa-148">Questo valore deve essere univoco perché viene usato per identificare l'associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6b6fa-149">A partire da .NET Framework 4, le associazioni e i comportamenti non devono avere un nome.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6b6fa-150">Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6b6fa-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="6b6fa-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="6b6fa-151">openTimeout</span></span>|<span data-ttu-id="6b6fa-152">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6b6fa-153">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b6fa-154">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b6fa-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6b6fa-155">receiveTimeout</span></span>|<span data-ttu-id="6b6fa-156">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6b6fa-157">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b6fa-158">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="6b6fa-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="6b6fa-159">sendTimeout</span></span>|<span data-ttu-id="6b6fa-160">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6b6fa-161">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b6fa-162">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b6fa-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="6b6fa-163">transactionFlow</span></span>|<span data-ttu-id="6b6fa-164">Valore booleano che specifica se l'associazione supporta la propagazione di WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6b6fa-165">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-165">The default is `false`.</span></span>|  
|<span data-ttu-id="6b6fa-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="6b6fa-166">transactionProtocol</span></span>|<span data-ttu-id="6b6fa-167">Specifica il protocollo di transazione da usare con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="6b6fa-168">I valori validi sono:</span><span class="sxs-lookup"><span data-stu-id="6b6fa-168">Valid values are</span></span><br /><br /> <span data-ttu-id="6b6fa-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="6b6fa-169">-   OleTransactions</span></span><br /><span data-ttu-id="6b6fa-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="6b6fa-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="6b6fa-171">L'impostazione predefinita è OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-171">The default is OleTransactions.</span></span> <span data-ttu-id="6b6fa-172">L'attributo è di tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="6b6fa-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="6b6fa-173">transferMode</span></span>|<span data-ttu-id="6b6fa-174">Valore <xref:System.ServiceModel.TransferMode> che specifica se i messaggi vengono memorizzati nel buffer o inviati nel flusso o sono una richiesta o una risposta.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b6fa-175">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6b6fa-175">Child Elements</span></span>  
  
|<span data-ttu-id="6b6fa-176">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b6fa-176">Element</span></span>|<span data-ttu-id="6b6fa-177">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6b6fa-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b6fa-178">> di sicurezza \<</span><span class="sxs-lookup"><span data-stu-id="6b6fa-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="6b6fa-179">Definisce le impostazioni di sicurezza per l'associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="6b6fa-180">L'elemento è di tipo <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="6b6fa-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b6fa-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6b6fa-182">Definisce i vincoli sulla complessità dei messaggi SOAP che possono essere elaborati dagli endpoint configurati con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6b6fa-183">L'elemento è di tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b6fa-184">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6b6fa-184">Parent Elements</span></span>  
  
|<span data-ttu-id="6b6fa-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b6fa-185">Element</span></span>|<span data-ttu-id="6b6fa-186">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6b6fa-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b6fa-187">associazioni di \<</span><span class="sxs-lookup"><span data-stu-id="6b6fa-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="6b6fa-188">Questo elemento contiene una raccolta di associazioni standard e personalizzate.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b6fa-189">Note</span><span class="sxs-lookup"><span data-stu-id="6b6fa-189">Remarks</span></span>  
 <span data-ttu-id="6b6fa-190">L'associazione `NetNamedPipeBinding` genera per impostazione predefinita uno stack di comunicazione di runtime che usa la sicurezza del trasporto, le named pipe per il recapito dei messaggi e una codifica dei messaggi binaria.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="6b6fa-191">Questa associazione rappresenta una scelta fornita dal sistema Windows Communication Foundation (WCF) appropriata per la comunicazione su computer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="6b6fa-192">Supporta inoltre le transazioni.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="6b6fa-193">La configurazione predefinita per `NetNamedPipeBinding` è simile alla configurazione fornita da `NetTcpBinding`, ma è più semplice poiché l'implementazione WCF è destinata solo all'utilizzo su computer e le funzionalità esposte sono di conseguenza minori.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="6b6fa-194">La differenza più evidente è che per l'impostazione di `securityMode` sono disponibili solo le opzioni `None` e `Transport`.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="6b6fa-195">Il supporto della sicurezza SOAP non è incluso fra le opzioni.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="6b6fa-196">Il comportamento di sicurezza può essere configurato usando l'attributo `securityMode` facoltativo.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b6fa-197">Esempio</span><span class="sxs-lookup"><span data-stu-id="6b6fa-197">Example</span></span>  
 <span data-ttu-id="6b6fa-198">Nell'esempio seguente è dimostrata l'associazione netNamedPipeBinding, che fornisce comunicazione tra processi sullo stesso computer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="6b6fa-199">Le named pipe non funzionano tra computer.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="6b6fa-200">L'associazione è specificata nei file di configurazione per il client e il servizio.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="6b6fa-201">Il tipo di associazione è specificato nell'attributo `binding` dell'elemento `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="6b6fa-202">Se si desidera configurare l'associazione netNamedPipeBinding e modificare alcune delle relative impostazioni, è necessario definire una configurazione di associazione.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="6b6fa-203">L'endpoint deve fare riferimento alla configurazione di associazione tramite il nome con un attributo `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="6b6fa-204">In questo esempio, la configurazione di associazione è denominata Binding1.</span><span class="sxs-lookup"><span data-stu-id="6b6fa-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b6fa-205">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6b6fa-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="6b6fa-206">Binding \<</span><span class="sxs-lookup"><span data-stu-id="6b6fa-206">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="6b6fa-207">Associazioni</span><span class="sxs-lookup"><span data-stu-id="6b6fa-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6b6fa-208">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="6b6fa-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6b6fa-209">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="6b6fa-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
