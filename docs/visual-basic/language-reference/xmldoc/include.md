---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348452"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)
Refers to another file that describes the types and members in your source code.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametri  
 `filename`  
 Obbligatorio. Nome del file che contiene la documentazione. È possibile qualificare il nome del file con un percorso. Enclose `filename` in double quotation marks (" ").  
  
 `tagpath`  
 Obbligatorio. Percorso dei tag di `filename` che porta al `name` del tag. Enclose the path in double quotation marks (" ").  
  
 `name`  
 Obbligatorio. The name specifier in the tag that precedes the comments. `Name` will have an `id`.  
  
 `id`  
 Obbligatorio. ID del tag che precede i commenti. Enclose the ID in single quotation marks (' ').  
  
## <a name="remarks"></a>Note  
 Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code. eliminando la necessità di inserire i commenti relativi alla documentazione direttamente nel file del codice sorgente.  
  
 The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation. For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Esempio  
 This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 The format of the `commentFile.xml` is as follows.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Tag di commento XML](../../../visual-basic/language-reference/xmldoc/index.md)
