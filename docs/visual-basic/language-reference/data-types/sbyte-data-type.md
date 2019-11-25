---
title: Tipo di dati SByte
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343941"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="46290-102">SByte data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46290-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="46290-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span><span class="sxs-lookup"><span data-stu-id="46290-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="46290-104">Note</span><span class="sxs-lookup"><span data-stu-id="46290-104">Remarks</span></span>

<span data-ttu-id="46290-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span><span class="sxs-lookup"><span data-stu-id="46290-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="46290-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span><span class="sxs-lookup"><span data-stu-id="46290-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="46290-107">Il valore predefinito di `SByte` è 0.</span><span class="sxs-lookup"><span data-stu-id="46290-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="46290-108">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="46290-108">Literal assignments</span></span>

<span data-ttu-id="46290-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="46290-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="46290-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span><span class="sxs-lookup"><span data-stu-id="46290-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="46290-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span><span class="sxs-lookup"><span data-stu-id="46290-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="46290-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="46290-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="46290-113">I valori letterali decimali non hanno prefissi.</span><span class="sxs-lookup"><span data-stu-id="46290-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="46290-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="46290-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="46290-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="46290-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="46290-116">Esempio:</span><span class="sxs-lookup"><span data-stu-id="46290-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="46290-117">Se il valore letterale integer è esterno all'intervallo di `SByte`, vale a dire se è minore di <xref:System.SByte.MinValue?displayProperty=nameWithType> o maggiore di <xref:System.SByte.MaxValue?displayProperty=nameWithType>, si verifica un errore di compilazione.</span><span class="sxs-lookup"><span data-stu-id="46290-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="46290-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span><span class="sxs-lookup"><span data-stu-id="46290-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="46290-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span><span class="sxs-lookup"><span data-stu-id="46290-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="46290-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46290-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="46290-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span><span class="sxs-lookup"><span data-stu-id="46290-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="46290-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span><span class="sxs-lookup"><span data-stu-id="46290-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="46290-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span><span class="sxs-lookup"><span data-stu-id="46290-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="46290-124">The following example assigns a negative literal `Short` value to an `SByte`.</span><span class="sxs-lookup"><span data-stu-id="46290-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="46290-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span><span class="sxs-lookup"><span data-stu-id="46290-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="46290-126">In the case of our example, this is bit 15 of the literal `Short` value.</span><span class="sxs-lookup"><span data-stu-id="46290-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="46290-127">Suggerimenti per la programmazione</span><span class="sxs-lookup"><span data-stu-id="46290-127">Programming tips</span></span>

- <span data-ttu-id="46290-128">**CLS Compliance.**</span><span class="sxs-lookup"><span data-stu-id="46290-128">**CLS Compliance.**</span></span> <span data-ttu-id="46290-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span><span class="sxs-lookup"><span data-stu-id="46290-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="46290-130">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="46290-130">**Widening.**</span></span> <span data-ttu-id="46290-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="46290-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="46290-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="46290-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="46290-133">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="46290-133">**Type Characters.**</span></span> <span data-ttu-id="46290-134">`SByte` has no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="46290-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="46290-135">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="46290-135">**Framework Type.**</span></span> <span data-ttu-id="46290-136">Il tipo corrispondente in .NET Framework è la struttura <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46290-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="46290-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46290-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="46290-138">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="46290-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="46290-139">Funzioni di conversione del tipo</span><span class="sxs-lookup"><span data-stu-id="46290-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="46290-140">Riepilogo della conversione</span><span class="sxs-lookup"><span data-stu-id="46290-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="46290-141">Tipo di dati Short</span><span class="sxs-lookup"><span data-stu-id="46290-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="46290-142">Tipo di dati Integer</span><span class="sxs-lookup"><span data-stu-id="46290-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="46290-143">Tipo di dati Long</span><span class="sxs-lookup"><span data-stu-id="46290-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="46290-144">Uso efficiente dei tipi di dati</span><span class="sxs-lookup"><span data-stu-id="46290-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
