---
title: Combinazione efficace di operatori
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348974"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="0af57-102">Combinazione efficace di operatori (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af57-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="0af57-103">Complex expressions can contain many different operators.</span><span class="sxs-lookup"><span data-stu-id="0af57-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="0af57-104">Questa condizione è illustrata nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="0af57-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="0af57-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span><span class="sxs-lookup"><span data-stu-id="0af57-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="0af57-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0af57-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="0af57-107">Parenthetical Expressions</span><span class="sxs-lookup"><span data-stu-id="0af57-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="0af57-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span><span class="sxs-lookup"><span data-stu-id="0af57-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="0af57-109">Si osservi l'esempio riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="0af57-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="0af57-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span><span class="sxs-lookup"><span data-stu-id="0af57-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="0af57-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span><span class="sxs-lookup"><span data-stu-id="0af57-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="0af57-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span><span class="sxs-lookup"><span data-stu-id="0af57-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="0af57-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span><span class="sxs-lookup"><span data-stu-id="0af57-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="0af57-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span><span class="sxs-lookup"><span data-stu-id="0af57-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="0af57-115">Nested Parenthetical Expressions</span><span class="sxs-lookup"><span data-stu-id="0af57-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="0af57-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span><span class="sxs-lookup"><span data-stu-id="0af57-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="0af57-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span><span class="sxs-lookup"><span data-stu-id="0af57-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="0af57-118">Questa condizione è illustrata nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="0af57-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="0af57-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span><span class="sxs-lookup"><span data-stu-id="0af57-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="0af57-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span><span class="sxs-lookup"><span data-stu-id="0af57-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af57-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0af57-121">See also</span></span>

- [<span data-ttu-id="0af57-122">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af57-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="0af57-123">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af57-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="0af57-124">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af57-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="0af57-125">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af57-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0af57-126">Espressioni booleane</span><span class="sxs-lookup"><span data-stu-id="0af57-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="0af57-127">Confronto di valori</span><span class="sxs-lookup"><span data-stu-id="0af57-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="0af57-128">Procedura: Calcolare valori numerici</span><span class="sxs-lookup"><span data-stu-id="0af57-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="0af57-129">Precedenza tra gli operatori in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af57-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
