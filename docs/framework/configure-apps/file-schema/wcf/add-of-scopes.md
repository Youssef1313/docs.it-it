---
title: <add> di <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926622"
---
# <a name="add-of-scopes"></a><span data-ttu-id="3053d-102">\<aggiungere > degli \<ambiti ></span><span class="sxs-lookup"><span data-stu-id="3053d-102">\<add> of \<scopes></span></span>
<span data-ttu-id="3053d-103">Aggiunge URI di ambito personalizzato che è possibile usare per filtrare gli endpoint di servizio durante l'esecuzione di query.</span><span class="sxs-lookup"><span data-stu-id="3053d-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="3053d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3053d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3053d-105">\<comportamenti ></span><span class="sxs-lookup"><span data-stu-id="3053d-105">\<behaviors></span></span>  
<span data-ttu-id="3053d-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3053d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="3053d-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="3053d-107">\<behavior></span></span>  
<span data-ttu-id="3053d-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="3053d-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="3053d-109">\<ambiti ></span><span class="sxs-lookup"><span data-stu-id="3053d-109">\<scopes></span></span>  
<span data-ttu-id="3053d-110">\<add></span><span class="sxs-lookup"><span data-stu-id="3053d-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3053d-111">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3053d-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3053d-112">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="3053d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3053d-113">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="3053d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3053d-114">Attributi</span><span class="sxs-lookup"><span data-stu-id="3053d-114">Attributes</span></span>  
  
|<span data-ttu-id="3053d-115">Attributo</span><span class="sxs-lookup"><span data-stu-id="3053d-115">Attribute</span></span>|<span data-ttu-id="3053d-116">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3053d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3053d-117">scope</span><span class="sxs-lookup"><span data-stu-id="3053d-117">scope</span></span>|<span data-ttu-id="3053d-118">URI contenente informazioni sull'ambito per l'endpoint che è possibile usare nei criteri di corrispondenza per la ricerca di servizi.</span><span class="sxs-lookup"><span data-stu-id="3053d-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3053d-119">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3053d-119">Child Elements</span></span>  
 <span data-ttu-id="3053d-120">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="3053d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3053d-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3053d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3053d-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="3053d-122">Element</span></span>|<span data-ttu-id="3053d-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3053d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3053d-124">\<ambiti ></span><span class="sxs-lookup"><span data-stu-id="3053d-124">\<scopes></span></span>](scopes.md)|<span data-ttu-id="3053d-125">Contiene una raccolta di elementi di configurazione che specificano URI di ambito personalizzati che è possibile usare per filtrare gli endpoint del servizio durante l'esecuzione di query.</span><span class="sxs-lookup"><span data-stu-id="3053d-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3053d-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3053d-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
