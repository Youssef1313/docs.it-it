---
title: '#Direttiva Const (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 031f35df24fd52aeeafcb7b4c0208806d7fc5fc4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774751"
---
# <a name="const-directive"></a><span data-ttu-id="4a081-102">Direttiva #Const</span><span class="sxs-lookup"><span data-stu-id="4a081-102">#Const Directive</span></span>
<span data-ttu-id="4a081-103">Definisce le costanti del compilatore condizionale per Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4a081-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a081-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4a081-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4a081-105">Parti</span><span class="sxs-lookup"><span data-stu-id="4a081-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="4a081-106">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4a081-106">Required.</span></span> <span data-ttu-id="4a081-107">Nome della costante da definire.</span><span class="sxs-lookup"><span data-stu-id="4a081-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="4a081-108">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="4a081-108">Required.</span></span> <span data-ttu-id="4a081-109">Valore letterale, altra costante del compilatore condizionale o qualsiasi combinazione che includa tutti gli operatori aritmetici o logici eccetto `Is`.</span><span class="sxs-lookup"><span data-stu-id="4a081-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a081-110">Note</span><span class="sxs-lookup"><span data-stu-id="4a081-110">Remarks</span></span>  
 <span data-ttu-id="4a081-111">Le costanti del compilatore condizionale sono sempre private per il file in cui sono visualizzate.</span><span class="sxs-lookup"><span data-stu-id="4a081-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="4a081-112">Non è possibile creare costanti del compilatore pubbliche usando la direttiva `#Const`; è possibile crearli solo nell'interfaccia utente o con l'opzione del compilatore `/define`.</span><span class="sxs-lookup"><span data-stu-id="4a081-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="4a081-113">È possibile utilizzare solo le costanti e i valori letterali del compilatore condizionale in `expression`.</span><span class="sxs-lookup"><span data-stu-id="4a081-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="4a081-114">L'uso di una costante standard definita con `Const` causa un errore.</span><span class="sxs-lookup"><span data-stu-id="4a081-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="4a081-115">Viceversa, è possibile utilizzare le costanti definite con la parola chiave `#Const` solo per la compilazione condizionale.</span><span class="sxs-lookup"><span data-stu-id="4a081-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="4a081-116">Le costanti possono anche essere indefinite, nel qual caso hanno il valore `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="4a081-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a081-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="4a081-117">Example</span></span>  
 <span data-ttu-id="4a081-118">In questo esempio viene usata la direttiva `#Const`.</span><span class="sxs-lookup"><span data-stu-id="4a081-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4a081-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a081-119">See also</span></span>

- [<span data-ttu-id="4a081-120">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a081-120">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="4a081-121">Direttive #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="4a081-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="4a081-122">Istruzione Const</span><span class="sxs-lookup"><span data-stu-id="4a081-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="4a081-123">Compilazione condizionale</span><span class="sxs-lookup"><span data-stu-id="4a081-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="4a081-124">Istruzione If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="4a081-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
