---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919563"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="c4172-101">\<> channelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c4172-101">\<channelPoolSettings></span></span>
<span data-ttu-id="c4172-102">Specifica le impostazioni del pool di canali per un'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="c4172-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="c4172-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c4172-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c4172-104">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="c4172-104">\<bindings></span></span>  
<span data-ttu-id="c4172-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c4172-105">\<customBinding></span></span>  
<span data-ttu-id="c4172-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="c4172-106">\<binding></span></span>  
<span data-ttu-id="c4172-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="c4172-107">\<oneWay></span></span>  
<span data-ttu-id="c4172-108">\<> channelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c4172-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4172-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c4172-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4172-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c4172-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4172-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="c4172-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4172-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="c4172-112">Attributes</span></span>  
  
|<span data-ttu-id="c4172-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="c4172-113">Attribute</span></span>|<span data-ttu-id="c4172-114">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="c4172-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="c4172-115">Oggetto <xref:System.TimeSpan> positivo che specifica il periodo massimo di inattività dei canali nel pool prima della disconnessione.</span><span class="sxs-lookup"><span data-stu-id="c4172-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="c4172-116">L'impostazione predefinita è 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="c4172-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="c4172-117">Oggetto <xref:System.TimeSpan> che specifica l'intervallo di tempo trascorso il quale un canale, dopo essere stato restituito al pool, viene chiuso.</span><span class="sxs-lookup"><span data-stu-id="c4172-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="c4172-118">L'impostazione predefinita è 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c4172-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="c4172-119">Numero intero positivo che specifica il numero massimo di canali che possono essere memorizzati nel pool per ogni endpoint remoto.</span><span class="sxs-lookup"><span data-stu-id="c4172-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="c4172-120">Il valore predefinito è 10.</span><span class="sxs-lookup"><span data-stu-id="c4172-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4172-121">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c4172-121">Child Elements</span></span>  
 <span data-ttu-id="c4172-122">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="c4172-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4172-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c4172-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c4172-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4172-124">Element</span></span>|<span data-ttu-id="c4172-125">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="c4172-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4172-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="c4172-126">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="c4172-127">Attiva il routing dei pacchetti per un'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="c4172-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4172-128">Note</span><span class="sxs-lookup"><span data-stu-id="c4172-128">Remarks</span></span>  
 <span data-ttu-id="c4172-129">Le quote sono usate come meccanismo di criterio per impedire un consumo eccessivo di risorse.</span><span class="sxs-lookup"><span data-stu-id="c4172-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="c4172-130">Impediscono attacchi di tipo Denial of Service (DoS), dannosi o non intenzionali.</span><span class="sxs-lookup"><span data-stu-id="c4172-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="c4172-131">Usare questo elemento durante l'impostazione delle quote dei canali in un canale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="c4172-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="c4172-132">`ChannelPoolSettings` specifica tre quote:</span><span class="sxs-lookup"><span data-stu-id="c4172-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="c4172-133">La quota `idleTimeout` viene usata per ridurre il rischio di attacchi di tipo Denial of Service (DoS) nel server basati sul blocco di risorse per periodi di tempo prolungati.</span><span class="sxs-lookup"><span data-stu-id="c4172-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="c4172-134">Nel client, l'impostazione del valore corretto può aumentare l'affidabilità della connessione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="c4172-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="c4172-135">Il valore predefinito è basato su un'allocazione conservativamente modesta di risorse.</span><span class="sxs-lookup"><span data-stu-id="c4172-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="c4172-136">È adatto per un ambiente di sviluppo e in scenari con installazioni di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="c4172-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="c4172-137">Gli amministratori del servizio devono rivedere il valore se un'installazione sta esaurendo le risorse o se le connessioni sono limitate nonostante la disponibilità di risorse aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="c4172-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="c4172-138">La quota `leaseTimeout` viene usata per l'integrazione con i servizi di bilanciamento del carico e per migliorare l'affidabilità.</span><span class="sxs-lookup"><span data-stu-id="c4172-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="c4172-139">Il valore predefinito è basato su un'allocazione conservativa di risorse.</span><span class="sxs-lookup"><span data-stu-id="c4172-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="c4172-140">È adatto per un ambiente di sviluppo e in scenari con installazioni di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="c4172-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="c4172-141">Gli amministratori del servizio devono rivedere il valore se un'installazione sta esaurendo le risorse o se le connessioni sono limitate nonostante la disponibilità di risorse aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="c4172-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="c4172-142">La quota `maxOutboundChannelsPerEndpoint` imposta limiti della cache sia nel server che nel client ed è usata per migliorare l'affidabilità.</span><span class="sxs-lookup"><span data-stu-id="c4172-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="c4172-143">Il valore predefinito è basato su un'allocazione conservativamente modesta di risorse idonee per ambienti di sviluppo e scenari con installazioni di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="c4172-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="c4172-144">Gli amministratori del servizio devono rivedere il valore se un'installazione sta esaurendo le risorse o se le connessioni sono limitate nonostante la disponibilità di risorse aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="c4172-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4172-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c4172-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c4172-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="c4172-146">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="c4172-147">Associazioni</span><span class="sxs-lookup"><span data-stu-id="c4172-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c4172-148">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="c4172-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c4172-149">Associazioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="c4172-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c4172-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c4172-150">\<customBinding></span></span>](custombinding.md)
