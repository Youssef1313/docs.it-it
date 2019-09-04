---
title: Funzioni di aggregazione (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251342"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="3f2fd-102">Funzioni di aggregazione (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3f2fd-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="3f2fd-103">Un'aggregazione è un construct di linguaggio che condensa una raccolta in un scalare come parte di un'operazione di gruppo.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> <span data-ttu-id="3f2fd-104">Le aggregazioni [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sono disponibili in due formati:</span><span class="sxs-lookup"><span data-stu-id="3f2fd-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3f2fd-105">funzioni di raccolta che possono essere utilizzate in qualsiasi punto di un'espressione.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="3f2fd-106">È incluso l'utilizzo di funzioni di aggregazione nelle proiezioni e di predicati che agiscono sulle raccolte.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="3f2fd-107">Le funzioni di raccolta sono la modalità preferibile di specificare aggregazioni in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f2fd-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="3f2fd-108">Aggregazioni di gruppo in espressioni di query che dispongono di una clausola GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="3f2fd-109">Come in Transact-SQL, le aggregazioni di gruppo accettano DISTINCT e ALL come modificatori nell'input di aggregazione.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3f2fd-110">tenta innanzitutto di interpretare un'espressione come una funzione di raccolta e se l'espressione si trova nel contesto di un'espressione SELECT, interpretata come aggregazione di gruppo.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3f2fd-111">definisce uno speciale operatore di aggregazione denominato [GROUPPARTITION](grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3f2fd-111">defines a special aggregate operator called [GROUPPARTITION](grouppartition-entity-sql.md).</span></span> <span data-ttu-id="3f2fd-112">Questo operatore consente di ottenere un riferimento al set di input raggruppato.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="3f2fd-113">Questo consente di ottenere query di raggruppamento più avanzate, dove i risultati della clausola GROUP BY possono essere usati in posizioni diverse dalle funzioni di raccolta o di aggregazione di gruppo.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="3f2fd-114">Funzioni di raccolta</span><span class="sxs-lookup"><span data-stu-id="3f2fd-114">Collection Functions</span></span>  
 <span data-ttu-id="3f2fd-115">Le funzioni della Collection operano su raccolte e restituiscono un valore scalare.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="3f2fd-116">Ad esempio, se `orders` è una raccolta di tutti gli oggetti `orders`, è possibile calcolare la prima data di spedizione usando l'espressione seguente:</span><span class="sxs-lookup"><span data-stu-id="3f2fd-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="3f2fd-117">Aggregazioni di gruppo</span><span class="sxs-lookup"><span data-stu-id="3f2fd-117">Group Aggregates</span></span>  
 <span data-ttu-id="3f2fd-118">Le aggregazioni di gruppo vengono calcolate su un risultato di gruppo definito dalla clausola GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="3f2fd-119">La clausola GROUP BY suddivide i dati in gruppi.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="3f2fd-120">Per ogni gruppo nel risultato, viene applicata la funzione di aggregazione e viene calcolata un'aggregazione distinta usando gli elementi in ciascun gruppo come input nel calcolo dell'aggregazione.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="3f2fd-121">Quando in un'espressione SELECT viene usata una clausola GROUP BY, nella proiezione, nella clausola ORDER BY o HAVING possono essere presenti solo nomi di espressioni di raggruppamento, aggregazioni o espressioni costanti.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="3f2fd-122">Nell'esempio seguente viene calcolata la quantità media ordinata per ciascun prodotto.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="3f2fd-123">È possibile usare un'aggregazione di gruppo senza una clausola GROUP BY esplicita nell'espressione SELECT.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="3f2fd-124">Tutti gli elementi saranno trattati come un gruppo singolo, equivalente al caso della specifica di un raggruppamento basato su una costante.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="3f2fd-125">Le espressioni usate nella clausola GROUP BY vengono valutate usando lo stesso ambito di risoluzione dei nomi che sarebbe visibile all'espressione con la clausola WHERE.</span><span class="sxs-lookup"><span data-stu-id="3f2fd-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f2fd-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f2fd-126">See also</span></span>

- [<span data-ttu-id="3f2fd-127">Funzioni</span><span class="sxs-lookup"><span data-stu-id="3f2fd-127">Functions</span></span>](functions-entity-sql.md)
