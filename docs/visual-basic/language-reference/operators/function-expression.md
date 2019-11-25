---
title: Espressione di funzione
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: d14d7c9bc701b5e06c51202c07c3b79832aba7cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331073"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="8e920-102">Espressione di funzione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e920-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="8e920-103">Declares the parameters and code that define a function lambda expression.</span><span class="sxs-lookup"><span data-stu-id="8e920-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e920-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8e920-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="8e920-105">Parti</span><span class="sxs-lookup"><span data-stu-id="8e920-105">Parts</span></span>  
  
|<span data-ttu-id="8e920-106">Termine</span><span class="sxs-lookup"><span data-stu-id="8e920-106">Term</span></span>|<span data-ttu-id="8e920-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="8e920-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="8e920-108">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="8e920-108">Optional.</span></span> <span data-ttu-id="8e920-109">A list of local variable names that represent the parameters of this procedure.</span><span class="sxs-lookup"><span data-stu-id="8e920-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="8e920-110">The parentheses must be present even when the list is empty.</span><span class="sxs-lookup"><span data-stu-id="8e920-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="8e920-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="8e920-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="8e920-112">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="8e920-112">Required.</span></span> <span data-ttu-id="8e920-113">A single expression.</span><span class="sxs-lookup"><span data-stu-id="8e920-113">A single expression.</span></span> <span data-ttu-id="8e920-114">The type of the expression is the return type of the function.</span><span class="sxs-lookup"><span data-stu-id="8e920-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="8e920-115">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="8e920-115">Required.</span></span> <span data-ttu-id="8e920-116">A list of statements that returns a value by using the `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="8e920-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="8e920-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span><span class="sxs-lookup"><span data-stu-id="8e920-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e920-118">Note</span><span class="sxs-lookup"><span data-stu-id="8e920-118">Remarks</span></span>  
 <span data-ttu-id="8e920-119">A *lambda expression* is a function without a name that calculates and returns a value.</span><span class="sxs-lookup"><span data-stu-id="8e920-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="8e920-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="8e920-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="8e920-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="8e920-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="8e920-122">Sintassi delle espressioni lambda</span><span class="sxs-lookup"><span data-stu-id="8e920-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="8e920-123">The syntax of a lambda expression resembles that of a standard function.</span><span class="sxs-lookup"><span data-stu-id="8e920-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="8e920-124">The differences are as follows:</span><span class="sxs-lookup"><span data-stu-id="8e920-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="8e920-125">A lambda expression does not have a name.</span><span class="sxs-lookup"><span data-stu-id="8e920-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="8e920-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8e920-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="8e920-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span><span class="sxs-lookup"><span data-stu-id="8e920-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="8e920-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span><span class="sxs-lookup"><span data-stu-id="8e920-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="8e920-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8e920-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="8e920-130">The body of a single-line lambda expression must be an expression, not a statement.</span><span class="sxs-lookup"><span data-stu-id="8e920-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="8e920-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span><span class="sxs-lookup"><span data-stu-id="8e920-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="8e920-132">Either all parameters must have specified data types or all must be inferred.</span><span class="sxs-lookup"><span data-stu-id="8e920-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="8e920-133">Optional and Paramarray parameters are not permitted.</span><span class="sxs-lookup"><span data-stu-id="8e920-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="8e920-134">Generic parameters are not permitted.</span><span class="sxs-lookup"><span data-stu-id="8e920-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e920-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e920-135">Example</span></span>  
 <span data-ttu-id="8e920-136">The following examples show two ways to create simple lambda expressions.</span><span class="sxs-lookup"><span data-stu-id="8e920-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="8e920-137">The first uses a `Dim` to provide a name for the function.</span><span class="sxs-lookup"><span data-stu-id="8e920-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="8e920-138">To call the function, you send in a value for the parameter.</span><span class="sxs-lookup"><span data-stu-id="8e920-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="8e920-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e920-139">Example</span></span>  
 <span data-ttu-id="8e920-140">Alternatively, you can declare and run the function at the same time.</span><span class="sxs-lookup"><span data-stu-id="8e920-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="8e920-141">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e920-141">Example</span></span>  
 <span data-ttu-id="8e920-142">Following is an example of a lambda expression that increments its argument and returns the value.</span><span class="sxs-lookup"><span data-stu-id="8e920-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="8e920-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span><span class="sxs-lookup"><span data-stu-id="8e920-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="8e920-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8e920-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="8e920-145">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e920-145">Example</span></span>  
 <span data-ttu-id="8e920-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span><span class="sxs-lookup"><span data-stu-id="8e920-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="8e920-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span><span class="sxs-lookup"><span data-stu-id="8e920-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="8e920-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e920-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="8e920-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8e920-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e920-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8e920-150">See also</span></span>

- [<span data-ttu-id="8e920-151">Istruzione Function</span><span class="sxs-lookup"><span data-stu-id="8e920-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="8e920-152">Espressioni lambda</span><span class="sxs-lookup"><span data-stu-id="8e920-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="8e920-153">Operatori ed espressioni</span><span class="sxs-lookup"><span data-stu-id="8e920-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="8e920-154">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="8e920-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="8e920-155">Confronto di valori</span><span class="sxs-lookup"><span data-stu-id="8e920-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="8e920-156">Espressioni booleane</span><span class="sxs-lookup"><span data-stu-id="8e920-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="8e920-157">Operatore If</span><span class="sxs-lookup"><span data-stu-id="8e920-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="8e920-158">Conversione di tipo relaxed del delegato</span><span class="sxs-lookup"><span data-stu-id="8e920-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
