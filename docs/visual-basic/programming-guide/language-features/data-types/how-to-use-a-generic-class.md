---
title: 'Procedura: utilizzare una classe generica'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350052"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="ab96e-102">Procedura: utilizzare una classe generica (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab96e-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="ab96e-103">Una classe che accetta *parametri di tipo* è chiamato *classe generica*.</span><span class="sxs-lookup"><span data-stu-id="ab96e-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="ab96e-104">Se si usa una classe generica, è possibile generare una *classe costruita* da essa fornendo un *argomento di tipo* per ciascuno di questi parametri.</span><span class="sxs-lookup"><span data-stu-id="ab96e-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="ab96e-105">È possibile quindi dichiarare una variabile del tipo di classe costruita, creare un'istanza della classe costruita e assegnarla alla variabile.</span><span class="sxs-lookup"><span data-stu-id="ab96e-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="ab96e-106">Oltre alle classi, è possibile definire e usare anche strutture, interfacce, routine e delegati generici.</span><span class="sxs-lookup"><span data-stu-id="ab96e-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="ab96e-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span><span class="sxs-lookup"><span data-stu-id="ab96e-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="ab96e-108">Per usare una classe che accetta un parametro di tipo</span><span class="sxs-lookup"><span data-stu-id="ab96e-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="ab96e-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="ab96e-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ab96e-110">In questo modo è possibile fare riferimento alla classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> senza doverla specificare completamente per differenziarla da altre classi queue come <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab96e-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="ab96e-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span><span class="sxs-lookup"><span data-stu-id="ab96e-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="ab96e-112">L'esempio seguente usa la stessa classe (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) per creare due oggetti queue che contengono elementi con tipi di dati diversi.</span><span class="sxs-lookup"><span data-stu-id="ab96e-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="ab96e-113">Aggiunge gli elementi alla fine di ogni coda e quindi rimuove e visualizza gli elementi dall'inizio di ogni coda.</span><span class="sxs-lookup"><span data-stu-id="ab96e-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ab96e-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab96e-114">See also</span></span>

- [<span data-ttu-id="ab96e-115">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="ab96e-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="ab96e-116">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab96e-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ab96e-117">Indipendenza del linguaggio e componenti indipendenti dal linguaggio</span><span class="sxs-lookup"><span data-stu-id="ab96e-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="ab96e-118">Of</span><span class="sxs-lookup"><span data-stu-id="ab96e-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="ab96e-119">Istruzione Imports (tipo e spazio dei nomi .NET)</span><span class="sxs-lookup"><span data-stu-id="ab96e-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="ab96e-120">Procedura: Definire una classe in grado di fornire funzionalità identiche con tipi di dati diversi</span><span class="sxs-lookup"><span data-stu-id="ab96e-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="ab96e-121">Iteratori</span><span class="sxs-lookup"><span data-stu-id="ab96e-121">Iterators</span></span>](../../../../visual-basic/programming-guide/concepts/iterators.md)
