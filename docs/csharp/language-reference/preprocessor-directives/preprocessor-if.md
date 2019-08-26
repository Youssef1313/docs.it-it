---
title: '#Direttiva del preprocessore if - Riferimenti per C#'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d0297094fbb8098b706cb8c6338fa123afc0753b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605691"
---
# <a name="if-c-reference"></a><span data-ttu-id="d0217-102">#if (Riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="d0217-102">#if (C# Reference)</span></span>

<span data-ttu-id="d0217-103">Quando il compilatore C# trova una direttiva `#if` seguita da una direttiva [#endif](preprocessor-endif.md), compila il codice tra tali direttive solo se il simbolo specificato è definito.</span><span class="sxs-lookup"><span data-stu-id="d0217-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="d0217-104">Diversamente da C e C++, non è possibile assegnare un valore numerico a un simbolo.</span><span class="sxs-lookup"><span data-stu-id="d0217-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="d0217-105">L'istruzione #if in C# è di tipo booleano e verifica solo se il simbolo è stato definito o meno.</span><span class="sxs-lookup"><span data-stu-id="d0217-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="d0217-106">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d0217-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="d0217-107">È possibile usare gli operatori [==](../operators/equality-operators.md#equality-operator-) (uguaglianza) e [!=](../operators/equality-operators.md#inequality-operator-) (disuguaglianza) solo per verificare se una condizione è [true](../keywords/true-literal.md) o [false](../keywords/false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="d0217-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="d0217-108">True significa che il simbolo è definito.</span><span class="sxs-lookup"><span data-stu-id="d0217-108">True means the symbol is defined.</span></span> <span data-ttu-id="d0217-109">L'istruzione `#if DEBUG` ha lo stesso significato di `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="d0217-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="d0217-110">È possibile usare gli operatori [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or) e [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="d0217-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="d0217-111">(not) per stabilire se sono stati definiti più simboli.</span><span class="sxs-lookup"><span data-stu-id="d0217-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="d0217-112">È anche possibile raggruppare simboli e operatori tra parentesi.</span><span class="sxs-lookup"><span data-stu-id="d0217-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0217-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d0217-113">Remarks</span></span>

<span data-ttu-id="d0217-114">`#if`, nsieme alle direttive [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) e [#undef](preprocessor-undef.md), consente di includere o escludere il codice in base all'esistenza di uno o più simboli.</span><span class="sxs-lookup"><span data-stu-id="d0217-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="d0217-115">Questo può essere utile quando si compila il codice per una build di debug o per una configurazione specifica.</span><span class="sxs-lookup"><span data-stu-id="d0217-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="d0217-116">Una direttiva condizionale che inizia con `#if` deve terminare in modo esplicito con una direttiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="d0217-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="d0217-117">`#define` consente di definire un simbolo.</span><span class="sxs-lookup"><span data-stu-id="d0217-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="d0217-118">Usando poi il simbolo come espressione passata alla direttiva `#if`, l'espressione restituisce `true`.</span><span class="sxs-lookup"><span data-stu-id="d0217-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="d0217-119">Un simbolo può anche essere definito tramite l'opzione del compilatore [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d0217-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d0217-120">Per rimuovere la definizione di un simbolo, è possibile usare [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="d0217-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="d0217-121">Un simbolo definito tramite `-define` o `#define` non provoca conflitti con una variabile avente lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="d0217-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="d0217-122">Il nome di una variabile, infatti, non può essere passato a una direttiva del preprocessore e un simbolo può essere valutato solo da una direttiva del preprocessore.</span><span class="sxs-lookup"><span data-stu-id="d0217-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="d0217-123">L'ambito di un simbolo creato con `#define` è il file in cui è stato definito.</span><span class="sxs-lookup"><span data-stu-id="d0217-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="d0217-124">Il sistema di compilazione è anche a conoscenza dei simboli del preprocessore predefiniti che rappresentano [framework di destinazione](../../../standard/frameworks.md) diversi.</span><span class="sxs-lookup"><span data-stu-id="d0217-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="d0217-125">Questi simboli sono utili durante la creazione di applicazioni destinata a più di un'implementazione o versione di .NET.</span><span class="sxs-lookup"><span data-stu-id="d0217-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="d0217-126">Altri simboli predefiniti includono le costanti DEBUG e TRACE.</span><span class="sxs-lookup"><span data-stu-id="d0217-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="d0217-127">È possibile sostituire i valori impostati per il progetto con `#define`.</span><span class="sxs-lookup"><span data-stu-id="d0217-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="d0217-128">Il simbolo DEBUG, ad esempio, viene impostato automaticamente a seconda delle proprietà di configurazione della build (modalità "Debug" o "Versione").</span><span class="sxs-lookup"><span data-stu-id="d0217-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="d0217-129">Esempi</span><span class="sxs-lookup"><span data-stu-id="d0217-129">Examples</span></span>

<span data-ttu-id="d0217-130">L'esempio seguente illustra come definire un simbolo MYTEST su un file e quindi testare i valori dei simboli MYTEST e DEBUG.</span><span class="sxs-lookup"><span data-stu-id="d0217-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="d0217-131">L'output di questo esempio dipende dal fatto che il progetto sia stato compilato con la modalità di configurazione Debug o Versione.</span><span class="sxs-lookup"><span data-stu-id="d0217-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="d0217-132">L'esempio seguente illustra come eseguire test per framework di destinazione diversi, in modo da poter usare le API più recenti quando possibile:</span><span class="sxs-lookup"><span data-stu-id="d0217-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="d0217-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0217-133">See also</span></span>

- [<span data-ttu-id="d0217-134">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="d0217-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0217-135">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="d0217-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0217-136">Direttive per il preprocessore C#</span><span class="sxs-lookup"><span data-stu-id="d0217-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="d0217-137">Procedura: Compilare in modo condizionale con traccia e debug</span><span class="sxs-lookup"><span data-stu-id="d0217-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
