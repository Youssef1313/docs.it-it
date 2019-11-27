---
title: Serializzazione con una dichiarazione XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350625"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="21239-102">Serializzazione con una dichiarazione XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21239-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="21239-103">In questo argomento viene descritto come controllare se la serializzazione genera una dichiarazione XML.</span><span class="sxs-lookup"><span data-stu-id="21239-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="21239-104">Generazione della dichiarazione XML</span><span class="sxs-lookup"><span data-stu-id="21239-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="21239-105">La serializzazione di <xref:System.IO.File> o <xref:System.IO.TextWriter> tramite il metodo <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> o il metodo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> genera una dichiarazione XML.</span><span class="sxs-lookup"><span data-stu-id="21239-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="21239-106">Quando si serializza in <xref:System.Xml.XmlWriter>, le impostazioni del writer (specificate in un oggetto <xref:System.Xml.XmlWriterSettings>) determinano se una dichiarazione XML viene generata o meno.</span><span class="sxs-lookup"><span data-stu-id="21239-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="21239-107">Se si serializza in una stringa tramite il metodo `ToString`, l'XML risultante non includerà una dichiarazione XML.</span><span class="sxs-lookup"><span data-stu-id="21239-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="21239-108">Serializzazione con una dichiarazione XML</span><span class="sxs-lookup"><span data-stu-id="21239-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="21239-109">Nell'esempio seguente viene creato un oggetto <xref:System.Xml.Linq.XElement>, viene salvato il documento in un file e quindi stampato il file nella console.</span><span class="sxs-lookup"><span data-stu-id="21239-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="21239-110">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="21239-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="21239-111">Serializzazione senza una dichiarazione XML</span><span class="sxs-lookup"><span data-stu-id="21239-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="21239-112">Nell'esempio seguente viene illustrato come salvare <xref:System.Xml.Linq.XElement> in <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="21239-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="21239-113">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="21239-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21239-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21239-114">See also</span></span>

- [<span data-ttu-id="21239-115">Serializzazione di strutture ad albero XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21239-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
