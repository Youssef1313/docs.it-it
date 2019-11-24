---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430298"
---
# <a name="mextcpbinding"></a><span data-ttu-id="d39c2-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d39c2-101">\<mexTcpBinding></span></span>
<span data-ttu-id="d39c2-102">Specifica le impostazioni per un'associazione usata per lo scambio di messaggi WS-MetadataExchange (WS-MEX) tramite TCP.</span><span class="sxs-lookup"><span data-stu-id="d39c2-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="d39c2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d39c2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d39c2-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d39c2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d39c2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d39c2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d39c2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding>**</span><span class="sxs-lookup"><span data-stu-id="d39c2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39c2-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d39c2-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d39c2-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="d39c2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d39c2-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="d39c2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d39c2-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="d39c2-110">Attributes</span></span>  
  
|<span data-ttu-id="d39c2-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="d39c2-111">Attribute</span></span>|<span data-ttu-id="d39c2-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d39c2-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d39c2-113">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="d39c2-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d39c2-114">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d39c2-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d39c2-115">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d39c2-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d39c2-116">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="d39c2-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d39c2-117">Questo valore deve essere univoco perché viene usato per identificare l'associazione.</span><span class="sxs-lookup"><span data-stu-id="d39c2-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d39c2-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="d39c2-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d39c2-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d39c2-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d39c2-120">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="d39c2-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d39c2-121">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d39c2-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d39c2-122">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d39c2-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d39c2-123">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="d39c2-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d39c2-124">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d39c2-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d39c2-125">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d39c2-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d39c2-126">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="d39c2-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d39c2-127">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d39c2-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d39c2-128">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d39c2-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d39c2-129">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="d39c2-129">Child Elements</span></span>  
 <span data-ttu-id="d39c2-130">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="d39c2-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d39c2-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="d39c2-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d39c2-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="d39c2-132">Element</span></span>|<span data-ttu-id="d39c2-133">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d39c2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d39c2-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d39c2-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d39c2-135">Questo elemento contiene una raccolta di associazioni standard e personalizzate.</span><span class="sxs-lookup"><span data-stu-id="d39c2-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d39c2-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d39c2-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="d39c2-137">Procedura: Pubblicare metadati per un servizio usando un file di configurazione</span><span class="sxs-lookup"><span data-stu-id="d39c2-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d39c2-138">Pubblicazione e recupero di metadati su un'associazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="d39c2-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d39c2-139">Metadati</span><span class="sxs-lookup"><span data-stu-id="d39c2-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="d39c2-140">Associazioni</span><span class="sxs-lookup"><span data-stu-id="d39c2-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d39c2-141">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="d39c2-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d39c2-142">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="d39c2-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d39c2-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="d39c2-143">\<binding></span></span>](bindings.md)
