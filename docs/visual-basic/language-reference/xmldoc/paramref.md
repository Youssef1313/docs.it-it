---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 85171bd8deeb5f54c4560bb8b2339107bb8d8c68
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524716"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="24eeb-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24eeb-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="24eeb-103">Formatta una parola come parametro.</span><span class="sxs-lookup"><span data-stu-id="24eeb-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24eeb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24eeb-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="24eeb-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="24eeb-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="24eeb-106">Nome del parametro a cui fare riferimento.</span><span class="sxs-lookup"><span data-stu-id="24eeb-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="24eeb-107">Racchiudere il nome tra virgolette doppie (" ").</span><span class="sxs-lookup"><span data-stu-id="24eeb-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24eeb-108">Note</span><span class="sxs-lookup"><span data-stu-id="24eeb-108">Remarks</span></span>  
 <span data-ttu-id="24eeb-109">Il tag `<paramref>` fornisce un modo per indicare che una parola è un parametro.</span><span class="sxs-lookup"><span data-stu-id="24eeb-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="24eeb-110">Il file XML può essere elaborato per formattare questo parametro in modo distinto.</span><span class="sxs-lookup"><span data-stu-id="24eeb-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="24eeb-111">Compilare con [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) per elaborare i commenti relativi alla documentazione in un file.</span><span class="sxs-lookup"><span data-stu-id="24eeb-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24eeb-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="24eeb-112">Example</span></span>  
 <span data-ttu-id="24eeb-113">Questo esempio usa il tag `<paramref>` per fare riferimento al parametro `id`.</span><span class="sxs-lookup"><span data-stu-id="24eeb-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="24eeb-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24eeb-114">See also</span></span>

- [<span data-ttu-id="24eeb-115">Tag di commento XML</span><span class="sxs-lookup"><span data-stu-id="24eeb-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
