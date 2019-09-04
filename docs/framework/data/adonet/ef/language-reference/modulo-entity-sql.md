---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250075"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="c5769-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c5769-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="c5769-103">Restituisce il resto di un'espressione divisa per un'altra.</span><span class="sxs-lookup"><span data-stu-id="c5769-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5769-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c5769-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5769-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="c5769-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="c5769-106">Espressione numerica da dividere.</span><span class="sxs-lookup"><span data-stu-id="c5769-106">The numeric expression to divide.</span></span> <span data-ttu-id="c5769-107">`dividend` è qualsiasi espressione valida con qualsiasi tipo di dati numerici.</span><span class="sxs-lookup"><span data-stu-id="c5769-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="c5769-108">Espressione numerica per la quale dividere il dividendo.</span><span class="sxs-lookup"><span data-stu-id="c5769-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="c5769-109">`divisor` è qualsiasi espressione valida con qualsiasi tipo di dati numerici.</span><span class="sxs-lookup"><span data-stu-id="c5769-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c5769-110">Tipi di risultati</span><span class="sxs-lookup"><span data-stu-id="c5769-110">Result Types</span></span>  
 <span data-ttu-id="c5769-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="c5769-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5769-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="c5769-112">Example</span></span>  
 <span data-ttu-id="c5769-113">Nella query Entity SQL seguente viene usato l'operatore aritmetico % per restituire il resto della divisione di un'espressione per un'altra.</span><span class="sxs-lookup"><span data-stu-id="c5769-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="c5769-114">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c5769-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c5769-115">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c5769-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c5769-116">Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c5769-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c5769-117">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="c5769-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="c5769-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c5769-118">See also</span></span>

- [<span data-ttu-id="c5769-119">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c5769-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
