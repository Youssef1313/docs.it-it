---
title: Tipi di dati compositi
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 1c099c5082f1c4173a50c70998c99135c94821e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346380"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="99a8d-102">Tipi di dati compositi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99a8d-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="99a8d-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span><span class="sxs-lookup"><span data-stu-id="99a8d-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="99a8d-104">You can build composite data types from elementary types and from other composite types.</span><span class="sxs-lookup"><span data-stu-id="99a8d-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="99a8d-105">For example, you can define an array of structure elements, or a structure with array members.</span><span class="sxs-lookup"><span data-stu-id="99a8d-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="99a8d-106">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="99a8d-106">Data Types</span></span>  
 <span data-ttu-id="99a8d-107">A composite type is different from the data type of any of its components.</span><span class="sxs-lookup"><span data-stu-id="99a8d-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="99a8d-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span><span class="sxs-lookup"><span data-stu-id="99a8d-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="99a8d-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span><span class="sxs-lookup"><span data-stu-id="99a8d-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="99a8d-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="99a8d-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="99a8d-111">Structure Types</span><span class="sxs-lookup"><span data-stu-id="99a8d-111">Structure Types</span></span>  
 <span data-ttu-id="99a8d-112">There is no single data type comprising all structures.</span><span class="sxs-lookup"><span data-stu-id="99a8d-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="99a8d-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span><span class="sxs-lookup"><span data-stu-id="99a8d-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="99a8d-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span><span class="sxs-lookup"><span data-stu-id="99a8d-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="99a8d-115">Tuple</span><span class="sxs-lookup"><span data-stu-id="99a8d-115">Tuples</span></span>

<span data-ttu-id="99a8d-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span><span class="sxs-lookup"><span data-stu-id="99a8d-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="99a8d-117">Tuples are supported starting with Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="99a8d-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="99a8d-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span><span class="sxs-lookup"><span data-stu-id="99a8d-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="99a8d-119">See the [Tuples](tuples.md) topic for more information on tuples.</span><span class="sxs-lookup"><span data-stu-id="99a8d-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="99a8d-120">Array Types</span><span class="sxs-lookup"><span data-stu-id="99a8d-120">Array Types</span></span>  
 <span data-ttu-id="99a8d-121">There is no single data type comprising all arrays.</span><span class="sxs-lookup"><span data-stu-id="99a8d-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="99a8d-122">The data type of a particular instance of an array is determined by the following:</span><span class="sxs-lookup"><span data-stu-id="99a8d-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="99a8d-123">The fact of being an array</span><span class="sxs-lookup"><span data-stu-id="99a8d-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="99a8d-124">The rank (number of dimensions) of the array</span><span class="sxs-lookup"><span data-stu-id="99a8d-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="99a8d-125">The element type of the array</span><span class="sxs-lookup"><span data-stu-id="99a8d-125">The element type of the array</span></span>  
  
 <span data-ttu-id="99a8d-126">In particular, the length of a given dimension is not part of the instance's data type.</span><span class="sxs-lookup"><span data-stu-id="99a8d-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="99a8d-127">Questa condizione è illustrata nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="99a8d-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="99a8d-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span><span class="sxs-lookup"><span data-stu-id="99a8d-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="99a8d-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span><span class="sxs-lookup"><span data-stu-id="99a8d-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="99a8d-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span><span class="sxs-lookup"><span data-stu-id="99a8d-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="99a8d-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span><span class="sxs-lookup"><span data-stu-id="99a8d-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="99a8d-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="99a8d-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="99a8d-133">Tipi di classe</span><span class="sxs-lookup"><span data-stu-id="99a8d-133">Class Types</span></span>  
 <span data-ttu-id="99a8d-134">There is no single data type comprising all classes.</span><span class="sxs-lookup"><span data-stu-id="99a8d-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="99a8d-135">Although one class can inherit from another class, each is a separate data type.</span><span class="sxs-lookup"><span data-stu-id="99a8d-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="99a8d-136">Multiple instances of the same class are of the same data type.</span><span class="sxs-lookup"><span data-stu-id="99a8d-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="99a8d-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span><span class="sxs-lookup"><span data-stu-id="99a8d-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="99a8d-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="99a8d-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a8d-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="99a8d-139">See also</span></span>

- [<span data-ttu-id="99a8d-140">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="99a8d-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="99a8d-141">Tipi di dati elementari</span><span class="sxs-lookup"><span data-stu-id="99a8d-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="99a8d-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99a8d-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="99a8d-143">Tipi valore e tipi di riferimento</span><span class="sxs-lookup"><span data-stu-id="99a8d-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="99a8d-144">Type Conversions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99a8d-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="99a8d-145">Strutture</span><span class="sxs-lookup"><span data-stu-id="99a8d-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="99a8d-146">Risoluzione dei problemi relativi ai tipi di dati</span><span class="sxs-lookup"><span data-stu-id="99a8d-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="99a8d-147">Procedura: Inserire più valori in una variabile</span><span class="sxs-lookup"><span data-stu-id="99a8d-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
