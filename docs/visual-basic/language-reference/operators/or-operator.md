---
title: Operatore Or
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348246"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="88166-102">Operatore Or (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88166-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="88166-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="88166-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88166-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="88166-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="88166-105">Parti</span><span class="sxs-lookup"><span data-stu-id="88166-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="88166-106">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88166-106">Required.</span></span> <span data-ttu-id="88166-107">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="88166-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="88166-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span><span class="sxs-lookup"><span data-stu-id="88166-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="88166-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span><span class="sxs-lookup"><span data-stu-id="88166-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="88166-110">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88166-110">Required.</span></span> <span data-ttu-id="88166-111">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="88166-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="88166-112">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="88166-112">Required.</span></span> <span data-ttu-id="88166-113">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="88166-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88166-114">Note</span><span class="sxs-lookup"><span data-stu-id="88166-114">Remarks</span></span>  
 <span data-ttu-id="88166-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span><span class="sxs-lookup"><span data-stu-id="88166-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="88166-116">The following table illustrates how `result` is determined.</span><span class="sxs-lookup"><span data-stu-id="88166-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="88166-117">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="88166-117">If `expression1` is</span></span>|<span data-ttu-id="88166-118">And `expression2` is</span><span class="sxs-lookup"><span data-stu-id="88166-118">And `expression2` is</span></span>|<span data-ttu-id="88166-119">The value of `result` is</span><span class="sxs-lookup"><span data-stu-id="88166-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="88166-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span><span class="sxs-lookup"><span data-stu-id="88166-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="88166-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span><span class="sxs-lookup"><span data-stu-id="88166-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="88166-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span><span class="sxs-lookup"><span data-stu-id="88166-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="88166-123">If bit in `expression1` is</span><span class="sxs-lookup"><span data-stu-id="88166-123">If bit in `expression1` is</span></span>|<span data-ttu-id="88166-124">And bit in `expression2` is</span><span class="sxs-lookup"><span data-stu-id="88166-124">And bit in `expression2` is</span></span>|<span data-ttu-id="88166-125">The bit in `result` is</span><span class="sxs-lookup"><span data-stu-id="88166-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="88166-126">1</span><span class="sxs-lookup"><span data-stu-id="88166-126">1</span></span>|<span data-ttu-id="88166-127">1</span><span class="sxs-lookup"><span data-stu-id="88166-127">1</span></span>|<span data-ttu-id="88166-128">1</span><span class="sxs-lookup"><span data-stu-id="88166-128">1</span></span>|  
|<span data-ttu-id="88166-129">1</span><span class="sxs-lookup"><span data-stu-id="88166-129">1</span></span>|<span data-ttu-id="88166-130">0</span><span class="sxs-lookup"><span data-stu-id="88166-130">0</span></span>|<span data-ttu-id="88166-131">1</span><span class="sxs-lookup"><span data-stu-id="88166-131">1</span></span>|  
|<span data-ttu-id="88166-132">0</span><span class="sxs-lookup"><span data-stu-id="88166-132">0</span></span>|<span data-ttu-id="88166-133">1</span><span class="sxs-lookup"><span data-stu-id="88166-133">1</span></span>|<span data-ttu-id="88166-134">1</span><span class="sxs-lookup"><span data-stu-id="88166-134">1</span></span>|  
|<span data-ttu-id="88166-135">0</span><span class="sxs-lookup"><span data-stu-id="88166-135">0</span></span>|<span data-ttu-id="88166-136">0</span><span class="sxs-lookup"><span data-stu-id="88166-136">0</span></span>|<span data-ttu-id="88166-137">0</span><span class="sxs-lookup"><span data-stu-id="88166-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="88166-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span><span class="sxs-lookup"><span data-stu-id="88166-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="88166-139">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="88166-139">Data Types</span></span>  
 <span data-ttu-id="88166-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span><span class="sxs-lookup"><span data-stu-id="88166-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="88166-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="88166-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="88166-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span><span class="sxs-lookup"><span data-stu-id="88166-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="88166-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="88166-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="88166-144">Overload</span><span class="sxs-lookup"><span data-stu-id="88166-144">Overloading</span></span>  
 <span data-ttu-id="88166-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="88166-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="88166-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="88166-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="88166-147">Per altre informazioni, vedere [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="88166-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88166-148">Esempio</span><span class="sxs-lookup"><span data-stu-id="88166-148">Example</span></span>  
 <span data-ttu-id="88166-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span><span class="sxs-lookup"><span data-stu-id="88166-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="88166-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span><span class="sxs-lookup"><span data-stu-id="88166-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="88166-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span><span class="sxs-lookup"><span data-stu-id="88166-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88166-152">Esempio</span><span class="sxs-lookup"><span data-stu-id="88166-152">Example</span></span>  
 <span data-ttu-id="88166-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="88166-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="88166-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span><span class="sxs-lookup"><span data-stu-id="88166-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="88166-155">The preceding example produces results of 10, 14, and 14, respectively.</span><span class="sxs-lookup"><span data-stu-id="88166-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88166-156">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88166-156">See also</span></span>

- [<span data-ttu-id="88166-157">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88166-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="88166-158">Precedenza tra gli operatori in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88166-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="88166-159">Elenco degli operatori per funzionalità</span><span class="sxs-lookup"><span data-stu-id="88166-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="88166-160">Operatore OrElse</span><span class="sxs-lookup"><span data-stu-id="88166-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="88166-161">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88166-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
