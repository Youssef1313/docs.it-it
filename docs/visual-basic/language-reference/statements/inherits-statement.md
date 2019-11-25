---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353231"
---
# <a name="inherits-statement"></a><span data-ttu-id="58c45-102">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="58c45-102">Inherits Statement</span></span>
<span data-ttu-id="58c45-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span><span class="sxs-lookup"><span data-stu-id="58c45-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c45-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="58c45-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="58c45-105">Parti</span><span class="sxs-lookup"><span data-stu-id="58c45-105">Parts</span></span>  
  
|<span data-ttu-id="58c45-106">Termine</span><span class="sxs-lookup"><span data-stu-id="58c45-106">Term</span></span>|<span data-ttu-id="58c45-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="58c45-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="58c45-108">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="58c45-108">Required.</span></span> <span data-ttu-id="58c45-109">The name of the class from which this class derives.</span><span class="sxs-lookup"><span data-stu-id="58c45-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="58c45-110">oppure</span><span class="sxs-lookup"><span data-stu-id="58c45-110">-or-</span></span><br /><br /> <span data-ttu-id="58c45-111">The names of the interfaces from which this interface derives.</span><span class="sxs-lookup"><span data-stu-id="58c45-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="58c45-112">Use commas to separate multiple names.</span><span class="sxs-lookup"><span data-stu-id="58c45-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58c45-113">Note</span><span class="sxs-lookup"><span data-stu-id="58c45-113">Remarks</span></span>  
 <span data-ttu-id="58c45-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span><span class="sxs-lookup"><span data-stu-id="58c45-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="58c45-115">It should immediately follow the `Class` or `Interface` statement.</span><span class="sxs-lookup"><span data-stu-id="58c45-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="58c45-116">You can use `Inherits` only in a class or interface.</span><span class="sxs-lookup"><span data-stu-id="58c45-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="58c45-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="58c45-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="58c45-118">Regole</span><span class="sxs-lookup"><span data-stu-id="58c45-118">Rules</span></span>  
  
- <span data-ttu-id="58c45-119">**Class Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="58c45-119">**Class Inheritance.**</span></span> <span data-ttu-id="58c45-120">If a class uses the `Inherits` statement, you can specify only one base class.</span><span class="sxs-lookup"><span data-stu-id="58c45-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="58c45-121">A class cannot inherit from a class nested within it.</span><span class="sxs-lookup"><span data-stu-id="58c45-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="58c45-122">**Interface Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="58c45-122">**Interface Inheritance.**</span></span> <span data-ttu-id="58c45-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span><span class="sxs-lookup"><span data-stu-id="58c45-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="58c45-124">You can inherit from two interfaces even if they each define a member with the same name.</span><span class="sxs-lookup"><span data-stu-id="58c45-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="58c45-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span><span class="sxs-lookup"><span data-stu-id="58c45-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="58c45-126">An interface cannot inherit from another interface with a more restrictive access level.</span><span class="sxs-lookup"><span data-stu-id="58c45-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="58c45-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span><span class="sxs-lookup"><span data-stu-id="58c45-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="58c45-128">An interface cannot inherit from an interface nested within it.</span><span class="sxs-lookup"><span data-stu-id="58c45-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="58c45-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span><span class="sxs-lookup"><span data-stu-id="58c45-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="58c45-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span><span class="sxs-lookup"><span data-stu-id="58c45-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="58c45-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="58c45-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="58c45-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span><span class="sxs-lookup"><span data-stu-id="58c45-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58c45-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="58c45-133">Example</span></span>  
 <span data-ttu-id="58c45-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="58c45-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="58c45-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="58c45-135">Example</span></span>  
 <span data-ttu-id="58c45-136">The following example shows inheritance of multiple interfaces.</span><span class="sxs-lookup"><span data-stu-id="58c45-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="58c45-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span><span class="sxs-lookup"><span data-stu-id="58c45-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="58c45-138">A class that implements `thisInterface` must implement every member of every base interface.</span><span class="sxs-lookup"><span data-stu-id="58c45-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c45-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="58c45-139">See also</span></span>

- [<span data-ttu-id="58c45-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="58c45-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="58c45-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="58c45-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="58c45-142">Oggetti e classi</span><span class="sxs-lookup"><span data-stu-id="58c45-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="58c45-143">Nozioni fondamentali sull'ereditarietà</span><span class="sxs-lookup"><span data-stu-id="58c45-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="58c45-144">Interfacce</span><span class="sxs-lookup"><span data-stu-id="58c45-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
