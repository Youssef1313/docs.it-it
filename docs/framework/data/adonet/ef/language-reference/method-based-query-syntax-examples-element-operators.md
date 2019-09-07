---
title: 'Esempi di sintassi delle query basate su metodo: Operatori di elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 7add62a2792a0fc82346851b7dd835aad5082742
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397453"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="3cf3d-102">Esempi di sintassi delle query basate su metodo: Operatori di elemento</span><span class="sxs-lookup"><span data-stu-id="3cf3d-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="3cf3d-103">Negli esempi di questo argomento viene illustrato come utilizzare il <xref:System.Linq.Enumerable.First%2A> metodo per eseguire query sul [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) utilizzando la sintassi delle query basate su metodo.</span><span class="sxs-lookup"><span data-stu-id="3cf3d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="3cf3d-104">Il modello Sales di AdventureWorks usato in questi esempi è compilato in base alle tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3cf3d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3cf3d-105">Nell'esempio riportato in questo argomento vengono utilizzate `using` le istruzioni seguenti / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="3cf3d-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="3cf3d-106">Primo</span><span class="sxs-lookup"><span data-stu-id="3cf3d-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cf3d-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="3cf3d-107">Example</span></span>  
 <span data-ttu-id="3cf3d-108">Nell'esempio seguente viene usato <xref:System.Linq.Enumerable.First%2A> il metodo per trovare il primo indirizzo di posta elettronica che inizia con "Caroline".</span><span class="sxs-lookup"><span data-stu-id="3cf3d-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="3cf3d-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3cf3d-109">See also</span></span>

- [<span data-ttu-id="3cf3d-110">Query in LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3cf3d-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
