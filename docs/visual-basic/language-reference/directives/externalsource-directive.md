---
title: '#Direttiva ExternalSource (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696829"
---
# <a name="externalsource-directive"></a><span data-ttu-id="1646b-102">Direttiva #ExternalSource</span><span class="sxs-lookup"><span data-stu-id="1646b-102">#ExternalSource Directive</span></span>
<span data-ttu-id="1646b-103">Indica un mapping tra le righe specifiche del codice sorgente e il testo esterno all'origine.</span><span class="sxs-lookup"><span data-stu-id="1646b-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1646b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1646b-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="1646b-105">Parti</span><span class="sxs-lookup"><span data-stu-id="1646b-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="1646b-106">Percorso dell'origine esterna.</span><span class="sxs-lookup"><span data-stu-id="1646b-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="1646b-107">Il numero di riga della prima riga dell'origine esterna.</span><span class="sxs-lookup"><span data-stu-id="1646b-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="1646b-108">Riga in cui si è verificato l'errore nell'origine esterna.</span><span class="sxs-lookup"><span data-stu-id="1646b-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="1646b-109">Termina il blocco `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="1646b-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1646b-110">Note</span><span class="sxs-lookup"><span data-stu-id="1646b-110">Remarks</span></span>  
 <span data-ttu-id="1646b-111">Questa direttiva viene utilizzata solo dal compilatore e dal debugger.</span><span class="sxs-lookup"><span data-stu-id="1646b-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="1646b-112">Un file di origine può includere direttive di origine esterne, che indicano un mapping tra righe specifiche di codice nel file di origine e testo esterno all'origine, ad esempio un file aspx.</span><span class="sxs-lookup"><span data-stu-id="1646b-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="1646b-113">Se durante la compilazione vengono rilevati errori nel codice sorgente designato, vengono identificati come provenienti dall'origine esterna.</span><span class="sxs-lookup"><span data-stu-id="1646b-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="1646b-114">Le direttive external source non hanno alcun effetto sulla compilazione e non possono essere annidate.</span><span class="sxs-lookup"><span data-stu-id="1646b-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="1646b-115">Sono destinate esclusivamente all'uso interno da parte dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1646b-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1646b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1646b-116">See also</span></span>

- [<span data-ttu-id="1646b-117">Compilazione condizionale</span><span class="sxs-lookup"><span data-stu-id="1646b-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
