---
title: Confronto di valori
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346293"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="88875-102">Confronto di valori (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88875-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="88875-103">Gli operatori di confronto possono essere utilizzati per costruire espressioni che confrontano i valori delle variabili numeriche.</span><span class="sxs-lookup"><span data-stu-id="88875-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="88875-104">Queste espressioni restituiscono un valore `Boolean` a seconda che il confronto sia true o false.</span><span class="sxs-lookup"><span data-stu-id="88875-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="88875-105">Di seguito sono riportati alcuni esempi di espressioni di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="88875-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="88875-106">La prima espressione restituisce `True`, perché 45 è maggiore di 26.</span><span class="sxs-lookup"><span data-stu-id="88875-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="88875-107">Nel secondo esempio viene restituito `False`, perché 26 non è maggiore di 45.</span><span class="sxs-lookup"><span data-stu-id="88875-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="88875-108">È anche possibile confrontare le espressioni numeriche in questo modo.</span><span class="sxs-lookup"><span data-stu-id="88875-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="88875-109">Le espressioni che si confrontano possono essere espressioni complesse, come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="88875-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="88875-110">L'espressione complessa precedente include valori letterali, variabili e chiamate di funzione.</span><span class="sxs-lookup"><span data-stu-id="88875-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="88875-111">Le espressioni su entrambi i lati dell'operatore di confronto vengono valutate e i valori risultanti vengono quindi confrontati tramite l'operatore di confronto `>=`.</span><span class="sxs-lookup"><span data-stu-id="88875-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="88875-112">Se il valore dell'espressione sul lato sinistro è maggiore o uguale al valore dell'espressione a destra, l'intera espressione restituisce `True`; in caso contrario, restituisce `False`.</span><span class="sxs-lookup"><span data-stu-id="88875-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="88875-113">Le espressioni che confrontano i valori vengono utilizzate più di frequente nelle costruzioni `If...Then`, come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="88875-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="88875-114">Il segno di `=` è un operatore di confronto e un operatore di assegnazione.</span><span class="sxs-lookup"><span data-stu-id="88875-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="88875-115">Quando viene usato come operatore di confronto, valuta se il valore a sinistra è uguale al valore a destra, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="88875-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="88875-116">È anche possibile usare un'espressione di confronto ovunque sia necessario un valore di `Boolean`, ad esempio in un'istruzione `If`, `While`, `Loop`o `ElseIf` oppure quando si assegna o si passa un valore a una variabile `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="88875-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="88875-117">Nell'esempio seguente, il valore restituito dall'espressione di confronto viene assegnato a una variabile `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="88875-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="88875-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88875-118">See also</span></span>

- [<span data-ttu-id="88875-119">Espressioni booleane</span><span class="sxs-lookup"><span data-stu-id="88875-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="88875-120">Operatori ed espressioni</span><span class="sxs-lookup"><span data-stu-id="88875-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="88875-121">Operatori di confronto in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88875-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="88875-122">Procedura: Calcolare valori numerici</span><span class="sxs-lookup"><span data-stu-id="88875-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="88875-123">Precedenza tra gli operatori in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88875-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
