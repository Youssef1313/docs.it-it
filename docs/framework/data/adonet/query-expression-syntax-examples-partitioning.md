---
title: 'Esempi di sintassi delle espressioni di query: Partizionamento (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 6a00c5d49acc02c476895c999687aa944ba26aff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795094"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="9ed48-102">Esempi di sintassi delle espressioni di query: Partizionamento (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9ed48-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="9ed48-103">Negli esempi di questo argomento viene illustrato l'uso dei metodi <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Take%2A> per eseguire una query su <xref:System.Data.DataSet> usando la sintassi delle espressioni di query.</span><span class="sxs-lookup"><span data-stu-id="9ed48-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="9ed48-104">Il `FillDataSet` metodo utilizzato in questi esempi viene specificato nel [caricamento di dati in un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9ed48-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9ed48-105">Negli esempi di questo argomento vengono usate le tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9ed48-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9ed48-106">Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`</span><span class="sxs-lookup"><span data-stu-id="9ed48-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9ed48-107">Per altre informazioni, vedere [Procedura: Creare un progetto LINQ to DataSet in Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9ed48-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="9ed48-108">Skip</span><span class="sxs-lookup"><span data-stu-id="9ed48-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ed48-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="9ed48-109">Example</span></span>  
 <span data-ttu-id="9ed48-110">In questo esempio viene usato il metodo <xref:System.Linq.Enumerable.Skip%2A> per ottenere tutti gli indirizzi di Seattle ad eccezione dei primi due.</span><span class="sxs-lookup"><span data-stu-id="9ed48-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="9ed48-111">Take</span><span class="sxs-lookup"><span data-stu-id="9ed48-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ed48-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="9ed48-112">Example</span></span>  
 <span data-ttu-id="9ed48-113">In questo esempio viene usato il metodo <xref:System.Linq.Enumerable.Take%2A> per ottenere i primi tre indirizzi di Seattle.</span><span class="sxs-lookup"><span data-stu-id="9ed48-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="9ed48-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9ed48-114">See also</span></span>

- [<span data-ttu-id="9ed48-115">Caricamento di dati in un oggetto DataSet</span><span class="sxs-lookup"><span data-stu-id="9ed48-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="9ed48-116">Esempi di LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9ed48-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="9ed48-117">Panoramica degli operatori di query standard (C#)</span><span class="sxs-lookup"><span data-stu-id="9ed48-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9ed48-118">Panoramica degli operatori query standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ed48-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
