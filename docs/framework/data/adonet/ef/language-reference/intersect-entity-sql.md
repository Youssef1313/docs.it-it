---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319772"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="ed235-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed235-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="ed235-103">Restituisce una raccolta di tutti i valori distinti restituiti da entrambe le espressioni di query a sinistra e a destra dell'operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="ed235-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ed235-104">Tutte le espressioni devono essere dello stesso tipo o di un tipo di base o derivato comune di `expression`.</span><span class="sxs-lookup"><span data-stu-id="ed235-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed235-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ed235-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed235-106">argomenti</span><span class="sxs-lookup"><span data-stu-id="ed235-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ed235-107">Qualsiasi espressione di query valida che restituisce una raccolta da confrontare con la raccolta restituita da un'altra espressione di query.</span><span class="sxs-lookup"><span data-stu-id="ed235-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed235-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ed235-108">Return Value</span></span>  
 <span data-ttu-id="ed235-109">Raccolta dello stesso tipo o di un tipo di base o derivato comune di `expression`.</span><span class="sxs-lookup"><span data-stu-id="ed235-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed235-110">Note</span><span class="sxs-lookup"><span data-stu-id="ed235-110">Remarks</span></span>  
 <span data-ttu-id="ed235-111">INTERSECT è uno degli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed235-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ed235-112">Tutti gli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vengono valutati da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="ed235-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ed235-113">Per informazioni sulla precedenza per gli operatori set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vedere [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ed235-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed235-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="ed235-114">Example</span></span>  
 <span data-ttu-id="ed235-115">Nella query Entity SQL seguente viene usato l'operatore INTERSECT per restituire una raccolta di tutti i valori distinti restituiti da entrambe le espressioni di query a sinistra e a destra dell'operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="ed235-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ed235-116">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ed235-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed235-117">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ed235-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ed235-118">Seguire la procedura indicata in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ed235-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ed235-119">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ed235-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="ed235-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed235-120">See also</span></span>

- [<span data-ttu-id="ed235-121">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ed235-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
