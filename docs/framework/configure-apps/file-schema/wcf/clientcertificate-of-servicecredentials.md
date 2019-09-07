---
title: <clientCertificate> di <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398130"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="6e46d-102">\<ClientCertificate > di \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="6e46d-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="6e46d-103">Definisce un certificato X.509 usato per firmare e crittografare i messaggi da un client a un servizio in un modello di comunicazione duplex.</span><span class="sxs-lookup"><span data-stu-id="6e46d-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
<span data-ttu-id="6e46d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e46d-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6e46d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamenti >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6e46d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6e46d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamento >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="6e46d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> di serviceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="6e46d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="6e46d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientCertificate**</span><span class="sxs-lookup"><span data-stu-id="6e46d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e46d-111">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6e46d-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e46d-112">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="6e46d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6e46d-113">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="6e46d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e46d-114">Attributi</span><span class="sxs-lookup"><span data-stu-id="6e46d-114">Attributes</span></span>  
 <span data-ttu-id="6e46d-115">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="6e46d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e46d-116">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="6e46d-116">Child Elements</span></span>  
  
|<span data-ttu-id="6e46d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e46d-117">Element</span></span>|<span data-ttu-id="6e46d-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6e46d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e46d-119">\<authentication></span><span class="sxs-lookup"><span data-stu-id="6e46d-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="6e46d-120">Specifica le opzioni di autenticazione del certificato client.</span><span class="sxs-lookup"><span data-stu-id="6e46d-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="6e46d-121">\<> certificato</span><span class="sxs-lookup"><span data-stu-id="6e46d-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="6e46d-122">Specifica il certificato da usare.</span><span class="sxs-lookup"><span data-stu-id="6e46d-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e46d-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="6e46d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e46d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e46d-124">Element</span></span>|<span data-ttu-id="6e46d-125">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="6e46d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e46d-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6e46d-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="6e46d-127">Specifica le credenziali da usare nell'autenticazione del servizio e le impostazioni relative alla convalida delle credenziali client.</span><span class="sxs-lookup"><span data-stu-id="6e46d-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e46d-128">Note</span><span class="sxs-lookup"><span data-stu-id="6e46d-128">Remarks</span></span>  
 <span data-ttu-id="6e46d-129">Questo elemento viene usato quando il servizio deve disporre in anticipo del certificato del client per poter comunicare in modo sicuro con il client.</span><span class="sxs-lookup"><span data-stu-id="6e46d-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="6e46d-130">Questa esigenza si presenta quando si usa il modello di comunicazione duplex.</span><span class="sxs-lookup"><span data-stu-id="6e46d-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="6e46d-131">Nel modello più comune di comunicazione richiesta/risposta, il client include il proprio certificato nella richiesta e il servizio usa tale certificato per crittografare e firmare la risposta che invia al client.</span><span class="sxs-lookup"><span data-stu-id="6e46d-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="6e46d-132">Nel modello di comunicazione duplex, tuttavia, il servizio non riceve alcuna richiesta dal client e pertanto deve disporre in anticipo del certificato del client per proteggere il messaggio da inviare al client.</span><span class="sxs-lookup"><span data-stu-id="6e46d-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="6e46d-133">Questo certificato deve quindi essere ottenuto mediante una negoziazione fuori banda e deve essere specificato tramite questo elemento.</span><span class="sxs-lookup"><span data-stu-id="6e46d-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="6e46d-134">Per ulteriori informazioni sui servizi duplex, vedere [procedura: Creazione di un contratto](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.</span><span class="sxs-lookup"><span data-stu-id="6e46d-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="6e46d-135">Il certificato impostato in questo elemento viene usato per crittografare i messaggi indirizzati al client solo per le associazioni configurate con la modalità di autenticazione di sicurezza dei messaggi `MutualCertificateDuplex`.</span><span class="sxs-lookup"><span data-stu-id="6e46d-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e46d-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6e46d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="6e46d-137">Procedura: Creazione di un contratto duplex</span><span class="sxs-lookup"><span data-stu-id="6e46d-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="6e46d-138">Comportamenti di sicurezza</span><span class="sxs-lookup"><span data-stu-id="6e46d-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6e46d-139">Uso di certificati</span><span class="sxs-lookup"><span data-stu-id="6e46d-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
