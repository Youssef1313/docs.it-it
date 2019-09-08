---
title: Trovare il valore minimo in una sequenza numerica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793838"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="793b6-102">Trovare il valore minimo in una sequenza numerica</span><span class="sxs-lookup"><span data-stu-id="793b6-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="793b6-103">Usare l'operatore <xref:System.Linq.Enumerable.Min%2A> affinché venga restituito il valore minimo da una sequenza di valori numerici.</span><span class="sxs-lookup"><span data-stu-id="793b6-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="793b6-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="793b6-104">Example</span></span>  
 <span data-ttu-id="793b6-105">Nell'esempio seguente viene cercato il prezzo unitario più basso di qualsiasi prodotto.</span><span class="sxs-lookup"><span data-stu-id="793b6-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="793b6-106">Se si esegue questa query sul database di esempio Northwind, l'output sarà: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="793b6-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="793b6-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="793b6-107">Example</span></span>  
 <span data-ttu-id="793b6-108">Nell'esempio seguente viene cercato il costo di trasporto più basso per qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="793b6-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="793b6-109">Se si esegue questa query sul database di esempio Northwind, l'output sarà: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="793b6-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="793b6-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="793b6-110">Example</span></span>  
 <span data-ttu-id="793b6-111">Nell'esempio seguente viene usato Min per cercare in `Products` gli elementi con il prezzo unitario più basso di ogni categoria.</span><span class="sxs-lookup"><span data-stu-id="793b6-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="793b6-112">L'output viene disposto per categoria.</span><span class="sxs-lookup"><span data-stu-id="793b6-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="793b6-113">Se si esegue la query precedente sul database di esempio Northwind, i risultati saranno simili ai seguenti:</span><span class="sxs-lookup"><span data-stu-id="793b6-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="793b6-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="793b6-114">See also</span></span>

- [<span data-ttu-id="793b6-115">Query di aggregazione</span><span class="sxs-lookup"><span data-stu-id="793b6-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="793b6-116">Download di database di esempio</span><span class="sxs-lookup"><span data-stu-id="793b6-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
