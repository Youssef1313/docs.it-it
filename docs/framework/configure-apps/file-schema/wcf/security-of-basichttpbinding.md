---
title: <security> di <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936799"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="cc6e1-102">\<> di sicurezza \<di BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cc6e1-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="cc6e1-103">Definisce le funzionalità di sicurezza del [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cc6e1-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="cc6e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc6e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc6e1-105">\<Binding ></span><span class="sxs-lookup"><span data-stu-id="cc6e1-105">\<bindings></span></span>  
<span data-ttu-id="cc6e1-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cc6e1-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="cc6e1-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="cc6e1-107">\<binding></span></span>  
<span data-ttu-id="cc6e1-108">\<security></span><span class="sxs-lookup"><span data-stu-id="cc6e1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6e1-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cc6e1-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc6e1-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cc6e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc6e1-111">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc6e1-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="cc6e1-112">Attributes</span></span>  
  
|<span data-ttu-id="cc6e1-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="cc6e1-113">Attribute</span></span>|<span data-ttu-id="cc6e1-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cc6e1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc6e1-115">modalità</span><span class="sxs-lookup"><span data-stu-id="cc6e1-115">mode</span></span>|<span data-ttu-id="cc6e1-116">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-116">Optional.</span></span> <span data-ttu-id="cc6e1-117">Specifica il tipo di sicurezza usata.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="cc6e1-118">Il valore predefinito è `None`.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-118">The default is `None`.</span></span> <span data-ttu-id="cc6e1-119">L'attributo è di tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cc6e1-120">Attributo mode</span><span class="sxs-lookup"><span data-stu-id="cc6e1-120">mode Attribute</span></span>  
  
|<span data-ttu-id="cc6e1-121">Valore</span><span class="sxs-lookup"><span data-stu-id="cc6e1-121">Value</span></span>|<span data-ttu-id="cc6e1-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cc6e1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc6e1-123">Nessuna</span><span class="sxs-lookup"><span data-stu-id="cc6e1-123">None</span></span>|<span data-ttu-id="cc6e1-124">-I messaggi non vengono protetti durante il trasferimento.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="cc6e1-125">Trasporto</span><span class="sxs-lookup"><span data-stu-id="cc6e1-125">Transport</span></span>|<span data-ttu-id="cc6e1-126">La sicurezza è fornita mediante il trasporto HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="cc6e1-127">I messaggi SOAP vengono protetti utilizzando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="cc6e1-128">Il servizio viene autenticato sul client mediante il certificato X.509 del servizio.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="cc6e1-129">Il client viene autenticato mediante il ClientCredentialType  fornito.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="cc6e1-130">Vedere il [ \<> di trasporto](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cc6e1-130">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="cc6e1-131">Messaggio</span><span class="sxs-lookup"><span data-stu-id="cc6e1-131">Message</span></span>|<span data-ttu-id="cc6e1-132">La sicurezza è fornita mediante la sicurezza dei messaggi SOAP.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="cc6e1-133">Per impostazione predefinita, il corpo viene crittografato e firmato.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="cc6e1-134">Per questa associazione, il sistema richiede che il certificato server sia fornito al client fuori banda.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="cc6e1-135">L'unico valore `ClientCredentialType` valido per questa associazione è `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="cc6e1-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cc6e1-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="cc6e1-137">Integrità, riservatezza e autenticazione server sono fornite dalla sicurezza del trasporto.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="cc6e1-138">L'autenticazione del client è fornita per mezzo della sicurezza del messaggio SOAP.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="cc6e1-139">Questa modalità è appropriata quando l'utente esegue l'autenticazione usando nome utente/password in presenza di una distribuzione HTTP esistente per la sicurezza del trasferimento dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="cc6e1-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="cc6e1-140">TransportCredentialOnly</span></span>|<span data-ttu-id="cc6e1-141">Questa modalità non fornisce l'integrità e la riservatezza dei messaggi,</span><span class="sxs-lookup"><span data-stu-id="cc6e1-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="cc6e1-142">Fornisce autenticazione client basata su HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-142">It provides http-based client authentication.</span></span> <span data-ttu-id="cc6e1-143">Tale modalità deve essere usata con cautela.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-143">This mode should be used with caution.</span></span> <span data-ttu-id="cc6e1-144">Deve essere utilizzato in ambienti in cui la sicurezza del trasporto viene fornita tramite altri mezzi (ad esempio IPSec) e l'infrastruttura WCF fornisce solo l'autenticazione client.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc6e1-145">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cc6e1-145">Child Elements</span></span>  
  
|<span data-ttu-id="cc6e1-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc6e1-146">Element</span></span>|<span data-ttu-id="cc6e1-147">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="cc6e1-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc6e1-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="cc6e1-148">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="cc6e1-149">Definisce le impostazioni di sicurezza del trasporto per un servizio HTTP di base.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="cc6e1-150">L'elemento corrisponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="cc6e1-151">\<> messaggi</span><span class="sxs-lookup"><span data-stu-id="cc6e1-151">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="cc6e1-152">Definisce le impostazioni di sicurezza del messaggio per un servizio HTTP di base.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="cc6e1-153">L'elemento corrisponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc6e1-154">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cc6e1-154">Parent Elements</span></span>  
  
|<span data-ttu-id="cc6e1-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc6e1-155">Element</span></span>|<span data-ttu-id="cc6e1-156">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cc6e1-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc6e1-157">binding</span><span class="sxs-lookup"><span data-stu-id="cc6e1-157">binding</span></span>|<span data-ttu-id="cc6e1-158">Elemento di associazione della [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cc6e1-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc6e1-159">Note</span><span class="sxs-lookup"><span data-stu-id="cc6e1-159">Remarks</span></span>  
 <span data-ttu-id="cc6e1-160">Per impostazione predefinita, il messaggio SOAP non è protetto e il client non viene autenticato.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="cc6e1-161">Questo elemento consente di configurare impostazioni di sicurezza aggiuntive per l'elemento `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="cc6e1-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6e1-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cc6e1-162">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="cc6e1-163">Protezione di servizi e client</span><span class="sxs-lookup"><span data-stu-id="cc6e1-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cc6e1-164">Selezione di un tipo di credenziale</span><span class="sxs-lookup"><span data-stu-id="cc6e1-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="cc6e1-165">Associazioni</span><span class="sxs-lookup"><span data-stu-id="cc6e1-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc6e1-166">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="cc6e1-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cc6e1-167">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="cc6e1-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cc6e1-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="cc6e1-168">\<binding></span></span>](../../../misc/binding.md)
