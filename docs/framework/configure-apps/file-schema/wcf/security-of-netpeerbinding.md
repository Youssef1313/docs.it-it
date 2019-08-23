---
title: <security> di <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936620"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="987ca-102">\<> di sicurezza \<di netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="987ca-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="987ca-103">Definisce le impostazioni di sicurezza del [ \<> NetPeerTcpBinding](netpeertcpbinding.md), incluso il tipo di autenticazione utilizzato e la sicurezza utilizzata per il trasporto del messaggio.</span><span class="sxs-lookup"><span data-stu-id="987ca-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="987ca-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="987ca-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="987ca-105">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="987ca-105">\<bindings></span></span>  
<span data-ttu-id="987ca-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="987ca-106">\<netPeerBinding></span></span>  
<span data-ttu-id="987ca-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="987ca-107">\<binding></span></span>  
<span data-ttu-id="987ca-108">\<security></span><span class="sxs-lookup"><span data-stu-id="987ca-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="987ca-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="987ca-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="987ca-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="987ca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="987ca-111">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="987ca-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="987ca-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="987ca-112">Attributes</span></span>  
  
|<span data-ttu-id="987ca-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="987ca-113">Attribute</span></span>|<span data-ttu-id="987ca-114">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="987ca-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="987ca-115">modalità</span><span class="sxs-lookup"><span data-stu-id="987ca-115">mode</span></span>|<span data-ttu-id="987ca-116">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="987ca-116">Optional.</span></span> <span data-ttu-id="987ca-117">Specifica il tipo di sicurezza usata da peer configurati con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="987ca-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="987ca-118">Il valore predefinito è `Message`.</span><span class="sxs-lookup"><span data-stu-id="987ca-118">The default value is `Message`.</span></span> <span data-ttu-id="987ca-119">L'attributo è di tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="987ca-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="987ca-120">Attributo mode</span><span class="sxs-lookup"><span data-stu-id="987ca-120">mode Attribute</span></span>  
  
|<span data-ttu-id="987ca-121">Value</span><span class="sxs-lookup"><span data-stu-id="987ca-121">Value</span></span>|<span data-ttu-id="987ca-122">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="987ca-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="987ca-123">Messaggio</span><span class="sxs-lookup"><span data-stu-id="987ca-123">Message</span></span>|<span data-ttu-id="987ca-124">La sicurezza SOAP fornisce autenticazione, integrità e riservatezza.</span><span class="sxs-lookup"><span data-stu-id="987ca-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="987ca-125">Nessuna</span><span class="sxs-lookup"><span data-stu-id="987ca-125">None</span></span>|<span data-ttu-id="987ca-126">La sicurezza è disabilitata.</span><span class="sxs-lookup"><span data-stu-id="987ca-126">Security is disabled.</span></span>|  
|<span data-ttu-id="987ca-127">Trasporto</span><span class="sxs-lookup"><span data-stu-id="987ca-127">Transport</span></span>|<span data-ttu-id="987ca-128">La sicurezza è fornita mediante HTTPS.</span><span class="sxs-lookup"><span data-stu-id="987ca-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="987ca-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="987ca-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="987ca-130">HTTPS fornisce autenticazione e riservatezza.</span><span class="sxs-lookup"><span data-stu-id="987ca-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="987ca-131">I messaggi SOAP forniscono tipi di credenziale dettagliati.</span><span class="sxs-lookup"><span data-stu-id="987ca-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="987ca-132">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="987ca-132">Child Elements</span></span>  
  
|<span data-ttu-id="987ca-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="987ca-133">Element</span></span>|<span data-ttu-id="987ca-134">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="987ca-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="987ca-135">\<transport></span><span class="sxs-lookup"><span data-stu-id="987ca-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="987ca-136">Definisce il tipo di trasporto per messaggi protetti inviati dai peer configurati con questa associazione.</span><span class="sxs-lookup"><span data-stu-id="987ca-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="987ca-137">L'elemento è di tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="987ca-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="987ca-138">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="987ca-138">Parent Elements</span></span>  
  
|<span data-ttu-id="987ca-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="987ca-139">Element</span></span>|<span data-ttu-id="987ca-140">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="987ca-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="987ca-141">\<binding></span><span class="sxs-lookup"><span data-stu-id="987ca-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="987ca-142">Definisce tutte le funzionalità di associazione del [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="987ca-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="987ca-143">Note</span><span class="sxs-lookup"><span data-stu-id="987ca-143">Remarks</span></span>  
 <span data-ttu-id="987ca-144">La sicurezza può essere specifica dei messaggi o del trasporto.</span><span class="sxs-lookup"><span data-stu-id="987ca-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987ca-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="987ca-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="987ca-146">Protezione di servizi e client</span><span class="sxs-lookup"><span data-stu-id="987ca-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="987ca-147">Selezione di un tipo di credenziale</span><span class="sxs-lookup"><span data-stu-id="987ca-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="987ca-148">Associazioni</span><span class="sxs-lookup"><span data-stu-id="987ca-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="987ca-149">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="987ca-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="987ca-150">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="987ca-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="987ca-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="987ca-151">\<binding></span></span>](../../../misc/binding.md)
