---
title: Valore letterale di documento XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: db77cccd26c87e271d6db45ce514ab6dabbc53e3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349378"
---
# <a name="xml-document-literal-visual-basic"></a>Valore letterale di documento XML (Visual Basic)
A literal representing an <xref:System.Xml.Linq.XDocument> object.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Parti  
  
|Termine|Definizione|  
|---|---|  
|`encoding`|Parametro facoltativo. Literal text declaring which encoding the document uses.|  
|`standalone`|Parametro facoltativo. Literal text. Must be "yes" or "no".|  
|`piCommentList`|Parametro facoltativo. List of XML processing instructions and XML comments. Takes the following format:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Each `piComment` can be one of the following:<br /><br /> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Obbligatorio. Root element of the document. The format is one of the following:<br /><br /> <ul><li>[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Embedded expression of the form `<%=` `elementExp` `%>`. The `elementExp` returns one of the following:<br /><br /> <ul><li>Oggetto <xref:System.Xml.Linq.XElement>.</li><li>A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</li></ul></li></ul><br /> For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Note  
 An XML document literal is identified by the XML declaration at the start of the literal. Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.  
  
 An XML document literal cannot appear in an XML element.  
  
> [!NOTE]
> An XML literal can span multiple lines without using line continuation characters. This enables you to copy content from an XML document and paste it directly into a Visual Basic program.  
  
 The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.  
  
## <a name="example"></a>Esempio  
 The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Valore letterale istruzione di elaborazione XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [Valore letterale di commento XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Valore letterale elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Valori letterali XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Creazione di XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Espressioni incorporate in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
