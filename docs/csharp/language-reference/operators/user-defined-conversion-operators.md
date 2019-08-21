---
title: Operatori di conversione definiti dall'utente - Riferimenti per C#
description: Informazioni su come definire conversioni di tipi impliciti ed espliciti personalizzate in C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566668"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="5e6ad-103">Operatori di conversione definiti dall'utente (riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="5e6ad-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="5e6ad-104">Un tipo definito dall'utente può definire una conversione implicita o esplicita da o in un altro tipo.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="5e6ad-105">Le conversioni implicite non richiedono una sintassi specifica per essere richiamate e possono essere usate in diverse situazioni, ad esempio durante le chiamate di metodi e assegnazioni.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="5e6ad-106">Le conversioni implicite C# predefinite hanno sempre esito positivo e non generano mai un'eccezione o una perdita di informazioni.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="5e6ad-107">Anche le conversioni implicite definite dall'utente si devono comportare nello stesso modo.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="5e6ad-108">Se una conversione personalizzata può generare un'eccezione o una perdita di informazioni, è necessario definirla come conversione esplicita.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="5e6ad-109">Le conversioni definite dall'utente non vengono considerate dagli operatori [is](type-testing-and-cast.md#is-operator) e [as](type-testing-and-cast.md#as-operator).</span><span class="sxs-lookup"><span data-stu-id="5e6ad-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="5e6ad-110">Usare l'[operatore cast ()](type-testing-and-cast.md#cast-operator-) per richiamare una conversione esplicita definita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="5e6ad-111">Usare `operator` e `implicit` o le parole chiave `explicit` per definire rispettivamente una conversione implicita o esplicita.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="5e6ad-112">Il tipo che definisce una conversione deve essere un tipo di origine o un tipo di destinazione della conversione.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="5e6ad-113">È possibile definire una conversione tra due tipi definiti dall'utente in uno dei due tipi.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="5e6ad-114">L'esempio seguente illustra come definire una conversione implicita ed esplicita:</span><span class="sxs-lookup"><span data-stu-id="5e6ad-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="5e6ad-115">È anche possibile usare la parola chiave `operator` per eseguire l'overload di un operatore C# predefinito.</span><span class="sxs-lookup"><span data-stu-id="5e6ad-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="5e6ad-116">Per altre informazioni, vedere [Overload degli operatori](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ad-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e6ad-117">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="5e6ad-117">C# language specification</span></span>

<span data-ttu-id="5e6ad-118">Per altre informazioni, vedere le sezioni seguenti delle [specifiche del linguaggio C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5e6ad-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5e6ad-119">Operatori di conversione</span><span class="sxs-lookup"><span data-stu-id="5e6ad-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="5e6ad-120">Conversioni definite dall'utente</span><span class="sxs-lookup"><span data-stu-id="5e6ad-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="5e6ad-121">Conversioni implicite</span><span class="sxs-lookup"><span data-stu-id="5e6ad-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="5e6ad-122">Conversioni esplicite</span><span class="sxs-lookup"><span data-stu-id="5e6ad-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="5e6ad-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5e6ad-123">See also</span></span>

- [<span data-ttu-id="5e6ad-124">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="5e6ad-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5e6ad-125">Operatori C#</span><span class="sxs-lookup"><span data-stu-id="5e6ad-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="5e6ad-126">Overload degli operatori</span><span class="sxs-lookup"><span data-stu-id="5e6ad-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="5e6ad-127">Operatori di cast e di test del tipo</span><span class="sxs-lookup"><span data-stu-id="5e6ad-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="5e6ad-128">Esecuzione del cast e conversioni di tipi</span><span class="sxs-lookup"><span data-stu-id="5e6ad-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="5e6ad-129">Conversioni esplicite concatenate definite dall'utente in C#</span><span class="sxs-lookup"><span data-stu-id="5e6ad-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
