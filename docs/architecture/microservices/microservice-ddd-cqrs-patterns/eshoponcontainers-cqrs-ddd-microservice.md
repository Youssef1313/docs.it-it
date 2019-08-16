---
title: Applicazione degli approcci CQRS e CQS in un microservizio DDD in eShopOnContainers
description: Architettura di microservizi .NET per applicazioni .NET incluse in contenitori | Modalità di implementazione di CQRS nel microservizio degli ordini in eShopOnContainers.
ms.date: 10/08/2018
ms.openlocfilehash: 0380e759595e8a159e89f858a5ced4dacfa4e9b4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674128"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a><span data-ttu-id="c207e-103">Applicare gli approcci CQRS e CQS in un microservizio DDD in eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c207e-103">Apply CQRS and CQS approaches in a DDD microservice in eShopOnContainers</span></span>

<span data-ttu-id="c207e-104">La progettazione del microservizio per gli ordini nell'applicazione di riferimento eShopOnContainers è basata sui principi del modello CQRS.</span><span class="sxs-lookup"><span data-stu-id="c207e-104">The design of the ordering microservice at the eShopOnContainers reference application is based on CQRS principles.</span></span> <span data-ttu-id="c207e-105">Tuttavia, usa l'approccio più semplice che consiste nella separazione delle query dai comandi e nell'uso dello stesso database per entrambe le azioni.</span><span class="sxs-lookup"><span data-stu-id="c207e-105">However, it uses the simplest approach, which is just separating the queries from the commands and using the same database for both actions.</span></span>

<span data-ttu-id="c207e-106">L'aspetto essenziale di tali modelli e, in questo caso, il punto importante è che le query sono idempotenti: indipendentemente da quante volte si esegue una query in un sistema, lo stato del sistema non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="c207e-106">The essence of those patterns, and the important point here, is that queries are idempotent: no matter how many times you query a system, the state of that system won't change.</span></span> <span data-ttu-id="c207e-107">In altre parole, le query non hanno effetti collaterali.</span><span class="sxs-lookup"><span data-stu-id="c207e-107">In other words, queries are side-effect free.</span></span>

<span data-ttu-id="c207e-108">Pertanto è possibile usare un modello di dati di "lettura" diverso dal modello di dominio "di scrittura" della logica transazionale, anche se i microservizi di ordinamento usano lo stesso database.</span><span class="sxs-lookup"><span data-stu-id="c207e-108">Therefore, you could use a different “reads” data model than the transactional logic “writes” domain model, even though the ordering microservices are using the same database.</span></span> <span data-ttu-id="c207e-109">Ecco perché questo è un approccio CQRS semplificato.</span><span class="sxs-lookup"><span data-stu-id="c207e-109">Hence, this is a simplified CQRS approach.</span></span>

<span data-ttu-id="c207e-110">D'altra parte, lo stato dei comandi che attivano le transazioni e gli aggiornamenti dei dati cambia nel sistema.</span><span class="sxs-lookup"><span data-stu-id="c207e-110">On the other hand, commands, which trigger transactions and data updates, change state in the system.</span></span> <span data-ttu-id="c207e-111">Con i comandi, occorre prestare attenzione quando si affrontano scenari complessi e regole aziendali in continua evoluzione.</span><span class="sxs-lookup"><span data-stu-id="c207e-111">With commands, you need to be careful when dealing with complexity and ever-changing business rules.</span></span> <span data-ttu-id="c207e-112">Ecco perché le tecniche di progettazione DDD consentono di ottenere un sistema con una modellazione ottimale.</span><span class="sxs-lookup"><span data-stu-id="c207e-112">This is where you want to apply DDD techniques to have a better modeled system.</span></span>

<span data-ttu-id="c207e-113">Gli schemi DDD presentati in questa guida non devono essere applicati a livello universale,</span><span class="sxs-lookup"><span data-stu-id="c207e-113">The DDD patterns presented in this guide should not be applied universally.</span></span> <span data-ttu-id="c207e-114">perché introducono vincoli nella progettazione.</span><span class="sxs-lookup"><span data-stu-id="c207e-114">They introduce constraints on your design.</span></span> <span data-ttu-id="c207e-115">Questi vincoli offrono vantaggi come una migliore qualità nel tempo, in particolare per i comandi e il codice che modifica lo stato del sistema.</span><span class="sxs-lookup"><span data-stu-id="c207e-115">Those constraints provide benefits such as higher quality over time, especially in commands and other code that modifies system state.</span></span> <span data-ttu-id="c207e-116">Tuttavia, questi vincoli aggiungono complessità con vantaggi ridotti per la lettura e le query sui dati.</span><span class="sxs-lookup"><span data-stu-id="c207e-116">However, those constraints add complexity with fewer benefits for reading and querying data.</span></span>

