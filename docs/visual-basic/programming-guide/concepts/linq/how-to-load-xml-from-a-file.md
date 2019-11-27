---
title: 'Procedura: caricare XML da un file'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: 72a5adb8c7165f8113584f27bea64efde4ec58fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336102"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a>Procedura: caricare XML da un file (Visual Basic)

In questo argomento viene illustrato come caricare XML da un URI tramite il metodo <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come caricare un documento XML da un file. Viene caricato il file books.xml e viene restituito l'albero XML alla console.

Nell'esempio viene usato il documento XML seguente: [File XML di esempio: libri (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
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

## <a name="see-also"></a>Vedere anche

- [Analisi di XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
