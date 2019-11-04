---
title: Risultati
description: Informazioni su come usare il F# tipo ' Result ' per semplificare la scrittura di codice a tolleranza di errore.
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424844"
---
# <a name="results"></a><span data-ttu-id="cace3-103">Risultati</span><span class="sxs-lookup"><span data-stu-id="cace3-103">Results</span></span>

<span data-ttu-id="cace3-104">A partire F# da 4,1, è disponibile un tipo di `Result<'T,'TFailure>` che è possibile usare per la scrittura di codice a tolleranza di errore che può essere composto.</span><span class="sxs-lookup"><span data-stu-id="cace3-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="cace3-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cace3-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="cace3-106">Note</span><span class="sxs-lookup"><span data-stu-id="cace3-106">Remarks</span></span>

<span data-ttu-id="cace3-107">Si noti che il tipo di risultato è un' [unione discriminata struct](discriminated-unions.md#struct-discriminated-unions), ovvero un'altra funzionalità F# introdotta in 4,1.</span><span class="sxs-lookup"><span data-stu-id="cace3-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="cace3-108">Qui viene applicata la semantica di uguaglianza strutturale.</span><span class="sxs-lookup"><span data-stu-id="cace3-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="cace3-109">Il tipo di `Result` viene in genere usato per la gestione di errori monadica, che è spesso detta [programmazione orientata](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) alle ferrovie F# all'interno della community.</span><span class="sxs-lookup"><span data-stu-id="cace3-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="cace3-110">Nell'esempio seguente viene illustrato questo approccio.</span><span class="sxs-lookup"><span data-stu-id="cace3-110">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="cace3-111">Come si può notare, è piuttosto semplice concatenare diverse funzioni di convalida se si impone che tutti restituiscano un `Result`.</span><span class="sxs-lookup"><span data-stu-id="cace3-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="cace3-112">In questo modo è possibile suddividere le funzionalità di questo tipo in parti più piccole, che sono componibili in quanto necessarie.</span><span class="sxs-lookup"><span data-stu-id="cace3-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="cace3-113">Questo ha anche il valore aggiunto per *applicare l'uso* di [criteri](pattern-matching.md) di ricerca alla fine di un ciclo di convalida, che a sua volta impone un livello superiore di correttezza del programma.</span><span class="sxs-lookup"><span data-stu-id="cace3-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="cace3-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cace3-114">See also</span></span>

- [<span data-ttu-id="cace3-115">Unioni discriminate</span><span class="sxs-lookup"><span data-stu-id="cace3-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="cace3-116">Criteri di ricerca</span><span class="sxs-lookup"><span data-stu-id="cace3-116">Pattern Matching</span></span>](pattern-matching.md)
