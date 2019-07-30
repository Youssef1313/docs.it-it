---
title: Abbreviazioni dei tipi
description: Informazioni sulle F# abbreviazioni di tipo per assegnare a un tipo un nome più significativo allo scopo di semplificare la lettura del codice.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630207"
---
# <a name="type-abbreviations"></a><span data-ttu-id="f60a1-103">Abbreviazioni dei tipi</span><span class="sxs-lookup"><span data-stu-id="f60a1-103">Type Abbreviations</span></span>

<span data-ttu-id="f60a1-104">Un'abbreviazione di *tipo* è un alias o un nome alternativo per un tipo.</span><span class="sxs-lookup"><span data-stu-id="f60a1-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="f60a1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f60a1-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="f60a1-106">Note</span><span class="sxs-lookup"><span data-stu-id="f60a1-106">Remarks</span></span>

<span data-ttu-id="f60a1-107">È possibile usare le abbreviazioni di tipo per assegnare a un tipo un nome più significativo, in modo da semplificare la lettura del codice.</span><span class="sxs-lookup"><span data-stu-id="f60a1-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="f60a1-108">È anche possibile usarli per creare un nome facile da usare per un tipo altrimenti complesso da scrivere. Inoltre, è possibile usare le abbreviazioni di tipo per semplificare la modifica di un tipo sottostante senza modificare tutto il codice che usa il tipo.</span><span class="sxs-lookup"><span data-stu-id="f60a1-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="f60a1-109">Di seguito è riportata un'abbreviazione di tipo semplice.</span><span class="sxs-lookup"><span data-stu-id="f60a1-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="f60a1-110">Per `public`impostazione predefinita, l'accessibilità delle abbreviazioni di tipo è.</span><span class="sxs-lookup"><span data-stu-id="f60a1-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="f60a1-111">Le abbreviazioni di tipo possono includere parametri generici, come nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="f60a1-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="f60a1-112">Nel codice precedente, `Transform` è un'abbreviazione di tipo che rappresenta una funzione che accetta un solo argomento di qualsiasi tipo e che restituisce un singolo valore dello stesso tipo.</span><span class="sxs-lookup"><span data-stu-id="f60a1-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="f60a1-113">Le abbreviazioni di tipo non vengono mantenute nel codice MSIL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f60a1-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="f60a1-114">Pertanto, quando si usa un F# assembly da un altro linguaggio .NET Framework, è necessario usare il nome del tipo sottostante per un'abbreviazione di tipo.</span><span class="sxs-lookup"><span data-stu-id="f60a1-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="f60a1-115">Le abbreviazioni di tipo possono essere usate anche in unità di misura.</span><span class="sxs-lookup"><span data-stu-id="f60a1-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="f60a1-116">Per ulteriori informazioni, vedere [unità di misura](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="f60a1-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f60a1-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f60a1-117">See also</span></span>

- [<span data-ttu-id="f60a1-118">Riferimenti per il linguaggio F#</span><span class="sxs-lookup"><span data-stu-id="f60a1-118">F# Language Reference</span></span>](index.md)
