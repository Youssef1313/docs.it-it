---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351591"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="9a5f3-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a5f3-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="9a5f3-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="9a5f3-104">If no modifier is specified, ByVal is the default.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="9a5f3-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="9a5f3-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a5f3-107">Note</span><span class="sxs-lookup"><span data-stu-id="9a5f3-107">Remarks</span></span>
 <span data-ttu-id="9a5f3-108">Il modificatore `ByVal` può essere usato nei contesti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a5f3-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="9a5f3-109">Istruzione Declare</span><span class="sxs-lookup"><span data-stu-id="9a5f3-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

 [<span data-ttu-id="9a5f3-110">Istruzione Function</span><span class="sxs-lookup"><span data-stu-id="9a5f3-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [<span data-ttu-id="9a5f3-111">Istruzione Operator</span><span class="sxs-lookup"><span data-stu-id="9a5f3-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [<span data-ttu-id="9a5f3-112">Istruzione Property</span><span class="sxs-lookup"><span data-stu-id="9a5f3-112">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [<span data-ttu-id="9a5f3-113">Istruzione Sub</span><span class="sxs-lookup"><span data-stu-id="9a5f3-113">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="9a5f3-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="9a5f3-114">Example</span></span>
 <span data-ttu-id="9a5f3-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="9a5f3-116">In the example, the argument is `c1`, an instance of class `Class1`.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="9a5f3-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span><span class="sxs-lookup"><span data-stu-id="9a5f3-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="9a5f3-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a5f3-118">See also</span></span>

- [<span data-ttu-id="9a5f3-119">Parole chiave</span><span class="sxs-lookup"><span data-stu-id="9a5f3-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="9a5f3-120">Passaggio di argomenti per valore e per riferimento</span><span class="sxs-lookup"><span data-stu-id="9a5f3-120">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
