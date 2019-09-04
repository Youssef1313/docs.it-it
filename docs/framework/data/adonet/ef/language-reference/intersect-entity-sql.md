---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250595"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="e2aa1-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2aa1-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="e2aa1-103">Restituisce una raccolta di tutti i valori distinti restituiti da entrambe le espressioni di query a sinistra e a destra dell'operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="e2aa1-104">Tutte le espressioni devono essere dello stesso tipo o di un tipo di base o derivato comune di `expression`.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2aa1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e2aa1-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2aa1-106">Argomenti</span><span class="sxs-lookup"><span data-stu-id="e2aa1-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e2aa1-107">Qualsiasi espressione di query valida che restituisce una raccolta da confrontare con la raccolta restituita da un'altra espressione di query.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2aa1-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e2aa1-108">Return Value</span></span>  
 <span data-ttu-id="e2aa1-109">Raccolta dello stesso tipo o di un tipo di base o derivato comune di `expression`.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2aa1-110">Note</span><span class="sxs-lookup"><span data-stu-id="e2aa1-110">Remarks</span></span>  
 <span data-ttu-id="e2aa1-111">INTERSECT è uno degli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2aa1-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e2aa1-112">Tutti gli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vengono valutati da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e2aa1-113">Per informazioni sulla precedenza per [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gli operatori sui set, vedere [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa1-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2aa1-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="e2aa1-114">Example</span></span>  
 <span data-ttu-id="e2aa1-115">Nella query Entity SQL seguente viene usato l'operatore INTERSECT per restituire una raccolta di tutti i valori distinti restituiti da entrambe le espressioni di query a sinistra e a destra dell'operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="e2aa1-116">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2aa1-117">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e2aa1-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e2aa1-118">Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.</span><span class="sxs-lookup"><span data-stu-id="e2aa1-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e2aa1-119">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e2aa1-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="e2aa1-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e2aa1-120">See also</span></span>

- [<span data-ttu-id="e2aa1-121">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2aa1-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
