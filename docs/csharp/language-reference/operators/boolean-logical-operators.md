---
title: Operatori logici booleani - Riferimenti per C#
description: Informazioni sugli operatori C# che eseguono operazioni logiche di negazione, congiunzione (AND) e disgiunzione inclusiva ed esclusiva (OR) con operandi booleani.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: b2c3553f527e9fec8856297c7424a081b5b31db0
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609932"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="6de68-103">Operatori logici booleani (Riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="6de68-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="6de68-104">Gli operatori seguenti eseguono operazioni logiche con gli operandi [bool](../keywords/bool.md):</span><span class="sxs-lookup"><span data-stu-id="6de68-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="6de68-105">Operatore unario [`!` (negazione logica)](#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="6de68-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="6de68-106">Operatori binari [`&` (AND logico)](#logical-and-operator-), [`|` (OR logico)](#logical-or-operator-) e [`^` (OR esclusivo logico)](#logical-exclusive-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="6de68-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="6de68-107">Questi operatori valutano sempre entrambi gli operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="6de68-108">Operatori binari [`&&` (AND condizionale logico)](#conditional-logical-and-operator-) e [`||` (OR condizionale logico)](#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="6de68-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="6de68-109">Questi operatori valutano l'operando di destra solo se è necessario.</span><span class="sxs-lookup"><span data-stu-id="6de68-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="6de68-110">Per gli operandi dei tipi [integrali](../builtin-types/integral-numeric-types.md), gli operatori `&`, `|` e `^` eseguono operazioni logiche bit per bit.</span><span class="sxs-lookup"><span data-stu-id="6de68-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="6de68-111">Per altre informazioni, vedere [Operatori di scorrimento e bit per bit](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6de68-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="6de68-112">Operatore di negazione logica !</span><span class="sxs-lookup"><span data-stu-id="6de68-112">Logical negation operator !</span></span>

<span data-ttu-id="6de68-113">L'operatore `!` calcola la negazione logica del suo operando.</span><span class="sxs-lookup"><span data-stu-id="6de68-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="6de68-114">Vale a dire, produce `true` se l'operando restituisce `false` e `false` se l'operando restituisce `true`:</span><span class="sxs-lookup"><span data-stu-id="6de68-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a> <span data-ttu-id="6de68-115">Operatore AND logico &amp;</span><span class="sxs-lookup"><span data-stu-id="6de68-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="6de68-116">L'operatore `&` calcola l'AND logico dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="6de68-117">Il risultato di `x & y` è `true` se `x` e `y` restituiscono `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="6de68-118">In caso contrario, il risultato è `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="6de68-119">L'operatore `&` valuta entrambi gli operandi anche se l'operando di sinistra restituisce `false`, in modo che il risultato sia `false` indipendentemente dal valore dell'operando di destra.</span><span class="sxs-lookup"><span data-stu-id="6de68-119">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="6de68-120">Nell'esempio seguente l'operando di destra dell'operatore `&` è una chiamata a un metodo, che viene eseguita indipendentemente dal valore dell'operando di sinistra:</span><span class="sxs-lookup"><span data-stu-id="6de68-120">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="6de68-121">L'[operatore AND condizionale logico](#conditional-logical-and-operator-) `&&` calcola anche l'AND logico dei relativi operandi, ma non valuta l'operando di destra se l'operando di sinistra restituisce `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="6de68-122">Per gli operandi dei tipi integrali, l'operatore `&` calcola l'[AND logico bit per bit](bitwise-and-shift-operators.md#logical-and-operator-) dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="6de68-123">L'operatore unario `&` è l'[operatore address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="6de68-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="6de68-124">Operatore OR esclusivo logico: ^</span><span class="sxs-lookup"><span data-stu-id="6de68-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="6de68-125">L'operatore `^` calcola l'OR esclusivo logico, noto anche come XOR logico, dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="6de68-126">Il risultato di `x ^ y` è `true` se `x` restituisce `true` e `y` restituisce `false` oppure `x` restituisce `false` e `y` restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="6de68-127">In caso contrario, il risultato è `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6de68-128">Vale a dire, per gli operandi `bool`, l'operatore `^` calcola lo stesso risultato dell'[operatore di disuguaglianza](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="6de68-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="6de68-129">Per gli operandi dei tipi integrali, l'operatore `^` calcola l'[OR esclusivo logico bit per bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="6de68-130">Operatore OR logico |</span><span class="sxs-lookup"><span data-stu-id="6de68-130">Logical OR operator |</span></span>

<span data-ttu-id="6de68-131">L'operatore `|` calcola l'OR logico dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="6de68-132">Il risultato di `x | y` è `true` se `x` o `y` restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="6de68-133">In caso contrario, il risultato è `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="6de68-134">L'operatore `|` valuta entrambi gli operandi anche se l'operando di sinistra restituisce `true`, in modo che il risultato sia `true` indipendentemente dal valore dell'operando di destra.</span><span class="sxs-lookup"><span data-stu-id="6de68-134">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="6de68-135">Nell'esempio seguente l'operando di destra dell'operatore `|` è una chiamata a un metodo, che viene eseguita indipendentemente dal valore dell'operando di sinistra:</span><span class="sxs-lookup"><span data-stu-id="6de68-135">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="6de68-136">L'[operatore OR condizionale logico](#conditional-logical-or-operator-) `||` calcola anche l'OR logico dei relativi operandi, ma non valuta l'operando di destra se l'operando di sinistra restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="6de68-137">Per gli operandi dei tipi integrali, l'operatore `|` calcola l'[OR logico bit per bit](bitwise-and-shift-operators.md#logical-or-operator-) dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="6de68-138">Operatore AND condizionale logico &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="6de68-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="6de68-139">L'operatore AND condizionale logico `&&`, chiamato anche operatore AND logico di "corto circuito", calcola l'AND logico dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="6de68-140">Il risultato di `x && y` è `true` se `x` e `y` restituiscono `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="6de68-141">In caso contrario, il risultato è `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6de68-142">Se `x` è `false`, `y` non viene valutato.</span><span class="sxs-lookup"><span data-stu-id="6de68-142">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="6de68-143">Nell'esempio seguente l'operando di destra dell'operatore `&&` è una chiamata a un metodo, che non viene eseguita se l'operando di sinistra restituisce `false`:</span><span class="sxs-lookup"><span data-stu-id="6de68-143">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="6de68-144">L'[operatore AND logico](#logical-and-operator-) `&` calcola anche l'AND logico dei relativi operandi, ma valuta sempre entrambi gli operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="6de68-145">Operatore OR condizionale logico ||</span><span class="sxs-lookup"><span data-stu-id="6de68-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="6de68-146">L'operatore OR condizionale logico `||`, chiamato anche operatore OR logico di "corto circuito", calcola l'OR logico dei relativi operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="6de68-147">Il risultato di `x || y` è `true` se `x` o `y` restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="6de68-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="6de68-148">In caso contrario, il risultato è `false`.</span><span class="sxs-lookup"><span data-stu-id="6de68-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6de68-149">Se `x` è `true`, `y` non viene valutato.</span><span class="sxs-lookup"><span data-stu-id="6de68-149">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="6de68-150">Nell'esempio seguente l'operando di destra dell'operatore `||` è una chiamata a un metodo, che non viene eseguita se l'operando di sinistra restituisce `true`:</span><span class="sxs-lookup"><span data-stu-id="6de68-150">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="6de68-151">L'[operatore OR logico](#logical-or-operator-) `|` calcola anche l'OR logico dei relativi operandi, ma valuta sempre entrambi gli operandi.</span><span class="sxs-lookup"><span data-stu-id="6de68-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="6de68-152">Operatori logici booleani nullable</span><span class="sxs-lookup"><span data-stu-id="6de68-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="6de68-153">Per gli operandi `bool?`, gli operatori `&` e `|` supportano la logica a tre valori.</span><span class="sxs-lookup"><span data-stu-id="6de68-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="6de68-154">La semantica di questi operatori è definita dalla tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="6de68-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="6de68-155">x</span><span class="sxs-lookup"><span data-stu-id="6de68-155">x</span></span>|<span data-ttu-id="6de68-156">y</span><span class="sxs-lookup"><span data-stu-id="6de68-156">y</span></span>|<span data-ttu-id="6de68-157">x&y</span><span class="sxs-lookup"><span data-stu-id="6de68-157">x&y</span></span>|<span data-ttu-id="6de68-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="6de68-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="6de68-159">true</span><span class="sxs-lookup"><span data-stu-id="6de68-159">true</span></span>|<span data-ttu-id="6de68-160">true</span><span class="sxs-lookup"><span data-stu-id="6de68-160">true</span></span>|<span data-ttu-id="6de68-161">true</span><span class="sxs-lookup"><span data-stu-id="6de68-161">true</span></span>|<span data-ttu-id="6de68-162">true</span><span class="sxs-lookup"><span data-stu-id="6de68-162">true</span></span>|  
|<span data-ttu-id="6de68-163">true</span><span class="sxs-lookup"><span data-stu-id="6de68-163">true</span></span>|<span data-ttu-id="6de68-164">False</span><span class="sxs-lookup"><span data-stu-id="6de68-164">false</span></span>|<span data-ttu-id="6de68-165">false</span><span class="sxs-lookup"><span data-stu-id="6de68-165">false</span></span>|<span data-ttu-id="6de68-166">true</span><span class="sxs-lookup"><span data-stu-id="6de68-166">true</span></span>|  
|<span data-ttu-id="6de68-167">true</span><span class="sxs-lookup"><span data-stu-id="6de68-167">true</span></span>|<span data-ttu-id="6de68-168">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-168">null</span></span>|<span data-ttu-id="6de68-169">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-169">null</span></span>|<span data-ttu-id="6de68-170">true</span><span class="sxs-lookup"><span data-stu-id="6de68-170">true</span></span>|  
|<span data-ttu-id="6de68-171">False</span><span class="sxs-lookup"><span data-stu-id="6de68-171">false</span></span>|<span data-ttu-id="6de68-172">true</span><span class="sxs-lookup"><span data-stu-id="6de68-172">true</span></span>|<span data-ttu-id="6de68-173">False</span><span class="sxs-lookup"><span data-stu-id="6de68-173">false</span></span>|<span data-ttu-id="6de68-174">true</span><span class="sxs-lookup"><span data-stu-id="6de68-174">true</span></span>|  
|<span data-ttu-id="6de68-175">False</span><span class="sxs-lookup"><span data-stu-id="6de68-175">false</span></span>|<span data-ttu-id="6de68-176">False</span><span class="sxs-lookup"><span data-stu-id="6de68-176">false</span></span>|<span data-ttu-id="6de68-177">False</span><span class="sxs-lookup"><span data-stu-id="6de68-177">false</span></span>|<span data-ttu-id="6de68-178">False</span><span class="sxs-lookup"><span data-stu-id="6de68-178">false</span></span>|  
|<span data-ttu-id="6de68-179">False</span><span class="sxs-lookup"><span data-stu-id="6de68-179">false</span></span>|<span data-ttu-id="6de68-180">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-180">null</span></span>|<span data-ttu-id="6de68-181">False</span><span class="sxs-lookup"><span data-stu-id="6de68-181">false</span></span>|<span data-ttu-id="6de68-182">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-182">null</span></span>|  
|<span data-ttu-id="6de68-183">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-183">null</span></span>|<span data-ttu-id="6de68-184">true</span><span class="sxs-lookup"><span data-stu-id="6de68-184">true</span></span>|<span data-ttu-id="6de68-185">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-185">null</span></span>|<span data-ttu-id="6de68-186">true</span><span class="sxs-lookup"><span data-stu-id="6de68-186">true</span></span>|  
|<span data-ttu-id="6de68-187">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-187">null</span></span>|<span data-ttu-id="6de68-188">False</span><span class="sxs-lookup"><span data-stu-id="6de68-188">false</span></span>|<span data-ttu-id="6de68-189">False</span><span class="sxs-lookup"><span data-stu-id="6de68-189">false</span></span>|<span data-ttu-id="6de68-190">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-190">null</span></span>|  
|<span data-ttu-id="6de68-191">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-191">null</span></span>|<span data-ttu-id="6de68-192">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-192">null</span></span>|<span data-ttu-id="6de68-193">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-193">null</span></span>|<span data-ttu-id="6de68-194">Null</span><span class="sxs-lookup"><span data-stu-id="6de68-194">null</span></span>|  

<span data-ttu-id="6de68-195">Il comportamento di questi operatori è diverso dal comportamento tipico degli operatori con tipi valore nullable.</span><span class="sxs-lookup"><span data-stu-id="6de68-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="6de68-196">In genere un operatore definito per gli operandi di un tipo valore può essere usato anche con gli operandi del tipo valore nullable corrispondente.</span><span class="sxs-lookup"><span data-stu-id="6de68-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="6de68-197">Un operatore di questo tipo produce `null` se uno qualsiasi dei suoi operandi è `null`.</span><span class="sxs-lookup"><span data-stu-id="6de68-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="6de68-198">Tuttavia gli operatori `&` e `|` possono produrre valori non Null anche se uno degli operandi è `null`.</span><span class="sxs-lookup"><span data-stu-id="6de68-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="6de68-199">Per altre informazioni sul comportamento degli operatori con i tipi valore nullable, vedere la sezione [Operatori](../../programming-guide/nullable-types/using-nullable-types.md#operators) dell'articolo [Uso dei tipi nullable](../../programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="6de68-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="6de68-200">È anche possibile usare gli operatori `!` e `^` con gli operandi `bool?`, come mostrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="6de68-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="6de68-201">Gli operatori condizionali logici `&&` e `||` non supportano gli operandi `bool?`.</span><span class="sxs-lookup"><span data-stu-id="6de68-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="6de68-202">Assegnazione composta</span><span class="sxs-lookup"><span data-stu-id="6de68-202">Compound assignment</span></span>

<span data-ttu-id="6de68-203">Per un operatore binario `op`, un'espressione di assegnazione composta in formato</span><span class="sxs-lookup"><span data-stu-id="6de68-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="6de68-204">equivale a</span><span class="sxs-lookup"><span data-stu-id="6de68-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="6de68-205">con la differenza che `x` viene valutato una sola volta.</span><span class="sxs-lookup"><span data-stu-id="6de68-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6de68-206">Gli operatori `&`, `|` e `^` supportano l'assegnazione composta, come illustrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="6de68-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="6de68-207">Gli operatori condizionali logici `&&` e `||` non supportano l'assegnazione composta.</span><span class="sxs-lookup"><span data-stu-id="6de68-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="6de68-208">Precedenza tra gli operatori</span><span class="sxs-lookup"><span data-stu-id="6de68-208">Operator precedence</span></span>

<span data-ttu-id="6de68-209">Nell'elenco seguente gli operatori logici sono ordinati dalla precedenza più elevata a quella più bassa:</span><span class="sxs-lookup"><span data-stu-id="6de68-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="6de68-210">Operatore di negazione logica `!`</span><span class="sxs-lookup"><span data-stu-id="6de68-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="6de68-211">Operatore AND logico `&`</span><span class="sxs-lookup"><span data-stu-id="6de68-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="6de68-212">Operatore OR esclusivo logico `^`</span><span class="sxs-lookup"><span data-stu-id="6de68-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="6de68-213">Operatore OR logico `|`</span><span class="sxs-lookup"><span data-stu-id="6de68-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="6de68-214">Operatore AND condizionale logico `&&`</span><span class="sxs-lookup"><span data-stu-id="6de68-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="6de68-215">Operatore OR condizionale logico `||`</span><span class="sxs-lookup"><span data-stu-id="6de68-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="6de68-216">Usare le parentesi, `()`, per cambiare l'ordine di valutazione imposto dalla precedenza tra gli operatori:</span><span class="sxs-lookup"><span data-stu-id="6de68-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="6de68-217">Per l'elenco completo degli operatori C# ordinati in base al livello di precedenza, vedere [Operatori C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="6de68-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6de68-218">Overload degli operatori</span><span class="sxs-lookup"><span data-stu-id="6de68-218">Operator overloadability</span></span>

<span data-ttu-id="6de68-219">Un tipo definito dall'utente può eseguire l'[overload](operator-overloading.md) degli operatori `!`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="6de68-219">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="6de68-220">Quando viene eseguito l'overload di un operatore binario, viene anche eseguito in modo implicito l'overload dell'operatore di assegnazione composta corrispondente.</span><span class="sxs-lookup"><span data-stu-id="6de68-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="6de68-221">Un tipo definito dall'utente non può eseguire in modo esplicito l'overload di un operatore di assegnazione composta.</span><span class="sxs-lookup"><span data-stu-id="6de68-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="6de68-222">Un tipo definito dall'utente non può eseguire l'overload degli operatori condizionali logici `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="6de68-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="6de68-223">Tuttavia, se un tipo definito dall'utente esegue l'overload degli [operatori true e false](true-false-operators.md) e dell'operatore `&` o `|` in un determinato modo, l'operazione `&&` o `||` può essere valutata per gli operandi di quel tipo.</span><span class="sxs-lookup"><span data-stu-id="6de68-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="6de68-224">Per altre informazioni, vedere la sezione [Operatori logici condizionali definiti dall'utente](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) di [Specifica del linguaggio C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6de68-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6de68-225">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="6de68-225">C# language specification</span></span>

<span data-ttu-id="6de68-226">Per altre informazioni, vedere le sezioni seguenti delle [specifiche del linguaggio C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="6de68-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6de68-227">Operatore di negazione logica</span><span class="sxs-lookup"><span data-stu-id="6de68-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="6de68-228">Operatori logici</span><span class="sxs-lookup"><span data-stu-id="6de68-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="6de68-229">Operatori logici condizionali</span><span class="sxs-lookup"><span data-stu-id="6de68-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="6de68-230">Assegnazione composta</span><span class="sxs-lookup"><span data-stu-id="6de68-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="6de68-231">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6de68-231">See also</span></span>

- [<span data-ttu-id="6de68-232">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="6de68-232">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6de68-233">Operatori C#</span><span class="sxs-lookup"><span data-stu-id="6de68-233">C# operators</span></span>](index.md)
- [<span data-ttu-id="6de68-234">Operatori di scorrimento e bit per bit</span><span class="sxs-lookup"><span data-stu-id="6de68-234">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
