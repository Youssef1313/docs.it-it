---
title: implicit - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 00fe1a02b52ef2ddc393bc7424efa73fc4059a9c
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610118"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="e2595-102">implicit (Riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="e2595-102">implicit (C# Reference)</span></span>

<span data-ttu-id="e2595-103">La parola chiave `implicit` viene usata per dichiarare un operatore di conversione implicita di tipi definito dall'utente.</span><span class="sxs-lookup"><span data-stu-id="e2595-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="e2595-104">È possibile usare questa parola chiave per abilitare le conversioni implicite tra un tipo definito dall'utente e un altro tipo, se è garantito che tale conversione non provoca una perdita di dati.</span><span class="sxs-lookup"><span data-stu-id="e2595-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>

## <a name="example"></a><span data-ttu-id="e2595-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="e2595-105">Example</span></span>

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

<span data-ttu-id="e2595-106">Grazie all'eliminazione dei cast non necessari, le conversioni implicite contribuiscono a migliorare la leggibilità del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="e2595-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="e2595-107">Tuttavia, poiché per le conversioni implicite non è necessario eseguire il cast in modo esplicito da un tipo all'altro, è importante assicurarsi di non ottenere risultati imprevisti.</span><span class="sxs-lookup"><span data-stu-id="e2595-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="e2595-108">In genere, per poter essere usati in modo sicuro senza il controllo del programmatore, gli operatori di conversione implicita non devono generare eccezioni né determinare perdite di dati.</span><span class="sxs-lookup"><span data-stu-id="e2595-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="e2595-109">Se un operatore di conversione non soddisfa questi requisiti, è opportuno contrassegnarlo come `explicit`.</span><span class="sxs-lookup"><span data-stu-id="e2595-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="e2595-110">Per altre informazioni, vedere [Uso degli operatori di conversione](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e2595-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2595-111">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="e2595-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e2595-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e2595-112">See also</span></span>

- [<span data-ttu-id="e2595-113">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="e2595-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2595-114">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="e2595-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2595-115">Parole chiave di C#</span><span class="sxs-lookup"><span data-stu-id="e2595-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e2595-116">explicit</span><span class="sxs-lookup"><span data-stu-id="e2595-116">explicit</span></span>](explicit.md)
- [<span data-ttu-id="e2595-117">Overload degli operatori</span><span class="sxs-lookup"><span data-stu-id="e2595-117">Operator overloading</span></span>](../operators/operator-overloading.md)
- [<span data-ttu-id="e2595-118">Procedura: Implementare conversioni tra struct definite dall'utente</span><span class="sxs-lookup"><span data-stu-id="e2595-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
