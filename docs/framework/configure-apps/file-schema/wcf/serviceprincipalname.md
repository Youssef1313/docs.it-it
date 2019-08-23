---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936162"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="c86f3-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="c86f3-101">\<servicePrincipalName></span></span>
<span data-ttu-id="c86f3-102">Specifica l'identità di un servizio in base al relativo nome dell'entità servizio (SPN, Service Principal Name).</span><span class="sxs-lookup"><span data-stu-id="c86f3-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="c86f3-103">Per ulteriori informazioni sull'impostazione del nome SPN, vedere [identità e autenticazione del servizio](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c86f3-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c86f3-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="c86f3-104">\<identity></span></span>  
<span data-ttu-id="c86f3-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="c86f3-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86f3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c86f3-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c86f3-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c86f3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c86f3-108">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="c86f3-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c86f3-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="c86f3-109">Attributes</span></span>  
  
|<span data-ttu-id="c86f3-110">Attributo</span><span class="sxs-lookup"><span data-stu-id="c86f3-110">Attribute</span></span>|<span data-ttu-id="c86f3-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c86f3-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c86f3-112">value</span><span class="sxs-lookup"><span data-stu-id="c86f3-112">value</span></span>|<span data-ttu-id="c86f3-113">Nome in base al quale un client identifica in modo univoco un'istanza di un servizio.</span><span class="sxs-lookup"><span data-stu-id="c86f3-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="c86f3-114">Se si installano più istanze di un servizio in computer distribuiti in una foresta, a ogni istanza deve essere associato un nome SPN distinto.</span><span class="sxs-lookup"><span data-stu-id="c86f3-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="c86f3-115">Se i client possono usare più nomi per l'autenticazione, una determinata istanza di servizio può presentare più SPN.</span><span class="sxs-lookup"><span data-stu-id="c86f3-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c86f3-116">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c86f3-116">Child Elements</span></span>  
 <span data-ttu-id="c86f3-117">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="c86f3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c86f3-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c86f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c86f3-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c86f3-119">Element</span></span>|<span data-ttu-id="c86f3-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c86f3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c86f3-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="c86f3-121">\<identity></span></span>](identity.md)|<span data-ttu-id="c86f3-122">Specifica l'identità del servizio da autenticare presso il client.</span><span class="sxs-lookup"><span data-stu-id="c86f3-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c86f3-123">Note</span><span class="sxs-lookup"><span data-stu-id="c86f3-123">Remarks</span></span>  
 <span data-ttu-id="c86f3-124">Un client Windows Communication Foundation protetto (WCF) che si connette a un endpoint con questa identità usa il nome SPN quando esegue l'autenticazione SSPI con l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="c86f3-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86f3-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c86f3-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="c86f3-126">Identità del servizio e autenticazione</span><span class="sxs-lookup"><span data-stu-id="c86f3-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c86f3-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="c86f3-127">\<identity></span></span>](identity.md)
