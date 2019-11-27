---
title: Operatore <<
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350975"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b1326-102">Operatore \<\< (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1326-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="b1326-103">Esegue uno scorrimento a sinistra aritmetico in uno schema di bit.</span><span class="sxs-lookup"><span data-stu-id="b1326-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1326-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b1326-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b1326-105">Parti</span><span class="sxs-lookup"><span data-stu-id="b1326-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b1326-106">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="b1326-106">Required.</span></span> <span data-ttu-id="b1326-107">Valore numerico integrale.</span><span class="sxs-lookup"><span data-stu-id="b1326-107">Integral numeric value.</span></span> <span data-ttu-id="b1326-108">Risultato dello spostamento dello schema di bit.</span><span class="sxs-lookup"><span data-stu-id="b1326-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="b1326-109">Il tipo di dati è uguale a quello di `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b1326-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="b1326-110">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="b1326-110">Required.</span></span> <span data-ttu-id="b1326-111">Espressione numerica integrale.</span><span class="sxs-lookup"><span data-stu-id="b1326-111">Integral numeric expression.</span></span> <span data-ttu-id="b1326-112">Modello di bit da spostare.</span><span class="sxs-lookup"><span data-stu-id="b1326-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="b1326-113">Il tipo di dati deve essere un tipo integrale (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`o `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b1326-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b1326-114">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="b1326-114">Required.</span></span> <span data-ttu-id="b1326-115">Espressione numerica.</span><span class="sxs-lookup"><span data-stu-id="b1326-115">Numeric expression.</span></span> <span data-ttu-id="b1326-116">Numero di bit per spostare lo schema di bit.</span><span class="sxs-lookup"><span data-stu-id="b1326-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="b1326-117">Il tipo di dati deve essere `Integer` o ampliato per `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b1326-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1326-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b1326-118">Remarks</span></span>  
 <span data-ttu-id="b1326-119">I turni aritmetici non sono circolari, il che significa che i bit spostati da un'estremità del risultato non vengono reintrodotti nell'altra estremità.</span><span class="sxs-lookup"><span data-stu-id="b1326-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b1326-120">In uno scorrimento a sinistra aritmetico, i bit spostati oltre l'intervallo del tipo di dati del risultato vengono rimossi e le posizioni dei bit sgomberate a destra vengono impostate su zero.</span><span class="sxs-lookup"><span data-stu-id="b1326-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="b1326-121">Per evitare uno spostamento di più bit rispetto al risultato, Visual Basic maschera il valore di `amount` con una maschera di dimensioni che corrisponde al tipo di dati di `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b1326-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="b1326-122">Il file binario e di questi valori viene utilizzato per l'importo dello spostamento.</span><span class="sxs-lookup"><span data-stu-id="b1326-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="b1326-123">Le maschere delle dimensioni sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1326-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="b1326-124">Tipo di dati di `pattern`</span><span class="sxs-lookup"><span data-stu-id="b1326-124">Data type of `pattern`</span></span>|<span data-ttu-id="b1326-125">Maschera dimensioni (decimale)</span><span class="sxs-lookup"><span data-stu-id="b1326-125">Size mask (decimal)</span></span>|<span data-ttu-id="b1326-126">Maschera dimensioni (esadecimale)</span><span class="sxs-lookup"><span data-stu-id="b1326-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="b1326-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="b1326-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="b1326-128">7</span><span class="sxs-lookup"><span data-stu-id="b1326-128">7</span></span>|<span data-ttu-id="b1326-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="b1326-129">&H00000007</span></span>|  
|<span data-ttu-id="b1326-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="b1326-130">`Short`, `UShort`</span></span>|<span data-ttu-id="b1326-131">15</span><span class="sxs-lookup"><span data-stu-id="b1326-131">15</span></span>|<span data-ttu-id="b1326-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="b1326-132">&H0000000F</span></span>|  
|<span data-ttu-id="b1326-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="b1326-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="b1326-134">31</span><span class="sxs-lookup"><span data-stu-id="b1326-134">31</span></span>|<span data-ttu-id="b1326-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="b1326-135">&H0000001F</span></span>|  
|<span data-ttu-id="b1326-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="b1326-136">`Long`, `ULong`</span></span>|<span data-ttu-id="b1326-137">63</span><span class="sxs-lookup"><span data-stu-id="b1326-137">63</span></span>|<span data-ttu-id="b1326-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="b1326-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="b1326-139">Se `amount` è uguale a zero, il valore di `result` è identico al valore di `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b1326-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="b1326-140">Se `amount` è negativo, viene considerato come un valore senza segno e mascherato con la maschera di dimensioni appropriata.</span><span class="sxs-lookup"><span data-stu-id="b1326-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="b1326-141">I turni aritmetici non generano mai eccezioni di overflow.</span><span class="sxs-lookup"><span data-stu-id="b1326-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1326-142">L'operatore `<<` può essere sottoposto a *Overload*, il che significa che una classe o una struttura può ridefinire il comportamento quando un operando ha il tipo della classe o della struttura.</span><span class="sxs-lookup"><span data-stu-id="b1326-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b1326-143">Se il codice usa questo operatore su una classe o una struttura di questo tipo, assicurarsi di comprendere il comportamento ridefinito.</span><span class="sxs-lookup"><span data-stu-id="b1326-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="b1326-144">Per altre informazioni, vedere [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b1326-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1326-145">Esempio</span><span class="sxs-lookup"><span data-stu-id="b1326-145">Example</span></span>  
 <span data-ttu-id="b1326-146">Nell'esempio seguente viene usato l'operatore `<<` per eseguire turni aritmetici a sinistra sui valori integrali.</span><span class="sxs-lookup"><span data-stu-id="b1326-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="b1326-147">Il risultato ha sempre lo stesso tipo di dati dell'espressione spostata.</span><span class="sxs-lookup"><span data-stu-id="b1326-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="b1326-148">I risultati dell'esempio precedente sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1326-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="b1326-149">`result1` è 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="b1326-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="b1326-150">`result2` è 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b1326-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="b1326-151">`result3` è-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b1326-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="b1326-152">`result4` è 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="b1326-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="b1326-153">`result5` è 0 (spostato di 15 posizioni a sinistra).</span><span class="sxs-lookup"><span data-stu-id="b1326-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="b1326-154">Il valore di Shift per `result4` viene calcolato come 17 e 15, che è uguale a 1.</span><span class="sxs-lookup"><span data-stu-id="b1326-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1326-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b1326-155">See also</span></span>

- [<span data-ttu-id="b1326-156">Operatori di spostamento bit</span><span class="sxs-lookup"><span data-stu-id="b1326-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="b1326-157">Operatori di assegnazione</span><span class="sxs-lookup"><span data-stu-id="b1326-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="b1326-158">Operatore <<=</span><span class="sxs-lookup"><span data-stu-id="b1326-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="b1326-159">Precedenza tra gli operatori in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1326-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b1326-160">Elenco degli operatori per funzionalità</span><span class="sxs-lookup"><span data-stu-id="b1326-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b1326-161">Operatori aritmetici in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1326-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
