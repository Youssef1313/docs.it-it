---
title: 'Procedura: intercettare gli errori di analisi'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353349"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="346a6-102">Procedura: intercettare gli errori di analisi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="346a6-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="346a6-103">In questo argomento viene illustrato come rilevare XML non corretto o non valido.</span><span class="sxs-lookup"><span data-stu-id="346a6-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="346a6-104">viene implementato usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="346a6-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="346a6-105">Se a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] viene passato XML non corretto o non valido, la classe <xref:System.Xml.XmlReader> sottostante genererà un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="346a6-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="346a6-106">I vari metodi che analizzano il codice XML, ad esempio <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, non intercettano l'eccezione, che può quindi essere intercettata dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="346a6-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="346a6-107">Si noti che non è possibile ottenere errori di analisi se si usano valori letterali XML.</span><span class="sxs-lookup"><span data-stu-id="346a6-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="346a6-108">Il compilatore Visual Basic intercetterà errori di XML non corretto o non valido.</span><span class="sxs-lookup"><span data-stu-id="346a6-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="346a6-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="346a6-109">Example</span></span>  
 <span data-ttu-id="346a6-110">Nel codice seguente si tenta di analizzare XML non valido:</span><span class="sxs-lookup"><span data-stu-id="346a6-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="346a6-111">Quando viene eseguito, questo codice genera la seguente eccezione:</span><span class="sxs-lookup"><span data-stu-id="346a6-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="346a6-112">Per informazioni sulle eccezioni che si può prevedere vengano generate dai metodi <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> e <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, vedere la documentazione relativa a <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="346a6-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346a6-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="346a6-113">See also</span></span>

- [<span data-ttu-id="346a6-114">Analisi di XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="346a6-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
