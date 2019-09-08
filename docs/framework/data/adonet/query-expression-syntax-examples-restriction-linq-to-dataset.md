---
title: 'Esempi di sintassi delle espressioni di query: Restrizione (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 04a7b2027ac956d14086f94527b10d253749949d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794674"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="8fd18-102">Esempi di sintassi delle espressioni di query: Restrizione (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8fd18-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="8fd18-103">Negli esempi di questo argomento viene illustrato l'uso del metodo <xref:System.Linq.Enumerable.Where%2A> per eseguire una query su <xref:System.Data.DataSet> usando la sintassi delle espressioni di query.</span><span class="sxs-lookup"><span data-stu-id="8fd18-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="8fd18-104">Il `FillDataSet` metodo utilizzato in questi esempi viene specificato nel [caricamento di dati in un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8fd18-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8fd18-105">Negli esempi di questo argomento vengono usate le tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8fd18-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8fd18-106">Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`</span><span class="sxs-lookup"><span data-stu-id="8fd18-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]        
  
 <span data-ttu-id="8fd18-107">Per altre informazioni, vedere [Procedura: Creare un progetto LINQ to DataSet in Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8fd18-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="8fd18-108">Where</span><span class="sxs-lookup"><span data-stu-id="8fd18-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fd18-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="8fd18-109">Example</span></span>  
 <span data-ttu-id="8fd18-110">In questo esempio vengono restituiti tutti gli ordini online.</span><span class="sxs-lookup"><span data-stu-id="8fd18-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]     
  
### <a name="example"></a><span data-ttu-id="8fd18-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="8fd18-111">Example</span></span>  
 <span data-ttu-id="8fd18-112">In questo esempio vengono restituiti gli ordini in cui la quantità ordinata è maggiore di 2 e minore di 6.</span><span class="sxs-lookup"><span data-stu-id="8fd18-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]     
  
### <a name="example"></a><span data-ttu-id="8fd18-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="8fd18-113">Example</span></span>  
 <span data-ttu-id="8fd18-114">In questo esempio vengono restituiti tutti i prodotti di colore rosso.</span><span class="sxs-lookup"><span data-stu-id="8fd18-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]     
  
### <a name="example"></a><span data-ttu-id="8fd18-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="8fd18-115">Example</span></span>  
 <span data-ttu-id="8fd18-116">In questo esempio viene usato il metodo <xref:System.Linq.Enumerable.Where%2A> per individuare gli ordini effettuati dopo il 1 dicembre 2002, quindi viene usato il metodo <xref:System.Data.DataRow.GetChildRows%2A> per ottenere i dettagli relativi a ogni ordine.</span><span class="sxs-lookup"><span data-stu-id="8fd18-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]       
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="8fd18-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8fd18-117">See also</span></span>

- [<span data-ttu-id="8fd18-118">Caricamento di dati in un oggetto DataSet</span><span class="sxs-lookup"><span data-stu-id="8fd18-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="8fd18-119">Esempi di LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8fd18-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8fd18-120">Panoramica degli operatori di query standard (C#)</span><span class="sxs-lookup"><span data-stu-id="8fd18-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8fd18-121">Panoramica degli operatori query standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fd18-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