<span data-ttu-id="c207e-117">Uno di questi schemi è lo schema Aggregate che verrà esaminato più in dettaglio nelle sezioni successive.</span><span class="sxs-lookup"><span data-stu-id="c207e-117">One such pattern is the Aggregate pattern, which we examine more in later sections.</span></span> <span data-ttu-id="c207e-118">In breve, nello schema Aggregate, gli oggetti di dominio vengono considerati come una singola unità in virtù della relativa relazione nel dominio.</span><span class="sxs-lookup"><span data-stu-id="c207e-118">Briefly, in the Aggregate pattern, you treat many domain objects as a single unit as a result of their relationship in the domain.</span></span> <span data-ttu-id="c207e-119">Non sempre questo schema genera vantaggi nelle query, in quanto può aumentare la complessità della logica di query.</span><span class="sxs-lookup"><span data-stu-id="c207e-119">You might not always gain advantages from this pattern in queries; it can increase the complexity of query logic.</span></span> <span data-ttu-id="c207e-120">Per le query di sola lettura non è vantaggioso considerare più oggetti come una singola aggregazione.</span><span class="sxs-lookup"><span data-stu-id="c207e-120">For read-only queries, you do not get the advantages of treating multiple objects as a single Aggregate.</span></span> <span data-ttu-id="c207e-121">Aumenta solo la complessità.</span><span class="sxs-lookup"><span data-stu-id="c207e-121">You only get the complexity.</span></span>

<span data-ttu-id="c207e-122">Come illustrato nella figura 7-2, questa guida suggerisce l'uso di schemi di progettazione DDD solo nell'area transazionale e degli aggiornamenti del microservizio, ovvero quella attivata dai comandi.</span><span class="sxs-lookup"><span data-stu-id="c207e-122">As shown in Figure 7-2, this guide suggests using DDD patterns only in the transactional/updates area of your microservice (that is, as triggered by commands).</span></span> <span data-ttu-id="c207e-123">Le query possono seguire un approccio più semplice e devono essere separate dai comandi, secondo quanto previsto dall'approccio CQRS.</span><span class="sxs-lookup"><span data-stu-id="c207e-123">Queries can follow a simpler approach and should be separated from commands, following a CQRS approach.</span></span>

<span data-ttu-id="c207e-124">Per implementare il "lato query" è possibile scegliere tra numerosi approcci, ad esempio uno basato su ORM (Object-Relational Mapping), come EF Core, proiezioni di AutoMapper, stored procedure, viste, viste materializzate o micro ORM.</span><span class="sxs-lookup"><span data-stu-id="c207e-124">For implementing the “queries side”, you can choose between many approaches, from your full-blown ORM like EF Core, AutoMapper projections, stored procedures, views, materialized views or a micro ORM.</span></span>

