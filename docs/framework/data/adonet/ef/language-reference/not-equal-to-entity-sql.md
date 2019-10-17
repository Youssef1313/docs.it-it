---
title: '!= (diverso da) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3f6f66d38eb9650e1adb06fa3ef5edbccf110374
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319505"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="9a022-102">!= (diverso da) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a022-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="9a022-103">Consente di confrontare due espressioni per determinare se l'espressione a sinistra è diversa da quella a destra.</span><span class="sxs-lookup"><span data-stu-id="9a022-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="9a022-104">L'operatore !=(diverso da) equivale dal punto di vista funzionale all'operatore <>.</span><span class="sxs-lookup"><span data-stu-id="9a022-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a022-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a022-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a022-106">argomenti</span><span class="sxs-lookup"><span data-stu-id="9a022-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9a022-107">Qualsiasi espressione valida.</span><span class="sxs-lookup"><span data-stu-id="9a022-107">Any valid expression.</span></span> <span data-ttu-id="9a022-108">Entrambe le espressioni devono contenere tipi di dati convertibili in modo implicito.</span><span class="sxs-lookup"><span data-stu-id="9a022-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a022-109">Tipi di risultati</span><span class="sxs-lookup"><span data-stu-id="9a022-109">Result Types</span></span>  
 <span data-ttu-id="9a022-110">`true` se l'espressione a sinistra è diversa da quella a destra; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="9a022-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a022-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="9a022-111">Example</span></span>  
 <span data-ttu-id="9a022-112">Nella query Entity SQL seguente viene usato l'operatore != per confrontare due espressioni e determinare se l'espressione a sinistra è diversa da quella a destra.</span><span class="sxs-lookup"><span data-stu-id="9a022-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="9a022-113">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a022-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a022-114">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a022-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9a022-115">Seguire la procedura indicata in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9a022-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9a022-116">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9a022-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="9a022-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a022-117">See also</span></span>

- [<span data-ttu-id="9a022-118">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9a022-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
