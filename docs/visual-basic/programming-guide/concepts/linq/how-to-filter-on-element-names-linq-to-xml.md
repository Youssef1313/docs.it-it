---
title: 'Procedura: Filtra per nomi di elementi (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: f64f80b1544e8c5f2d55a44dafe01fee8758d611
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709722"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a>Procedura: Filtra per nomi di elementi (LINQ to XML) (Visual Basic)
Quando si chiama uno dei metodi che restituisce l'oggetto <xref:System.Collections.Generic.IEnumerable%601> di <xref:System.Xml.Linq.XElement>, è possibile filtrare in base al nome dell'elemento.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene recuperata una raccolta di discendenti filtrata in maniera tale da includere solo i discendenti con il nome specificato.  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: tipico ordine di acquisto (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 L'output del codice è il seguente:  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Gli altri metodi che restituiscono l'oggetto <xref:System.Collections.Generic.IEnumerable%601> delle raccolte <xref:System.Xml.Linq.XElement> sono caratterizzati dallo stesso schema. Le relative firme sono simili a <xref:System.Xml.Linq.XContainer.Elements%2A> e <xref:System.Xml.Linq.XContainer.Descendants%2A>. Di seguito è riportato l'elenco completo dei metodi con firme simili:  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi. Per ulteriori informazioni, vedere [Cenni preliminari sugli spazi dei nomi (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: tipico ordine di acquisto in uno spazio dei nomi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 L'output del codice è il seguente:  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Vedere anche

- [Assi LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
