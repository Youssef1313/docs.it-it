---
title: 'Procedura: Scrivere query in XML negli spazi dei nomi (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 1ded47ced44bebfda92b96f4dc908f1c1b2bbf6b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253184"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Procedura: Scrivere query in XML negli spazi dei nomi (C#)
Per scrivere una query su XML inclusa in uno spazio dei nomi, è necessario usare oggetti <xref:System.Xml.Linq.XName> con lo spazio dei nomi corretto.  
  
 Per C#, l'approccio più comune consiste nell'inizializzare un oggetto <xref:System.Xml.Linq.XNamespace> usando una stringa contenente l'URI, quindi usare l'overload dell'operatore di addizione per combinare lo spazio dei nomi con il nome locale.  
  
 Nel primo set di esempi in questo argomento è illustrato come creare un albero XML in uno spazio dei nomi predefinito. Nel secondo set viene illustrato come creare un albero XML in uno spazio dei nomi con un prefisso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un albero XML incluso in uno spazio dei nomi predefinito. Viene quindi recuperata una raccolta di elementi.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Questo esempio produce il seguente output:  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Esempio  
 In C# le query vengono scritte in modo identico a prescindere che vengano scritte in un albero XML che usa uno spazio dei nomi con un prefisso o in un albero XML con uno spazio dei nomi predefinito.  
  
 Nell'esempio seguente viene creato un albero XML incluso in uno spazio dei nomi con un prefisso. Viene quindi recuperata una raccolta di elementi.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Questo esempio produce il seguente output:  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md)
