---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523925"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="603db-102">\<exception > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="603db-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="603db-103">Specifica le eccezioni che possono essere generate.</span><span class="sxs-lookup"><span data-stu-id="603db-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603db-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="603db-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="603db-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="603db-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="603db-106">Riferimento ad un'eccezione disponibile dall'ambiente di compilazione corrente.</span><span class="sxs-lookup"><span data-stu-id="603db-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="603db-107">Il compilatore controlla che l'eccezione specificata esista e converte `member` nel nome canonico dell'elemento nel file XML di output.</span><span class="sxs-lookup"><span data-stu-id="603db-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="603db-108">`member` deve essere racchiuso tra virgolette doppie (" ").</span><span class="sxs-lookup"><span data-stu-id="603db-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="603db-109">Descrizione.</span><span class="sxs-lookup"><span data-stu-id="603db-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="603db-110">Note</span><span class="sxs-lookup"><span data-stu-id="603db-110">Remarks</span></span>  
 <span data-ttu-id="603db-111">Usare il tag `<exception>` per specificare le eccezioni che possono essere generate.</span><span class="sxs-lookup"><span data-stu-id="603db-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="603db-112">Questo tag viene applicato a una definizione di metodo.</span><span class="sxs-lookup"><span data-stu-id="603db-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="603db-113">Compilare con [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) per elaborare i commenti relativi alla documentazione in un file.</span><span class="sxs-lookup"><span data-stu-id="603db-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="603db-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="603db-114">Example</span></span>  
 <span data-ttu-id="603db-115">In questo esempio viene usato il tag `<exception>` per descrivere un'eccezione che la funzione `IntDivide` può generare.</span><span class="sxs-lookup"><span data-stu-id="603db-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="603db-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="603db-116">See also</span></span>

- [<span data-ttu-id="603db-117">Tag di commento XML</span><span class="sxs-lookup"><span data-stu-id="603db-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
