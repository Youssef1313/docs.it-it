---
title: Ambito degli spazi dei nomi predefiniti in C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 0c5f5cccda6ba6a75a8631ed095921b90b02916b
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868867"
---
# <a name="scope-of-default-namespaces-in-c"></a>Ambito degli spazi dei nomi predefiniti in C\#
Gli spazi dei nomi rappresentati nell'albero XML non sono inclusi nell'ambito delle query. Se il codice XML è incluso in uno spazio dei nomi predefinito, è comunque necessario dichiarare una variabile <xref:System.Xml.Linq.XNamespace> e combinarla con il nome locale per creare un nome completo da usare nella query.  
  
 Uno dei problemi più comuni che viene riscontrato durante l'esecuzione di query su alberi XML è che, se l'albero XML include uno spazio dei nomi predefinito, lo sviluppatore scrive talvolta la query come se il codice XML non fosse incluso in uno spazio dei nomi.  
  
 Nel primo set di esempi riportati in questo argomento viene illustrato il tipico caricamento del codice XML in uno spazio dei nomi predefinito e l'esecuzione errata di query su tale codice.  
  
 Nel secondo set di esempi sono illustrate le correzioni necessarie da effettuare per poter eseguire query su codice XML in uno spazio dei nomi.  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono illustrate la creazione di codice XML in uno spazio dei nomi e una query che restituisce un set di risultati vuoto.  
  
### <a name="code"></a>Codice  
  
```csharp  
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
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Commenti  
 Il risultato ottenuto dall'esempio è il seguente:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono illustrate la creazione di codice XML in uno spazio dei nomi e una query codificata correttamente.  
  
 Contrariamente all'esempio di codice errato precedente, l'approccio corretto in C# consiste nel dichiarare e inizializzare un oggetto <xref:System.Xml.Linq.XNamespace> e usarlo se si specificano oggetti <xref:System.Xml.Linq.XName>. In questo caso l'argomento del metodo <xref:System.Xml.Linq.XContainer.Elements%2A> è un oggetto <xref:System.Xml.Linq.XName>.  
  
### <a name="code"></a>Codice  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>Commenti  
 Il risultato ottenuto dall'esempio è il seguente:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md)
