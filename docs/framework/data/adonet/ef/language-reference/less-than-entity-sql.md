---
title: < (Minore di) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: fb3f4a1c6bc0df6af3c27836f7b53b2701776366
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319687"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="0baf6-102">\< (minore di) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0baf6-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="0baf6-103">Consente di confrontare due espressioni per determinare se l'espressione a sinistra ha un valore minore di quella a destra.</span><span class="sxs-lookup"><span data-stu-id="0baf6-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0baf6-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0baf6-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0baf6-105">argomenti</span><span class="sxs-lookup"><span data-stu-id="0baf6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0baf6-106">Qualsiasi espressione valida.</span><span class="sxs-lookup"><span data-stu-id="0baf6-106">Any valid expression.</span></span> <span data-ttu-id="0baf6-107">Entrambe le espressioni devono contenere tipi di dati convertibili in modo implicito.</span><span class="sxs-lookup"><span data-stu-id="0baf6-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0baf6-108">Tipi di risultati</span><span class="sxs-lookup"><span data-stu-id="0baf6-108">Result Types</span></span>  
 <span data-ttu-id="0baf6-109">`true` se l'espressione a sinistra ha un valore minore di quella a destra; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="0baf6-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0baf6-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="0baf6-110">Example</span></span>  
 <span data-ttu-id="0baf6-111">Nella query Entity SQL seguente viene usato l'operatore di confronto < per confrontare due espressioni e determinare se l'espressione a sinistra ha un valore minore di quella a destra.</span><span class="sxs-lookup"><span data-stu-id="0baf6-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="0baf6-112">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0baf6-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0baf6-113">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="0baf6-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0baf6-114">Seguire la procedura indicata in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0baf6-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0baf6-115">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="0baf6-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="0baf6-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0baf6-116">See also</span></span>

- [<span data-ttu-id="0baf6-117">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0baf6-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
