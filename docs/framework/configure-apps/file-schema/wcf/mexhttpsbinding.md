---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738930"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="f95b7-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="f95b7-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="f95b7-102">Specifica le impostazioni per un'associazione usata per lo scambio di messaggi WS-MetadataExchange (WS-MEX) tramite HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f95b7-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="f95b7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f95b7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f95b7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f95b7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f95b7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="f95b7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="f95b7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding** ></span><span class="sxs-lookup"><span data-stu-id="f95b7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f95b7-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f95b7-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f95b7-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f95b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f95b7-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="f95b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f95b7-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="f95b7-110">Attributes</span></span>  
  
|<span data-ttu-id="f95b7-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="f95b7-111">Attribute</span></span>|<span data-ttu-id="f95b7-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f95b7-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f95b7-113">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="f95b7-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f95b7-114">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f95b7-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f95b7-115">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f95b7-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f95b7-116">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="f95b7-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f95b7-117">Questo valore deve essere univoco perché viene usato per identificare l'associazione.</span><span class="sxs-lookup"><span data-stu-id="f95b7-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f95b7-118">Ciascuna associazione è provvista di un attributo `name` e `namespace` che insieme la identificano in modo univoco nei metadati del servizio.</span><span class="sxs-lookup"><span data-stu-id="f95b7-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f95b7-119">In aggiunta, il nome è univoco fra associazioni dello stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="f95b7-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f95b7-120">A partire da [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], non è necessario che le associazioni e i comportamenti dispongano di un nome.</span><span class="sxs-lookup"><span data-stu-id="f95b7-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f95b7-121">Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f95b7-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f95b7-122">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="f95b7-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f95b7-123">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f95b7-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f95b7-124">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f95b7-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f95b7-125">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="f95b7-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f95b7-126">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f95b7-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f95b7-127">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f95b7-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f95b7-128">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="f95b7-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f95b7-129">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f95b7-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f95b7-130">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f95b7-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f95b7-131">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f95b7-131">Child Elements</span></span>  
 <span data-ttu-id="f95b7-132">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f95b7-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f95b7-133">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f95b7-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f95b7-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="f95b7-134">Element</span></span>|<span data-ttu-id="f95b7-135">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f95b7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f95b7-136">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="f95b7-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f95b7-137">Questo elemento contiene una raccolta di associazioni standard e personalizzate.</span><span class="sxs-lookup"><span data-stu-id="f95b7-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f95b7-138">Note</span><span class="sxs-lookup"><span data-stu-id="f95b7-138">Remarks</span></span>  
 <span data-ttu-id="f95b7-139">Questa associazione fondamentalmente un'associazione `WSHttpBinding` che supporta la sicurezza a livello di trasporto mediante certificati.</span><span class="sxs-lookup"><span data-stu-id="f95b7-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="f95b7-140">Per altre informazioni sulla configurazione e sull'uso di un endpoint di metadati di questo tipo, vedere [procedura: configurare un'associazione di WS-Metadata Exchange personalizzati](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [procedura: recuperare metadati su un'associazione non MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e l' [endpoint di metadati sicuro personalizzato](../../../wcf/samples/custom-secure-metadata-endpoint.md) di esempio .</span><span class="sxs-lookup"><span data-stu-id="f95b7-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95b7-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f95b7-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="f95b7-142">Procedura: Pubblicare metadati per un servizio usando un file di configurazione</span><span class="sxs-lookup"><span data-stu-id="f95b7-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f95b7-143">Pubblicazione e recupero di metadati su un'associazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="f95b7-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f95b7-144">Procedura: Configurare un'associazione WS-Metadata Exchange personalizzata</span><span class="sxs-lookup"><span data-stu-id="f95b7-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="f95b7-145">Procedura: Recuperare metadati attraverso un'associazione non MEX</span><span class="sxs-lookup"><span data-stu-id="f95b7-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="f95b7-146">Endpoint di metadati protetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="f95b7-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="f95b7-147">Metadati</span><span class="sxs-lookup"><span data-stu-id="f95b7-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="f95b7-148">Associazioni</span><span class="sxs-lookup"><span data-stu-id="f95b7-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f95b7-149">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="f95b7-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f95b7-150">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="f95b7-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f95b7-151">\<binding ></span><span class="sxs-lookup"><span data-stu-id="f95b7-151">\<binding></span></span>](bindings.md)
