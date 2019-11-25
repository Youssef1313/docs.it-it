---
title: Proprietà dell'indicizzatore di estensione
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352691"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="ceb90-102">Proprietà dell'indicizzatore di estensione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceb90-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="ceb90-103">Fornisce l'accesso ai singoli elementi di una raccolta.</span><span class="sxs-lookup"><span data-stu-id="ceb90-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb90-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ceb90-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="ceb90-105">Parti</span><span class="sxs-lookup"><span data-stu-id="ceb90-105">Parts</span></span>  
  
|<span data-ttu-id="ceb90-106">Termine</span><span class="sxs-lookup"><span data-stu-id="ceb90-106">Term</span></span>|<span data-ttu-id="ceb90-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="ceb90-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="ceb90-108">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ceb90-108">Required.</span></span> <span data-ttu-id="ceb90-109">A queryable collection.</span><span class="sxs-lookup"><span data-stu-id="ceb90-109">A queryable collection.</span></span> <span data-ttu-id="ceb90-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="ceb90-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="ceb90-111">(</span><span class="sxs-lookup"><span data-stu-id="ceb90-111">(</span></span>|<span data-ttu-id="ceb90-112">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ceb90-112">Required.</span></span> <span data-ttu-id="ceb90-113">Denotes the start of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="ceb90-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="ceb90-114">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ceb90-114">Required.</span></span> <span data-ttu-id="ceb90-115">An integer expression that specifies the zero-based position of an element of the collection.</span><span class="sxs-lookup"><span data-stu-id="ceb90-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="ceb90-116">)</span><span class="sxs-lookup"><span data-stu-id="ceb90-116">)</span></span>|<span data-ttu-id="ceb90-117">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ceb90-117">Required.</span></span> <span data-ttu-id="ceb90-118">Denotes the end of the indexer property.</span><span class="sxs-lookup"><span data-stu-id="ceb90-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ceb90-119">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ceb90-119">Return Value</span></span>  
 <span data-ttu-id="ceb90-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="ceb90-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceb90-121">Note</span><span class="sxs-lookup"><span data-stu-id="ceb90-121">Remarks</span></span>  
 <span data-ttu-id="ceb90-122">You can use the extension indexer property to access individual elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="ceb90-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="ceb90-123">This indexer property is typically used on the output of XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="ceb90-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="ceb90-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span><span class="sxs-lookup"><span data-stu-id="ceb90-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="ceb90-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span><span class="sxs-lookup"><span data-stu-id="ceb90-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="ceb90-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span><span class="sxs-lookup"><span data-stu-id="ceb90-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="ceb90-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="ceb90-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="ceb90-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span><span class="sxs-lookup"><span data-stu-id="ceb90-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="ceb90-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span><span class="sxs-lookup"><span data-stu-id="ceb90-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="ceb90-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="ceb90-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceb90-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="ceb90-131">Example</span></span>  
 <span data-ttu-id="ceb90-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="ceb90-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ceb90-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="ceb90-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="ceb90-134">Questo codice visualizza il testo seguente:</span><span class="sxs-lookup"><span data-stu-id="ceb90-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="ceb90-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ceb90-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="ceb90-136">Proprietà Axis XML</span><span class="sxs-lookup"><span data-stu-id="ceb90-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="ceb90-137">Valori letterali XML</span><span class="sxs-lookup"><span data-stu-id="ceb90-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="ceb90-138">Creazione di XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ceb90-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ceb90-139">Proprietà Value XML</span><span class="sxs-lookup"><span data-stu-id="ceb90-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
