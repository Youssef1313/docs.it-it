---
title: 'Esempi di sintassi delle query basate su metodo: Conversione'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: a78588cb4bd09f8a8a8ce8ed4a60dd45fce1d386
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397488"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="dc6de-102">Esempi di sintassi delle query basate su metodo: Conversione</span><span class="sxs-lookup"><span data-stu-id="dc6de-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="dc6de-103">Negli esempi di questo argomento viene illustrato come usare i <xref:System.Linq.Enumerable.ToArray%2A>metodi <xref:System.Linq.Enumerable.ToDictionary%2A> , <xref:System.Linq.Enumerable.ToList%2A> e per eseguire query sul [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando la sintassi delle query basate su metodo.</span><span class="sxs-lookup"><span data-stu-id="dc6de-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="dc6de-104">Il modello Sales di AdventureWorks usato in questi esempi è compilato in base alle tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dc6de-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dc6de-105">Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`</span><span class="sxs-lookup"><span data-stu-id="dc6de-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="dc6de-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="dc6de-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="dc6de-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="dc6de-107">Example</span></span>  
 <span data-ttu-id="dc6de-108">Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToArray%2A> per restituire immediatamente una matrice da una sequenza.</span><span class="sxs-lookup"><span data-stu-id="dc6de-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="dc6de-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="dc6de-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="dc6de-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="dc6de-110">Example</span></span>  
 <span data-ttu-id="dc6de-111">Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToDictionary%2A> per restituire immediatamente un dizionario da una sequenza e un'espressione chiave correlata.</span><span class="sxs-lookup"><span data-stu-id="dc6de-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="dc6de-112">ToList</span><span class="sxs-lookup"><span data-stu-id="dc6de-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="dc6de-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="dc6de-113">Example</span></span>  
 <span data-ttu-id="dc6de-114">Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToList%2A> per restituire immediatamente un oggetto <xref:System.Collections.Generic.List%601>, dove `T` è di tipo <xref:System.Data.DataRow>, da una sequenza.</span><span class="sxs-lookup"><span data-stu-id="dc6de-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="dc6de-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dc6de-115">See also</span></span>

- [<span data-ttu-id="dc6de-116">Query in LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="dc6de-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
