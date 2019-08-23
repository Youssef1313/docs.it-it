---
title: <transport> di <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934677"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="576a2-102">\<> di trasporto \<di NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="576a2-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="576a2-103">Definisce le impostazioni di sicurezza del trasporto per una named pipe.</span><span class="sxs-lookup"><span data-stu-id="576a2-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="576a2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="576a2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="576a2-105">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="576a2-105">\<bindings></span></span>  
<span data-ttu-id="576a2-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="576a2-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="576a2-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="576a2-107">\<binding></span></span>  
<span data-ttu-id="576a2-108">\<security></span><span class="sxs-lookup"><span data-stu-id="576a2-108">\<security></span></span>  
<span data-ttu-id="576a2-109">\<> di trasporto</span><span class="sxs-lookup"><span data-stu-id="576a2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576a2-110">Sintassi</span><span class="sxs-lookup"><span data-stu-id="576a2-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="576a2-111">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="576a2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="576a2-112">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="576a2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="576a2-113">Attributi</span><span class="sxs-lookup"><span data-stu-id="576a2-113">Attributes</span></span>  
  
|<span data-ttu-id="576a2-114">Attributo</span><span class="sxs-lookup"><span data-stu-id="576a2-114">Attribute</span></span>|<span data-ttu-id="576a2-115">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="576a2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="576a2-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="576a2-116">protectionLevel</span></span>|<span data-ttu-id="576a2-117">Definisce il livello di protezione della named pipe.</span><span class="sxs-lookup"><span data-stu-id="576a2-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="576a2-118">La firma dei messaggi riduce il rischio di manomissione da parte di terzi durante il trasferimento.</span><span class="sxs-lookup"><span data-stu-id="576a2-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="576a2-119">La crittografia fornisce riservatezza a livello di dati durante il trasporto.</span><span class="sxs-lookup"><span data-stu-id="576a2-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="576a2-120">Di seguito vengono elencati i valori validi:</span><span class="sxs-lookup"><span data-stu-id="576a2-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="576a2-121">Nessuno Nessuna protezione.</span><span class="sxs-lookup"><span data-stu-id="576a2-121">-   None: No protection.</span></span><br /><span data-ttu-id="576a2-122">Sign I messaggi vengono firmati.</span><span class="sxs-lookup"><span data-stu-id="576a2-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="576a2-123">EncryptAndSign I messaggi vengono crittografati e firmati.</span><span class="sxs-lookup"><span data-stu-id="576a2-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="576a2-124">Il valore predefinito è EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="576a2-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="576a2-125">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="576a2-125">Child Elements</span></span>  
 <span data-ttu-id="576a2-126">Nessuna</span><span class="sxs-lookup"><span data-stu-id="576a2-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="576a2-127">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="576a2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="576a2-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="576a2-128">Element</span></span>|<span data-ttu-id="576a2-129">Descrizione</span><span class="sxs-lookup"><span data-stu-id="576a2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="576a2-130">\<security></span><span class="sxs-lookup"><span data-stu-id="576a2-130">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="576a2-131">Definisce le impostazioni di sicurezza per un'associazione.</span><span class="sxs-lookup"><span data-stu-id="576a2-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="576a2-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="576a2-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="576a2-133">Protezione di servizi e client</span><span class="sxs-lookup"><span data-stu-id="576a2-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="576a2-134">Associazioni</span><span class="sxs-lookup"><span data-stu-id="576a2-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="576a2-135">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="576a2-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="576a2-136">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="576a2-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="576a2-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="576a2-137">\<binding></span></span>](../../../misc/binding.md)
