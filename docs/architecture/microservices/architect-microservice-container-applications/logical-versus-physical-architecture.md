---
title: Architettura logica e architettura fisica
description: Informazioni sulle differenze tra architetture logiche e architetture fisiche.
ms.date: 09/20/2018
ms.openlocfilehash: c269369e9b5391e8d25ece46e6b08e34a82fbbba
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673058"
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="4ee4b-103">Architettura logica e architettura fisica</span><span class="sxs-lookup"><span data-stu-id="4ee4b-103">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="4ee4b-104">A questo punto, è utile fermarsi per esaminare la distinzione tra architettura logica e architettura fisica e valutare come si applica alla progettazione di applicazioni basate su microservizi.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-104">It's useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="4ee4b-105">Per iniziare, la creazione di microservizi non richiede l'uso di alcuna tecnologia specifica.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-105">To begin, building microservices doesn't require the use of any specific technology.</span></span> <span data-ttu-id="4ee4b-106">Ad esempio, non è obbligatorio usare contenitori Docker per creare un'architettura basata su microservizi.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-106">For instance, Docker containers aren't mandatory to create a microservice-based architecture.</span></span> <span data-ttu-id="4ee4b-107">I microservizi possono anche essere eseguiti come processi normali.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-107">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="4ee4b-108">I microservizi sono un'architettura logica.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-108">Microservices is a logical architecture.</span></span>

<span data-ttu-id="4ee4b-109">Inoltre, anche quando è possibile implementare un microservizio fisicamente come un singolo servizio, processo o contenitore (per semplicità, questo è l'approccio adottato per la versione iniziale di [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), questa parità tra microservizi aziendali e contenitori o servizi fisici non è necessariamente richiesta in tutti i casi quando si crea un'applicazione complessa di grandi dimensioni costituita da decine o centinaia di servizi.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-109">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity's sake, that's the approach taken in the initial version of [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container isn't necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="4ee4b-110">Qui sta la differenza tra l'architettura logica e l'architettura fisica di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-110">This is where there's a difference between an application's logical architecture and physical architecture.</span></span> <span data-ttu-id="4ee4b-111">L'architettura logica e i limiti logici di un sistema non presentano necessariamente un mapping di uno-a-uno rispetto all'architettura di distribuzione o fisica.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-111">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="4ee4b-112">Può verificarsi, ma spesso non accade.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-112">It can happen, but it often doesn't.</span></span>

<span data-ttu-id="4ee4b-113">Sebbene possano essere stati identificati alcuni microservizi aziendali o contesti delimitati, questo non significa che il miglior modo di implementarli sia sempre costituito dalla creazione di un singolo servizio, ad esempio un'API Web ASP.NET, o un singolo contenitore Docker per ogni microservizio aziendale.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-113">Although you might have identified certain business microservices or Bounded Contexts, it doesn't mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="4ee4b-114">Una regola che prevede che ogni microservizio aziendale debba essere implementato con un singolo servizio o contenitore è troppo rigida.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-114">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="4ee4b-115">Di conseguenza, un microservizio aziendale o un contesto delimitato è un'architettura logica che potrebbe coincidere (oppure no) con l'architettura fisica.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-115">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="4ee4b-116">Il punto importante è che un microservizio aziendale o un contesto delimitato deve essere autonomo e consentire al codice e allo stato il controllo delle versioni, la distribuzione e il ridimensionamento indipendenti.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-116">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="4ee4b-117">Come mostrato nella figura 4-8, il microservizio aziendale del catalogo può essere composto da numerosi servizi o processi.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-117">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="4ee4b-118">Questi possono essere costituiti da più servizi API Web ASP.NET o da altre tipologie di servizi che usano HTTP o altri protocolli.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-118">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="4ee4b-119">Inoltre, i servizi possono condividere gli stessi dati, purché siano coesi rispetto allo stesso dominio aziendale.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-119">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![Diagramma del microservizio aziendale del catalogo, che contiene un servizio API, un servizio di ricerca e un database di SQL Server.](./media/image8.png)

<span data-ttu-id="4ee4b-121">**Figura 4-8**.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-121">**Figure 4-8**.</span></span> <span data-ttu-id="4ee4b-122">Microservizio aziendale con numerosi servizi fisici</span><span class="sxs-lookup"><span data-stu-id="4ee4b-122">Business microservice with several physical services</span></span>

<span data-ttu-id="4ee4b-123">I servizi nell'esempio condividono lo stesso modello di dati perché il servizio API Web usa gli stessi dati del servizio di ricerca.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="4ee4b-124">Quindi, nell'implementazione fisica del microservizio aziendale si divide questa funzionalità per poter ridimensionare ogni servizio interno in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-124">So, in the physical implementation of the business microservice, you're splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="4ee4b-125">Nella maggior parte dei casi il servizio API Web potrebbe richiedere un maggior numero di istanze rispetto al servizio di ricerca o viceversa.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.</span></span>

<span data-ttu-id="4ee4b-126">In breve, l'architettura logica dei microservizi non deve sempre coincidere con l'architettura di distribuzione fisica.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-126">In short, the logical architecture of microservices doesn't always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="4ee4b-127">In questa guida ogni volta che viene citato un microservizio si intente un microservizio logico o aziendale che può essere mappato a uno o più servizi (fisici).</span><span class="sxs-lookup"><span data-stu-id="4ee4b-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more (physical) services.</span></span> <span data-ttu-id="4ee4b-128">Nella maggior parte dei casi, si tratterà di un singolo servizio, ma potrebbero anche essere più servizi.</span><span class="sxs-lookup"><span data-stu-id="4ee4b-128">In most cases, this will be a single service, but it might be more.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4ee4b-129">[Precedente](data-sovereignty-per-microservice.md)
>[Successivo](distributed-data-management.md)</span><span class="sxs-lookup"><span data-stu-id="4ee4b-129">[Previous](data-sovereignty-per-microservice.md)
[Next](distributed-data-management.md)</span></span>