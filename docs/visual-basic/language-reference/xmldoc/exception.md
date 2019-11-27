---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346968"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="ea182-101">\<> eccezione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea182-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="ea182-102">Specifica le eccezioni che possono essere generate.</span><span class="sxs-lookup"><span data-stu-id="ea182-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea182-103">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ea182-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea182-104">Parametri</span><span class="sxs-lookup"><span data-stu-id="ea182-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ea182-105">Riferimento ad un'eccezione disponibile dall'ambiente di compilazione corrente.</span><span class="sxs-lookup"><span data-stu-id="ea182-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="ea182-106">Il compilatore controlla che l'eccezione specificata esista e converte `member` nel nome canonico dell'elemento nel file XML di output.</span><span class="sxs-lookup"><span data-stu-id="ea182-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="ea182-107">`member` deve essere racchiuso tra virgolette doppie (" ").</span><span class="sxs-lookup"><span data-stu-id="ea182-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ea182-108">Descrizione.</span><span class="sxs-lookup"><span data-stu-id="ea182-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea182-109">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ea182-109">Remarks</span></span>  
 <span data-ttu-id="ea182-110">Usare il tag `<exception>` per specificare le eccezioni che possono essere generate.</span><span class="sxs-lookup"><span data-stu-id="ea182-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="ea182-111">Questo tag viene applicato a una definizione di metodo.</span><span class="sxs-lookup"><span data-stu-id="ea182-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="ea182-112">Compilare con [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) per elaborare i commenti relativi alla documentazione in un file.</span><span class="sxs-lookup"><span data-stu-id="ea182-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea182-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="ea182-113">Example</span></span>  
 <span data-ttu-id="ea182-114">In questo esempio viene usato il tag `<exception>` per descrivere un'eccezione che la funzione `IntDivide` può generare.</span><span class="sxs-lookup"><span data-stu-id="ea182-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ea182-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea182-115">See also</span></span>

- [<span data-ttu-id="ea182-116">Tag di commento XML</span><span class="sxs-lookup"><span data-stu-id="ea182-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
