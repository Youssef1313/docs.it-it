---
title: 'Procedura: Recuperare il valore di un attributo (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: e099c20a519563eba2a060320b36761ebe54e0f1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710067"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Procedura: Recuperare il valore di un attributo (LINQ to XML) (C#)
In questo argomento viene illustrato come ottenere il valore di attributi. Per eseguire questa operazione, è possibile scegliere tra due alternative: è possibile eseguire il cast di un <xref:System.Xml.Linq.XAttribute> al tipo desiderato; l'operatore di conversione esplicito converte quindi il contenuto dell'elemento o dell'attributo al tipo specificato. In alternativa, è possibile usare la proprietà <xref:System.Xml.Linq.XAttribute.Value%2A>. L'esecuzione del cast costituisce in genere l'approccio migliore. Se si esegue il cast dell'attributo a un tipo nullable, sarà più semplice scrivere il codice quando si recupera il valore di un attributo che potrebbe o meno esistere. Per esempi di questa tecnica, vedere [Procedura: Recuperare il valore di un elemento (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Esempio  
 Per recuperare il valore di un attributo, è sufficiente eseguire il cast dell'oggetto <xref:System.Xml.Linq.XAttribute> al tipo desiderato.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Questo esempio produce il seguente output:  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come recuperare il valore di un attributo quando l'attributo è in uno spazio dei nomi. Per altre informazioni, vedere [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Questo esempio produce il seguente output:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Vedere anche

- [Assi LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
