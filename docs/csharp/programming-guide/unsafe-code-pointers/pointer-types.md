---
title: Tipi di puntatori - Guida per programmatori C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 59846affb1eea5bd9d6a80c623eab5e3aa9db87c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661078"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="1a0c4-102">Tipi di puntatori (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="1a0c4-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="1a0c4-103">In un contesto unsafe, un tipo può essere un tipo di puntatore, un tipo di valore o un tipo di riferimento.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="1a0c4-104">La dichiarazione di un tipo di puntatore può assumere uno dei seguenti formati:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="1a0c4-105">Il tipo specificato prima di `*` in un tipo di puntatore viene chiamato **tipo referente**.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="1a0c4-106">I tipi seguenti possono essere tipi referenti:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="1a0c4-107">Qualsiasi tipo integrale: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-107">Any integral type: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="1a0c4-108">Qualsiasi tipo a virgola mobile: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-108">Any floating-point type: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="1a0c4-109">[char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="1a0c4-110">[bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="1a0c4-111">[decimal](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-111">[decimal](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="1a0c4-112">Qualsiasi tipo [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="1a0c4-113">Qualsiasi tipo di puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-113">Any pointer type.</span></span> <span data-ttu-id="1a0c4-114">Ciò consente l'utilizzo di espressioni come `void**`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="1a0c4-115">Qualsiasi tipo struct definito dall'utente che contenga campi solo di tipi non gestiti.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="1a0c4-116">I tipi di puntatore non ereditano da [object](../../language-reference/keywords/object.md). Non sono inoltre previste conversioni tra i tipi di puntatore e `object`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="1a0c4-117">Con i puntatori non sono inoltre supportate le operazioni di boxing e unboxing.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="1a0c4-118">È tuttavia possibile eseguire conversioni tra tipi di puntatore diversi e tra tipi di puntatore e tipi integrali.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="1a0c4-119">Quando si dichiarano più puntatori nella stessa dichiarazione, l'asterisco (\*) viene scritto solo con il tipo sottostante. Non viene utilizzato come prefisso di ogni nome di puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="1a0c4-120">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="1a0c4-121">Un puntatore non può puntare a un riferimento o a uno [struct](../../language-reference/keywords/struct.md) che contiene riferimenti, perché un riferimento a un oggetto può essere sottoposto a processi di Garbage Collection anche se un puntatore punta a esso.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="1a0c4-122">Il Garbage Collector non tiene traccia degli altri tipi di puntatore che puntano all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="1a0c4-123">Il valore della variabile del puntatore di tipo `myType*` è l'indirizzo di una variabile di tipo `myType`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="1a0c4-124">Di seguito sono riportati alcuni esempi di dichiarazioni di tipi di puntatore:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="1a0c4-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="1a0c4-125">Example</span></span>|<span data-ttu-id="1a0c4-126">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="1a0c4-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="1a0c4-127">`p` è un puntatore a un Integer.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="1a0c4-128">`p` è un puntatore a un puntatore a un Integer.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="1a0c4-129">`p` è una matrice unidimensionale di puntatori a Integer.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="1a0c4-130">`p` è un puntatore a un carattere.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="1a0c4-131">`p` è un puntatore a un tipo sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="1a0c4-132">Per accedere al contenuto nella posizione a cui punta la variabile del puntatore, è possibile utilizzare \*, ovvero l'operatore di riferimento indiretto a puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="1a0c4-133">Si consideri ad esempio la seguente dichiarazione:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="1a0c4-134">L'espressione `*myVariable` indica la variabile `int` individuata all'indirizzo contenuto in `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="1a0c4-135">Gli argomenti [Istruzione fixed](../../language-reference/keywords/fixed-statement.md) e [Conversioni di puntatori](../../programming-guide/unsafe-code-pointers/pointer-conversions.md) includono diversi esempi di puntatori.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="1a0c4-136">L'esempio seguente usa la parola chiave `unsafe` e l'istruzione `fixed` e mostra come incrementare un puntatore interno.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="1a0c4-137">È possibile incollare il codice nella funzione Main di un'applicazione console per eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="1a0c4-138">Questi esempi devono essere compilati con il set di opzioni del compilatore [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="1a0c4-139">Non è possibile applicare l'operatore di riferimento indiretto a un puntatore di tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="1a0c4-140">È tuttavia possibile eseguire un cast per convertire un puntatore void in qualsiasi altro tipo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="1a0c4-141">Un puntatore può essere `null`.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-141">A pointer can be `null`.</span></span> <span data-ttu-id="1a0c4-142">Se l'operatore di riferimento indiretto viene applicato a un puntatore Null, si otterrà un comportamento definito dall'implementazione.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="1a0c4-143">Tenere presente che il passaggio di puntatori tra metodi può generare un comportamento non definito.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="1a0c4-144">Prendere in considerazione un metodo che restituisce un puntatore a una variabile locale tramite un parametro `in`, `out` o `ref` oppure come risultato della funzione.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="1a0c4-145">Se il puntatore è stato impostato in un blocco fisso, la variabile a cui punta potrebbe non essere più fissa.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="1a0c4-146">Nella tabella riportata di seguito sono elencati gli operatori e le istruzioni che è possibile utilizzare con i puntatori in un contesto unsafe:</span><span class="sxs-lookup"><span data-stu-id="1a0c4-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="1a0c4-147">Operatore/istruzione</span><span class="sxs-lookup"><span data-stu-id="1a0c4-147">Operator/Statement</span></span>|<span data-ttu-id="1a0c4-148">Usa</span><span class="sxs-lookup"><span data-stu-id="1a0c4-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="1a0c4-149">Esegue il riferimento indiretto al puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="1a0c4-150">Accede a un membro di struct tramite un puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="1a0c4-151">Indicizza un puntatore.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="1a0c4-152">Ottiene l'indirizzo di una variabile.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="1a0c4-153">`++` e `--`</span><span class="sxs-lookup"><span data-stu-id="1a0c4-153">`++` and `--`</span></span>|<span data-ttu-id="1a0c4-154">Incrementa e decrementa puntatori.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="1a0c4-155">`+` e `-`</span><span class="sxs-lookup"><span data-stu-id="1a0c4-155">`+` and `-`</span></span>|<span data-ttu-id="1a0c4-156">Utilizza l'aritmetica dei puntatori.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="1a0c4-157">`==`, `!=`, `<`, `>`, `<=` e `>=`</span><span class="sxs-lookup"><span data-stu-id="1a0c4-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="1a0c4-158">Confronta puntatori.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-158">Compares pointers.</span></span>|
|[<span data-ttu-id="1a0c4-159">Operatore `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="1a0c4-159">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="1a0c4-160">Alloca memoria nello stack.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="1a0c4-161">Istruzione `fixed`</span><span class="sxs-lookup"><span data-stu-id="1a0c4-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="1a0c4-162">Corregge temporaneamente una variabile per consentire di trovarne l'indirizzo.</span><span class="sxs-lookup"><span data-stu-id="1a0c4-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="1a0c4-163">Per altre informazioni sugli operatori correlati ai puntatori, vedere [Operatori correlati ai puntatori](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1a0c4-164">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="1a0c4-164">C# language specification</span></span>

<span data-ttu-id="1a0c4-165">Per altre informazioni, vedere la sezione [Tipi puntatore](~/_csharplang/spec/unsafe-code.md#pointer-types) nella [specifica del linguaggio C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1a0c4-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a0c4-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a0c4-166">See also</span></span>

- [<span data-ttu-id="1a0c4-167">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="1a0c4-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a0c4-168">Codice unsafe e puntatori</span><span class="sxs-lookup"><span data-stu-id="1a0c4-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="1a0c4-169">Conversioni puntatore</span><span class="sxs-lookup"><span data-stu-id="1a0c4-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="1a0c4-170">Tipi</span><span class="sxs-lookup"><span data-stu-id="1a0c4-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="1a0c4-171">unsafe</span><span class="sxs-lookup"><span data-stu-id="1a0c4-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
