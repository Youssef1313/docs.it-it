---
title: "Procedura: Trovare un'unione di due percorsi (XPath-LINQ to XML) (C#)"
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 9fc88a8784958294ba6077893a5d54110de335a0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593751"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Procedura: Trovare un'unione di due percorsi (XPath-LINQ to XML) (C#)
In XPath è possibile trovare l'unione dei risultati di due percorsi di posizione XPath.  
  
 L'espressione XPath è:  
  
 `//Category|//Price`  
  
 È possibile ottenere gli stessi risultati usando l'operatore di query standard <xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono trovati tutti gli elementi `Category` e tutti gli elementi `Price`, che vengono concatenati in un'unica raccolta. Si noti che la query [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] chiama <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> per ordinare i risultati. Anche i risultati della valutazione dell'espressione di XPath sono nell'ordine del documento.  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: dati numerici (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Questo esempio produce il seguente output:  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  