---
title: 'Procedura: Caricare XML da un file (C#)'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: d3e7cdbb0691fafcfcfc684f4495f4785b4ea3e7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593171"
---
# <a name="how-to-load-xml-from-a-file-c"></a>Procedura: Caricare XML da un file (C#)
In questo argomento viene illustrato come caricare XML da un URI tramite il metodo <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come caricare un documento XML da un file. Viene caricato il file books.xml e viene restituito l'albero XML alla console.  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: libri (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 L'output del codice è il seguente:  
  
```xml  
<Catalog>  
  <Book id="bk101">  
    <Author>Garghentini, Davide</Author>  
    <Title>XML Developer's Guide</Title>  
    <Genre>Computer</Genre>  
    <Price>44.95</Price>  
    <PublishDate>2000-10-01</PublishDate>  
    <Description>An in-depth look at creating applications   
      with XML.</Description>  
  </Book>  
  <Book id="bk102">  
    <Author>Garcia, Debra</Author>  
    <Title>Midnight Rain</Title>  
    <Genre>Fantasy</Genre>  
    <Price>5.95</Price>  
    <PublishDate>2000-12-16</PublishDate>  
    <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
  </Book>  
</Catalog>  
```  
  