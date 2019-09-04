---
title: '* Moltiplicare (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 19fb73d327f91303de938a5f49866339413b9698
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250057"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="abf09-102">\* (moltiplicazione) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="abf09-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="abf09-103">Moltiplica due espressioni.</span><span class="sxs-lookup"><span data-stu-id="abf09-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf09-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="abf09-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="abf09-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="abf09-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="abf09-106">Qualsiasi espressione valida con qualsiasi tipo di dati numerici.</span><span class="sxs-lookup"><span data-stu-id="abf09-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="abf09-107">Tipi di risultati</span><span class="sxs-lookup"><span data-stu-id="abf09-107">Result Types</span></span>  
 <span data-ttu-id="abf09-108">Tipo di dati ottenuto della promozione implicita del tipo dei due argomenti.</span><span class="sxs-lookup"><span data-stu-id="abf09-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="abf09-109">Per ulteriori informazioni sull'innalzamento di tipo implicito, vedere [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="abf09-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf09-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="abf09-110">Example</span></span>  
 <span data-ttu-id="abf09-111">Nella query Entity SQL seguente viene usato l'operatore aritmetico \* per moltiplicare due numeri.</span><span class="sxs-lookup"><span data-stu-id="abf09-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="abf09-112">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="abf09-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="abf09-113">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="abf09-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="abf09-114">Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.</span><span class="sxs-lookup"><span data-stu-id="abf09-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="abf09-115">Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="abf09-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="abf09-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="abf09-116">See also</span></span>

- [<span data-ttu-id="abf09-117">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="abf09-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