<span data-ttu-id="c207e-125">In questa guida e in eShopOnContainers, in particolare nel microservizio degli ordini, è stato scelto di implementare query lineari tramite un micro ORM come [Dapper](https://github.com/StackExchange/dapper-dot-net).</span><span class="sxs-lookup"><span data-stu-id="c207e-125">In this guide and in eShopOnContainers (specifically the ordering microservice) we chose to implement straight queries using a micro ORM like [Dapper](https://github.com/StackExchange/dapper-dot-net).</span></span> <span data-ttu-id="c207e-126">In questo modo è possibile implementare qualsiasi query basata su istruzioni SQL per ottenere le prestazioni migliori, grazie a un framework leggero con un sovraccarico ridotto.</span><span class="sxs-lookup"><span data-stu-id="c207e-126">This lets you implement any query based on SQL statements to get the best performance, thanks to a light framework with very little overhead.</span></span>

<span data-ttu-id="c207e-127">Si noti che quando si usa questo approccio, gli aggiornamenti al modello che influiscono sul modo in cui le entità vengono salvate in modo permanente in un database SQL devono separare gli aggiornamenti alle query SQL usate da Dapper o da qualsiasi altro approccio separato (non EF) all'esecuzione di query.</span><span class="sxs-lookup"><span data-stu-id="c207e-127">Note that when you use this approach, any updates to your model that impact how entities are persisted to a SQL database also need separate updates to SQL queries used by Dapper or any other separate (non-EF) approaches to querying.</span></span>

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a><span data-ttu-id="c207e-128">Gli schemi CQRS e DDD non sono architetture di primo livello</span><span class="sxs-lookup"><span data-stu-id="c207e-128">CQRS and DDD patterns are not top-level architectures</span></span>

<span data-ttu-id="c207e-129">È importante comprendere che gli schemi CQRS e la maggior parte degli schemi DDD, come i livelli DDD o un modello di dominio con aggregazioni, non sono stili architetturali, ma solo schemi di architetture.</span><span class="sxs-lookup"><span data-stu-id="c207e-129">It's important to understand that CQRS and most DDD patterns (like DDD layers or a domain model with aggregates) are not architectural styles, but only architecture patterns.</span></span> <span data-ttu-id="c207e-130">I microservizi, l'architettura orientata ai servizi (SOA) e l'architettura basata su eventi (EDA) sono esempi di stili architetturali.</span><span class="sxs-lookup"><span data-stu-id="c207e-130">Microservices, SOA, and event-driven architecture (EDA) are examples of architectural styles.</span></span> <span data-ttu-id="c207e-131">Descrivono un sistema costituito da molti componenti, ad esempio vari microservizi.</span><span class="sxs-lookup"><span data-stu-id="c207e-131">They describe a system of many components, such as many microservices.</span></span> <span data-ttu-id="c207e-132">Gli schemi CQRS e DDD descrivono un aspetto all'interno di un singolo sistema o componente. In questo caso, all'interno di un microservizio.</span><span class="sxs-lookup"><span data-stu-id="c207e-132">CQRS and DDD patterns describe something inside a single system or component; in this case, something inside a microservice.</span></span>

<span data-ttu-id="c207e-133">Diversi contesti delimitati useranno schemi differenti.</span><span class="sxs-lookup"><span data-stu-id="c207e-133">Different Bounded Contexts (BCs) will employ different patterns.</span></span> <span data-ttu-id="c207e-134">Poiché hanno responsabilità diverse, verranno impiegate soluzioni differenziate.</span><span class="sxs-lookup"><span data-stu-id="c207e-134">They have different responsibilities, and that leads to different solutions.</span></span> <span data-ttu-id="c207e-135">Tenere presente che forzare lo stesso schema ovunque può generare errori.</span><span class="sxs-lookup"><span data-stu-id="c207e-135">It is worth emphasizing that forcing the same pattern everywhere leads to failure.</span></span> <span data-ttu-id="c207e-136">Non usare gli schemi CQRS e DDD ovunque.</span><span class="sxs-lookup"><span data-stu-id="c207e-136">Do not use CQRS and DDD patterns everywhere.</span></span> <span data-ttu-id="c207e-137">Molti sottosistemi, contesti delimitati o microservizi sono più semplici e possono essere implementati facilmente con servizi CRUD o altri approcci.</span><span class="sxs-lookup"><span data-stu-id="c207e-137">Many subsystems, BCs, or microservices are simpler and can be implemented more easily using simple CRUD services or using another approach.</span></span>

<span data-ttu-id="c207e-138">Esiste una sola architettura dell'applicazione: l'architettura del sistema o dell'applicazione end-to-end che si sta progettando, ad esempio l'architettura di microservizi.</span><span class="sxs-lookup"><span data-stu-id="c207e-138">There is only one application architecture: the architecture of the system or end-to-end application you are designing (for example, the microservices architecture).</span></span> <span data-ttu-id="c207e-139">Tuttavia la progettazione di ogni contesto delimitato o microservizio all'interno dell'applicazione riflette i compromessi e le decisioni di progettazione interne al livello degli schemi di architettura.</span><span class="sxs-lookup"><span data-stu-id="c207e-139">However, the design of each Bounded Context or microservice within that application reflects its own tradeoffs and internal design decisions at an architecture patterns level.</span></span> <span data-ttu-id="c207e-140">Non provare ad applicare gli stessi schemi architetturali, come CQRS o DDD, ovunque.</span><span class="sxs-lookup"><span data-stu-id="c207e-140">Do not try to apply the same architectural patterns like CQRS or DDD everywhere.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c207e-141">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="c207e-141">Additional resources</span></span>

- <span data-ttu-id="c207e-142">**Martin Fowler. CQRS** </span><span class="sxs-lookup"><span data-stu-id="c207e-142">**Martin Fowler. CQRS** </span></span>\
  <https://martinfowler.com/bliki/CQRS.html>

- <span data-ttu-id="c207e-143">**Greg Young. Documenti CQRS** </span><span class="sxs-lookup"><span data-stu-id="c207e-143">**Greg Young. CQRS Documents** </span></span>\
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- <span data-ttu-id="c207e-144">**Udi Dahan. Clarified CQRS** \ (Definizione di CQRS)</span><span class="sxs-lookup"><span data-stu-id="c207e-144">**Udi Dahan. Clarified CQRS** \</span></span>
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
><span data-ttu-id="c207e-145">[Precedente](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[Successivo](cqrs-microservice-reads.md)</span><span class="sxs-lookup"><span data-stu-id="c207e-145">[Previous](apply-simplified-microservice-cqrs-ddd-patterns.md)
[Next](cqrs-microservice-reads.md)</span></span>