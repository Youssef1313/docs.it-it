---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039899"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="ca8c1-102">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ca8c1-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="ca8c1-103">La parola chiave COLLECTION viene usata solo nella definizione di una funzione inline.</span><span class="sxs-lookup"><span data-stu-id="ca8c1-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="ca8c1-104">Le funzioni di raccolta sono funzioni che operano su una raccolta di valori e producono un output scalare.</span><span class="sxs-lookup"><span data-stu-id="ca8c1-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca8c1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ca8c1-105">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="ca8c1-106">argomenti</span><span class="sxs-lookup"><span data-stu-id="ca8c1-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="ca8c1-107">Espressione che restituisce una raccolta di tipi supportati, righe o riferimenti.</span><span class="sxs-lookup"><span data-stu-id="ca8c1-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca8c1-108">Note</span><span class="sxs-lookup"><span data-stu-id="ca8c1-108">Remarks</span></span>  
 <span data-ttu-id="ca8c1-109">Per altre informazioni sulla parola chiave COLLECTION, vedere [Type Definitions](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ca8c1-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca8c1-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="ca8c1-110">Example</span></span>  
 <span data-ttu-id="ca8c1-111">Nell'esempio seguente viene mostrato come usare la parola chiave COLLECTION per dichiarare una raccolta di numeri decimali come argomento di una funzione inline della query.</span><span class="sxs-lookup"><span data-stu-id="ca8c1-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="ca8c1-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca8c1-112">See also</span></span>

- [<span data-ttu-id="ca8c1-113">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ca8c1-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
