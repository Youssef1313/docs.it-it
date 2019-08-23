---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926075"
---
# <a name="compositeduplex"></a><span data-ttu-id="24df7-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="24df7-101">\<compositeDuplex></span></span>
<span data-ttu-id="24df7-102">Definisce l'elemento di associazione usato quando il client deve esporre un endpoint affinché il servizio restituisca messaggi al client.</span><span class="sxs-lookup"><span data-stu-id="24df7-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="24df7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="24df7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="24df7-104">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="24df7-104">\<bindings></span></span>  
<span data-ttu-id="24df7-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="24df7-105">\<customBinding></span></span>  
<span data-ttu-id="24df7-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="24df7-106">\<binding></span></span>  
<span data-ttu-id="24df7-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="24df7-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24df7-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24df7-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24df7-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="24df7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24df7-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="24df7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24df7-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="24df7-111">Attributes</span></span>  
  
|<span data-ttu-id="24df7-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="24df7-112">Attribute</span></span>|<span data-ttu-id="24df7-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="24df7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24df7-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="24df7-114">clientBaseAddress</span></span>|<span data-ttu-id="24df7-115">URI che imposta l'indirizzo del canale di supporto in modalità duplex.</span><span class="sxs-lookup"><span data-stu-id="24df7-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="24df7-116">Il servizio usa questo indirizzo per creare un contatto e stabilire una connessione con il client.</span><span class="sxs-lookup"><span data-stu-id="24df7-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="24df7-117">Se questo attributo non è impostato, viene generato un indirizzo`full qualified name+default port\TemporaryIndigoAddress\guid`predefinito "".</span><span class="sxs-lookup"><span data-stu-id="24df7-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="24df7-118">Il valore predefinito è `null`.</span><span class="sxs-lookup"><span data-stu-id="24df7-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24df7-119">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="24df7-119">Child Elements</span></span>  
 <span data-ttu-id="24df7-120">Nessuna</span><span class="sxs-lookup"><span data-stu-id="24df7-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24df7-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="24df7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24df7-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="24df7-122">Element</span></span>|<span data-ttu-id="24df7-123">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="24df7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24df7-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="24df7-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="24df7-125">Definisce tutte le funzionalità di associazione dell'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="24df7-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24df7-126">Note</span><span class="sxs-lookup"><span data-stu-id="24df7-126">Remarks</span></span>  
 <span data-ttu-id="24df7-127">Questo elemento di configurazione viene usato con trasporti che non consentono comunicazioni duplex a livello nativo, ad esempio, HTTP.</span><span class="sxs-lookup"><span data-stu-id="24df7-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="24df7-128">TCP, al contrario, consente comunicazioni duplex a livello nativo e non richiede l'uso di questo elemento di associazione affinché il servizio invii messaggi a un client.</span><span class="sxs-lookup"><span data-stu-id="24df7-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="24df7-129">Il client deve esporre un indirizzo affinché il servizio crei un contatto e stabilisca una connessione.</span><span class="sxs-lookup"><span data-stu-id="24df7-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="24df7-130">Questo indirizzo client è fornito dall'attributo `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="24df7-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="24df7-131">Si noti che Windows Communication Foundation (WCF) genera automaticamente un ClientBaseAddress se l'utente non ne imposta uno in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="24df7-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24df7-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="24df7-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="24df7-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24df7-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="24df7-134">Associazioni</span><span class="sxs-lookup"><span data-stu-id="24df7-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="24df7-135">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="24df7-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="24df7-136">Associazioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="24df7-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="24df7-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="24df7-137">\<customBinding></span></span>](custombinding.md)
