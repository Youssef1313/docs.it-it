---
title: 'Procedura: Trovare un elemento con un attributo specifico (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
ms.openlocfilehash: 615dc9bb4ee9b90c0e7b9ecb86d9342bc688f3b1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710281"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a>Procedura: Trovare un elemento con un attributo specifico (Visual Basic)
In questo argomento viene illustrato come trovare un elemento che include un attributo con un valore specifico.  
  
## <a name="example"></a>Esempio  
 Nell'esempio viene illustrato come trovare l'elemento `Address` contenente un attributo `Type` con valore "Billing".  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: tipico ordine di acquisto (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 L'output del codice è il seguente:  
  
```xml  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 Si noti che in questo esempio vengono utilizzate la proprietà [Axis Child XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), la [Proprietà Axis attribute XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)e la [proprietà Value XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi. Per ulteriori informazioni, vedere [Cenni preliminari sugli spazi dei nomi (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: tipico ordine di acquisto in uno spazio dei nomi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 L'output del codice è il seguente:  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Query di base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Panoramica degli operatori query standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Operazioni di proiezione (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
