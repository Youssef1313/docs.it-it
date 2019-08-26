---
title: Set di nodi nelle trasformazioni
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a84234ee797dac7487492dc92af2de4fa7ef503
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962542"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="8c85b-102">Set di nodi nelle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="8c85b-102">Node Sets in Transformations</span></span>
<span data-ttu-id="8c85b-103">I set di nodi sono uno dei quattro tipi di dati principali restituiti dalle espressioni XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="8c85b-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="8c85b-104">Un set di nodi, ovvero una raccolta di nodi non ordinati senza duplicati e creati in base all'ordine con cui sono riportati del documento, può essere assegnato a una variabile in un foglio di stile.</span><span class="sxs-lookup"><span data-stu-id="8c85b-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c85b-105">La classe <xref:System.Xml.Xsl.XslTransform> è obsoleta in .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8c85b-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="8c85b-106">È possibile eseguire le trasformazioni XSLT (Extensible Stylesheet Language for Transformations) usando la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="8c85b-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8c85b-107">Per altre informazioni, vedere [Utilizzo della classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrazione dalla classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="8c85b-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="8c85b-108">I set di nodi sono uno dei quattro tipi di dati principali restituiti dalle espressioni XPath.</span><span class="sxs-lookup"><span data-stu-id="8c85b-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="8c85b-109">Un set di nodi, ovvero una raccolta di nodi non ordinati senza duplicati e creati in base all'ordine con cui sono riportati del documento, può essere assegnato a una variabile in un foglio di stile.</span><span class="sxs-lookup"><span data-stu-id="8c85b-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="8c85b-110">Il set di nodi risultante da un'espressione XPath usata in un attributo `select` per una trasformazione ha lo stesso comportamento di un set di nodi proveniente dal DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="8c85b-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="8c85b-111">È possibile spostarsi all'interno di un set di nodi usando i metodi illustrati in [Navigazione del set di nodi con XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), diversamente da un frammento di albero risultato che usa <xref:System.Xml.XPath.XPathNodeIterator> per la navigazione.</span><span class="sxs-lookup"><span data-stu-id="8c85b-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="8c85b-112">Nell'esempio di codice seguente viene illustrato come scorrere un set di nodi quando un elemento `variable` o `parameter` di un foglio di stile viene valutato come set di nodi.</span><span class="sxs-lookup"><span data-stu-id="8c85b-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="8c85b-113">Foglio di stile</span><span class="sxs-lookup"><span data-stu-id="8c85b-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="8c85b-114">Input</span><span class="sxs-lookup"><span data-stu-id="8c85b-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="8c85b-115">Output</span><span class="sxs-lookup"><span data-stu-id="8c85b-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c85b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8c85b-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="8c85b-117">Trasformazioni XSLT con la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="8c85b-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="8c85b-118">Implementazione del processore XSLT da parte della classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="8c85b-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
