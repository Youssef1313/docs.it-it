---
title: '>= (Maggiore o uguale a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833749"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="71163-102">> = (maggiore o uguale a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="71163-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="71163-103">Consente di confrontare due espressioni per determinare se l'espressione a sinistra ha un valore maggiore o uguale a quella a destra.</span><span class="sxs-lookup"><span data-stu-id="71163-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71163-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="71163-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="71163-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="71163-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="71163-106">Qualsiasi espressione valida.</span><span class="sxs-lookup"><span data-stu-id="71163-106">Any valid expression.</span></span> <span data-ttu-id="71163-107">Entrambe le espressioni devono contenere tipi di dati convertibili in modo implicito.</span><span class="sxs-lookup"><span data-stu-id="71163-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="71163-108">Tipi di risultati</span><span class="sxs-lookup"><span data-stu-id="71163-108">Result Types</span></span>  
 <span data-ttu-id="71163-109">`true` se l'espressione a sinistra ha un valore maggiore o uguale a quella a destra; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="71163-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71163-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="71163-110">Example</span></span>  
 <span data-ttu-id="71163-111">Nella query Entity SQL seguente viene usato l'operatore di confronto >= per confrontare due espressioni e determinare se l'espressione a sinistra ha un valore maggiore o uguale a quella a destra.</span><span class="sxs-lookup"><span data-stu-id="71163-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="71163-112">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="71163-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="71163-113">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="71163-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="71163-114">Seguire la procedura descritta in [How per: Eseguire una query che restituisce i risultati di StructuralType @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="71163-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="71163-115">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="71163-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="71163-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="71163-116">See also</span></span>

- [<span data-ttu-id="71163-117">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="71163-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
