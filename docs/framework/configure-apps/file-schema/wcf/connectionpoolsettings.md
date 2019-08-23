---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925966"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="99a8b-101">\<> connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="99a8b-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="99a8b-102">Specifica impostazioni aggiuntive del pool di connessioni per un'associazione con named pipe.</span><span class="sxs-lookup"><span data-stu-id="99a8b-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="99a8b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99a8b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="99a8b-104">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="99a8b-104">\<bindings></span></span>  
<span data-ttu-id="99a8b-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="99a8b-105">\<customBinding></span></span>  
<span data-ttu-id="99a8b-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="99a8b-106">\<binding></span></span>  
<span data-ttu-id="99a8b-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="99a8b-107">\<namePipeTransport></span></span>  
<span data-ttu-id="99a8b-108">\<> connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="99a8b-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a8b-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="99a8b-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99a8b-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="99a8b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99a8b-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="99a8b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99a8b-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="99a8b-112">Attributes</span></span>  
  
|<span data-ttu-id="99a8b-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="99a8b-113">Attribute</span></span>|<span data-ttu-id="99a8b-114">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="99a8b-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="99a8b-115">Stringa che definisce il nome del pool di connessioni usato per canali in uscita.</span><span class="sxs-lookup"><span data-stu-id="99a8b-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="99a8b-116">In modalità di invio nel flusso, le connessioni non sono condivise, pertanto il pool di connessioni è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="99a8b-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="99a8b-117">Il valore predefinito è una stringa "default".</span><span class="sxs-lookup"><span data-stu-id="99a8b-117">The default is a "default" string.</span></span> <span data-ttu-id="99a8b-118">È possibile modificare questo valore per isolare le connessioni per un particolare client in gruppi separati.</span><span class="sxs-lookup"><span data-stu-id="99a8b-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="99a8b-119">Elemento <xref:System.TimeSpan> positivo che specifica il periodo massimo di inattività della connessione prima che venga interrotta.</span><span class="sxs-lookup"><span data-stu-id="99a8b-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="99a8b-120">L'impostazione predefinita è 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="99a8b-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="99a8b-121">Numero intero positivo che specifica il numero massimo di connessioni a un endpoint remoto iniziate dal servizio.</span><span class="sxs-lookup"><span data-stu-id="99a8b-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="99a8b-122">Le connessioni in eccesso vengono messe in coda finché il numero di connessioni non risulta inferiore al limite consentito.</span><span class="sxs-lookup"><span data-stu-id="99a8b-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="99a8b-123">`idleTimeout` limita il periodo di tempo entro il quale le connessioni rimangono in coda prima che venga generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="99a8b-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="99a8b-124">Il valore predefinito è 10.</span><span class="sxs-lookup"><span data-stu-id="99a8b-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="99a8b-125">Questo attributo limita il numero di connessioni attive simultanee dal client a un particolare endpoint del servizio.</span><span class="sxs-lookup"><span data-stu-id="99a8b-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="99a8b-126">Se questo valore viene superato a causa di un numero maggiore di connessioni client attive, può risultare che il servizio non risponda al client.</span><span class="sxs-lookup"><span data-stu-id="99a8b-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="99a8b-127">In questo caso, il valore deve essere regolato in modo da superare il numero massimo di connessioni client simultanee previste a un endpoint specifico.</span><span class="sxs-lookup"><span data-stu-id="99a8b-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99a8b-128">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="99a8b-128">Child Elements</span></span>  
 <span data-ttu-id="99a8b-129">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="99a8b-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99a8b-130">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="99a8b-130">Parent Elements</span></span>  
  
|<span data-ttu-id="99a8b-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="99a8b-131">Element</span></span>|<span data-ttu-id="99a8b-132">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="99a8b-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99a8b-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="99a8b-133">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="99a8b-134">Definisce un trasporto che fa in modo che un canale trasferisca messaggi usando named pipe.</span><span class="sxs-lookup"><span data-stu-id="99a8b-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99a8b-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="99a8b-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="99a8b-136">Trasporti</span><span class="sxs-lookup"><span data-stu-id="99a8b-136">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="99a8b-137">Scelta di un trasporto</span><span class="sxs-lookup"><span data-stu-id="99a8b-137">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="99a8b-138">Associazioni</span><span class="sxs-lookup"><span data-stu-id="99a8b-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="99a8b-139">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="99a8b-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="99a8b-140">Associazioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="99a8b-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="99a8b-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="99a8b-141">\<customBinding></span></span>](custombinding.md)
