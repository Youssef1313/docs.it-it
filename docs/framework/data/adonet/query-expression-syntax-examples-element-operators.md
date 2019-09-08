---
title: 'Esempi di sintassi delle espressioni di query: Operatori di elemento (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: ae29ed3d61489b9da24a34e2e99ee32bd67c6d5c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783039"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="a2c34-102">Esempi di sintassi delle espressioni di query: Operatori di elemento (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="a2c34-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="a2c34-103">Negli esempi di questo argomento viene illustrato come usare i metodi <xref:System.Linq.Enumerable.First%2A> e <xref:System.Linq.Enumerable.ElementAt%2A> per ottenere elementi di <xref:System.Data.DataRow> da <xref:System.Data.DataSet> usando la sintassi delle espressioni di query.</span><span class="sxs-lookup"><span data-stu-id="a2c34-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="a2c34-104">Il `FillDataSet` metodo utilizzato in questi esempi viene specificato nel [caricamento di dati in un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="a2c34-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="a2c34-105">Negli esempi di questo argomento vengono usate le tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a2c34-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a2c34-106">Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`</span><span class="sxs-lookup"><span data-stu-id="a2c34-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="a2c34-107">Per altre informazioni, vedere [Procedura: Creare un progetto LINQ to DataSet in Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a2c34-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="a2c34-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="a2c34-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2c34-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="a2c34-109">Example</span></span>  
 <span data-ttu-id="a2c34-110">In questo esempio viene usato il metodo <xref:System.Linq.Enumerable.ElementAt%2A> per recuperare il quinto indirizzo in cui `PostalCode` == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="a2c34-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="a2c34-111">Primo</span><span class="sxs-lookup"><span data-stu-id="a2c34-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2c34-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="a2c34-112">Example</span></span>  
 <span data-ttu-id="a2c34-113">In questo esempio viene usato il metodo <xref:System.Linq.Enumerable.First%2A> per restituire il primo contatto il cui nome è 'Brooke'.</span><span class="sxs-lookup"><span data-stu-id="a2c34-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="a2c34-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a2c34-114">See also</span></span>

- [<span data-ttu-id="a2c34-115">Caricamento di dati in un oggetto DataSet</span><span class="sxs-lookup"><span data-stu-id="a2c34-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="a2c34-116">Esempi di LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a2c34-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="a2c34-117">Panoramica degli operatori di query standard (C#)</span><span class="sxs-lookup"><span data-stu-id="a2c34-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a2c34-118">Panoramica degli operatori query standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2c34-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
