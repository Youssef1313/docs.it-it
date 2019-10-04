---
title: 'Procedura: Elementi di ordinamento (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: 1bd76ade02f8f891e98b048ac866b6b9de65062f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835102"
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="fe1dd-102">Procedura: Elementi di ordinamento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe1dd-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="fe1dd-103">In questo esempio viene illustrato come scrivere una query che ordina i relativi risultati.</span><span class="sxs-lookup"><span data-stu-id="fe1dd-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe1dd-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="fe1dd-104">Example</span></span>  
 <span data-ttu-id="fe1dd-105">Nell'esempio viene utilizzato il seguente documento XML:  [File XML di esempio: dati numerici (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fe1dd-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="fe1dd-106">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="fe1dd-106">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="fe1dd-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="fe1dd-107">Example</span></span>  
 <span data-ttu-id="fe1dd-108">Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="fe1dd-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="fe1dd-109">Per ulteriori informazioni, vedere [Cenni preliminari sugli spazi dei nomi (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fe1dd-109">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fe1dd-110">Nell'esempio viene utilizzato il seguente documento XML:  [File XML di esempio: dati numerici in uno spazio dei nomi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="fe1dd-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fe1dd-111">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="fe1dd-111">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe1dd-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fe1dd-112">See also</span></span>

- [<span data-ttu-id="fe1dd-113">Ordinamento dei dati</span><span class="sxs-lookup"><span data-stu-id="fe1dd-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="fe1dd-114">Query di base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe1dd-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
