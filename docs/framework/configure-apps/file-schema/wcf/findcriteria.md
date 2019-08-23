---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925589"
---
# <a name="findcriteria"></a><span data-ttu-id="93355-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="93355-101">\<findCriteria></span></span>
<span data-ttu-id="93355-102">Elemento di configurazione che fornisce un set di criteri usati da un'applicazione client per la ricerca di un servizio di individuazione.</span><span class="sxs-lookup"><span data-stu-id="93355-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="93355-103">I criteri possono essere raggruppati in criteri di ricerca (specificando i servizi desiderati) e individuare i criteri di terminazione (durata della ricerca).</span><span class="sxs-lookup"><span data-stu-id="93355-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="93355-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93355-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="93355-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="93355-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93355-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="93355-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93355-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="93355-107">Attributes and Elements</span></span>  
 <span data-ttu-id="93355-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="93355-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93355-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="93355-109">Attributes</span></span>  
  
|<span data-ttu-id="93355-110">Attributo</span><span class="sxs-lookup"><span data-stu-id="93355-110">Attribute</span></span>|<span data-ttu-id="93355-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="93355-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93355-112">duration</span><span class="sxs-lookup"><span data-stu-id="93355-112">duration</span></span>|<span data-ttu-id="93355-113">Valore Timespan che specifica il tempo massimo di attesa per le risposte dai servizi in una rete.</span><span class="sxs-lookup"><span data-stu-id="93355-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="93355-114">La durata predefinita è 20 secondi.</span><span class="sxs-lookup"><span data-stu-id="93355-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="93355-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="93355-115">maxResults</span></span>|<span data-ttu-id="93355-116">Integer che specifica il numero massimo di risposte da attendere dai servizi in una rete o su Internet.</span><span class="sxs-lookup"><span data-stu-id="93355-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="93355-117">Se il numero massimo di risposte viene ricevuto prima della scadenza del valore specificato nell'attributo `duration`, l'operazione di ricerca termina.</span><span class="sxs-lookup"><span data-stu-id="93355-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="93355-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="93355-118">scopeMatchBy</span></span>|<span data-ttu-id="93355-119">URI che specifica l'algoritmo di corrispondenza da usare per trovare la corrispondenza tra l'ambito nel messaggio del Probe e quello dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="93355-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="93355-120">Sono supportate cinque regole di corrispondenza degli ambiti.</span><span class="sxs-lookup"><span data-stu-id="93355-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="93355-121">Se non si specifica una regola di corrispondenza degli ambiti, verrà usato `ScopeMatchByPrefix`.</span><span class="sxs-lookup"><span data-stu-id="93355-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="93355-122">Per altre informazioni in merito, vedere <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="93355-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93355-123">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="93355-123">Child Elements</span></span>  
  
|<span data-ttu-id="93355-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="93355-124">Element</span></span>|<span data-ttu-id="93355-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="93355-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93355-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="93355-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="93355-127">Raccolta di elementi di configurazione che contengono i nomi dei tipi di contratto di servizio del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="93355-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="93355-128">\<estensioni > di \<FindCriteria ></span><span class="sxs-lookup"><span data-stu-id="93355-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="93355-129">Raccolta di oggetti di elementi XML che forniscono estensioni.</span><span class="sxs-lookup"><span data-stu-id="93355-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="93355-130">\<ambiti ></span><span class="sxs-lookup"><span data-stu-id="93355-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="93355-131">Raccolta di oggetti contenenti URI assoluti usati durante un'operazione di ricerca per l'individuazione di uno o più servizi specifici.</span><span class="sxs-lookup"><span data-stu-id="93355-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="93355-132">Se il servizio specifico viene trovato, significa che è stata trovata una corrispondenza esatta tra l'URI del servizio e l'URI dell'ambito, talvolta con il supporto di regole di ambito che gestiscono i problemi di corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="93355-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93355-133">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="93355-133">Parent Elements</span></span>  
  
|<span data-ttu-id="93355-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="93355-134">Element</span></span>|<span data-ttu-id="93355-135">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="93355-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93355-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="93355-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="93355-137">Contiene le impostazioni necessarie a un'applicazione per partecipare al processo di individuazione del servizio come client.</span><span class="sxs-lookup"><span data-stu-id="93355-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93355-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="93355-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
