---
title: Ambito in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512858"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="9d71a-102">Ambito in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d71a-102">Scope in Visual Basic</span></span>

<span data-ttu-id="9d71a-103">L' *ambito* di un elemento dichiarato è il set di tutto il codice che può farvi riferimento senza qualificarne il nome o renderlo disponibile tramite un' [istruzione Imports (tipo e spazio dei nomi .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="9d71a-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="9d71a-104">Un elemento può avere un ambito a uno dei livelli seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d71a-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="9d71a-105">Level</span><span class="sxs-lookup"><span data-stu-id="9d71a-105">Level</span></span>|<span data-ttu-id="9d71a-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9d71a-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="9d71a-107">Ambito blocco</span><span class="sxs-lookup"><span data-stu-id="9d71a-107">Block scope</span></span>|<span data-ttu-id="9d71a-108">Disponibile solo all'interno del blocco di codice in cui è dichiarata</span><span class="sxs-lookup"><span data-stu-id="9d71a-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="9d71a-109">Ambito procedura</span><span class="sxs-lookup"><span data-stu-id="9d71a-109">Procedure scope</span></span>|<span data-ttu-id="9d71a-110">Disponibile per tutto il codice all'interno della routine in cui è dichiarata</span><span class="sxs-lookup"><span data-stu-id="9d71a-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="9d71a-111">Ambito del modulo</span><span class="sxs-lookup"><span data-stu-id="9d71a-111">Module scope</span></span>|<span data-ttu-id="9d71a-112">Disponibile per tutto il codice all'interno del modulo, della classe o della struttura in cui è dichiarata</span><span class="sxs-lookup"><span data-stu-id="9d71a-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="9d71a-113">Ambito dello spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="9d71a-113">Namespace scope</span></span>|<span data-ttu-id="9d71a-114">Disponibile per tutto il codice nello spazio dei nomi in cui è dichiarato</span><span class="sxs-lookup"><span data-stu-id="9d71a-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="9d71a-115">Questi livelli di avanzamento dell'ambito dal più piccolo (blocco) al più ampio (spazio dei nomi), dove l' *ambito* più ristretto indica il set di codice più piccolo che può fare riferimento all'elemento senza qualifica.</span><span class="sxs-lookup"><span data-stu-id="9d71a-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="9d71a-116">Per ulteriori informazioni, vedere "livelli di ambito" in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="9d71a-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="9d71a-117">Specifica dell'ambito e definizione delle variabili</span><span class="sxs-lookup"><span data-stu-id="9d71a-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="9d71a-118">L'ambito di un elemento viene specificato quando lo si dichiara.</span><span class="sxs-lookup"><span data-stu-id="9d71a-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="9d71a-119">L'ambito può dipendere dai fattori seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d71a-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="9d71a-120">Area (Block, procedure, modulo, classe o struttura) in cui viene dichiarato l'elemento</span><span class="sxs-lookup"><span data-stu-id="9d71a-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="9d71a-121">Spazio dei nomi contenente la dichiarazione dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="9d71a-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="9d71a-122">Livello di accesso dichiarato per l'elemento</span><span class="sxs-lookup"><span data-stu-id="9d71a-122">The access level you declare for the element</span></span>

<span data-ttu-id="9d71a-123">Prestare attenzione quando si definiscono le variabili con lo stesso nome ma con un ambito diverso, perché questa operazione può causare risultati imprevisti.</span><span class="sxs-lookup"><span data-stu-id="9d71a-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="9d71a-124">Per altre informazioni, vedere [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="9d71a-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="9d71a-125">Livelli di ambito</span><span class="sxs-lookup"><span data-stu-id="9d71a-125">Levels of Scope</span></span>

<span data-ttu-id="9d71a-126">Un elemento di programmazione è disponibile nell'area geografica in cui viene dichiarata.</span><span class="sxs-lookup"><span data-stu-id="9d71a-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="9d71a-127">Tutto il codice nella stessa area può fare riferimento all'elemento senza qualificare il nome.</span><span class="sxs-lookup"><span data-stu-id="9d71a-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="9d71a-128">Ambito del blocco</span><span class="sxs-lookup"><span data-stu-id="9d71a-128">Block Scope</span></span>

<span data-ttu-id="9d71a-129">Un blocco è un set di istruzioni racchiuse tra istruzioni di inizializzazione e terminazione di dichiarazione, come le seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d71a-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="9d71a-130">`Do` e `Loop`</span><span class="sxs-lookup"><span data-stu-id="9d71a-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="9d71a-131">`For`[`Each`] e`Next`</span><span class="sxs-lookup"><span data-stu-id="9d71a-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="9d71a-132">`If` e `End If`</span><span class="sxs-lookup"><span data-stu-id="9d71a-132">`If` and `End If`</span></span>

- <span data-ttu-id="9d71a-133">`Select` e `End Select`</span><span class="sxs-lookup"><span data-stu-id="9d71a-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="9d71a-134">`SyncLock` e `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="9d71a-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="9d71a-135">`Try` e `End Try`</span><span class="sxs-lookup"><span data-stu-id="9d71a-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="9d71a-136">`While` e `End While`</span><span class="sxs-lookup"><span data-stu-id="9d71a-136">`While` and `End While`</span></span>

- <span data-ttu-id="9d71a-137">`With` e `End With`</span><span class="sxs-lookup"><span data-stu-id="9d71a-137">`With` and `End With`</span></span>

<span data-ttu-id="9d71a-138">Se si dichiara una variabile all'interno di un blocco, è possibile utilizzarla solo all'interno di tale blocco.</span><span class="sxs-lookup"><span data-stu-id="9d71a-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="9d71a-139">Nell'esempio seguente, l' `cube` ambito della variabile integer è il blocco tra `If` e `End If`e non è più possibile fare riferimento a `cube` quando l'esecuzione passa all'esterno del blocco.</span><span class="sxs-lookup"><span data-stu-id="9d71a-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="9d71a-140">Anche se l'ambito di una variabile è limitato a un blocco, la sua durata è ancora quella dell'intera procedura.</span><span class="sxs-lookup"><span data-stu-id="9d71a-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="9d71a-141">Se durante la procedura si immette più di una volta il blocco, ogni variabile di blocco mantiene il valore precedente.</span><span class="sxs-lookup"><span data-stu-id="9d71a-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="9d71a-142">Per evitare risultati imprevisti in tal caso, è consigliabile inizializzare le variabili di blocco all'inizio del blocco.</span><span class="sxs-lookup"><span data-stu-id="9d71a-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="9d71a-143">Ambito procedura</span><span class="sxs-lookup"><span data-stu-id="9d71a-143">Procedure Scope</span></span>

<span data-ttu-id="9d71a-144">Un elemento dichiarato all'interno di una routine non è disponibile all'esterno di tale procedura.</span><span class="sxs-lookup"><span data-stu-id="9d71a-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="9d71a-145">Solo la routine che contiene la dichiarazione può usarla.</span><span class="sxs-lookup"><span data-stu-id="9d71a-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="9d71a-146">Le variabili a questo livello sono note anche come *variabili locali*.</span><span class="sxs-lookup"><span data-stu-id="9d71a-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="9d71a-147">Vengono dichiarati con l' [istruzione Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), con o senza la parola chiave [static](../../../../visual-basic/language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="9d71a-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="9d71a-148">La procedura e l'ambito del blocco sono strettamente correlati.</span><span class="sxs-lookup"><span data-stu-id="9d71a-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="9d71a-149">Se si dichiara una variabile all'interno di una routine, ma all'esterno di qualsiasi blocco all'interno di tale procedura, è possibile considerare la variabile come avente un ambito di blocco, in cui il blocco è l'intera routine.</span><span class="sxs-lookup"><span data-stu-id="9d71a-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="9d71a-150">Tutti gli elementi locali, anche se sono `Static` variabili, sono privati della routine in cui vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="9d71a-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="9d71a-151">Non è possibile dichiarare alcun elemento utilizzando la parola chiave [public](../../../../visual-basic/language-reference/modifiers/public.md) all'interno di una routine.</span><span class="sxs-lookup"><span data-stu-id="9d71a-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="9d71a-152">Ambito del modulo</span><span class="sxs-lookup"><span data-stu-id="9d71a-152">Module Scope</span></span>

<span data-ttu-id="9d71a-153">Per praticità, il *livello del modulo* a singolo termine si applica ugualmente a moduli, classi e strutture.</span><span class="sxs-lookup"><span data-stu-id="9d71a-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="9d71a-154">È possibile dichiarare elementi a questo livello inserendo l'istruzione di dichiarazione all'esterno di qualsiasi routine o blocco, ma all'interno del modulo, della classe o della struttura.</span><span class="sxs-lookup"><span data-stu-id="9d71a-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="9d71a-155">Quando si crea una dichiarazione a livello di modulo, il livello di accesso scelto determina l'ambito.</span><span class="sxs-lookup"><span data-stu-id="9d71a-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="9d71a-156">Lo spazio dei nomi che contiene il modulo, la classe o la struttura influiscono anche sull'ambito.</span><span class="sxs-lookup"><span data-stu-id="9d71a-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="9d71a-157">Gli elementi per i quali si dichiara il livello di accesso [privato](../../../../visual-basic/language-reference/modifiers/private.md) sono disponibili per tutte le procedure del modulo, ma non per il codice in un modulo diverso.</span><span class="sxs-lookup"><span data-stu-id="9d71a-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="9d71a-158">L' `Dim` istruzione a livello di modulo viene utilizzata `Private` per impostazione predefinita se non si utilizzano parole chiave del livello di accesso.</span><span class="sxs-lookup"><span data-stu-id="9d71a-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="9d71a-159">Tuttavia, è possibile rendere più evidenti l'ambito e il livello di accesso `Private` utilizzando la parola `Dim` chiave nell'istruzione.</span><span class="sxs-lookup"><span data-stu-id="9d71a-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="9d71a-160">Nell'esempio seguente, tutte le routine definite nel modulo possono fare riferimento alla variabile `strMsg`di stringa.</span><span class="sxs-lookup"><span data-stu-id="9d71a-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="9d71a-161">Quando viene chiamata la seconda procedura, viene visualizzato il contenuto della variabile `strMsg` stringa in una finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="9d71a-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="9d71a-162">Ambito dello spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="9d71a-162">Namespace Scope</span></span>

<span data-ttu-id="9d71a-163">Se si dichiara un elemento a livello di modulo usando la parola chiave [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) o [public](../../../../visual-basic/language-reference/modifiers/public.md) , diventa disponibile per tutte le routine in tutto lo spazio dei nomi in cui viene dichiarato l'elemento.</span><span class="sxs-lookup"><span data-stu-id="9d71a-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="9d71a-164">Con la seguente modifica all'esempio precedente, è possibile fare riferimento `strMsg` alla variabile di stringa dal codice in qualsiasi punto dello spazio dei nomi della relativa dichiarazione.</span><span class="sxs-lookup"><span data-stu-id="9d71a-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="9d71a-165">Lo spazio dei nomi include spazi dei nomi annidati.</span><span class="sxs-lookup"><span data-stu-id="9d71a-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="9d71a-166">Un elemento disponibile in uno spazio dei nomi è disponibile anche all'interno di qualsiasi spazio dei nomi annidato all'interno di tale spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="9d71a-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="9d71a-167">Se il progetto non contiene alcuna [istruzione dello spazio dei nomi](../../../../visual-basic/language-reference/statements/namespace-statement.md), tutti gli elementi del progetto si trova nello stesso spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="9d71a-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="9d71a-168">In questo caso, l'ambito dello spazio dei nomi può essere considerato come ambito del progetto.</span><span class="sxs-lookup"><span data-stu-id="9d71a-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="9d71a-169">`Public`gli elementi in un modulo, una classe o una struttura sono disponibili anche per qualsiasi progetto che fa riferimento al progetto.</span><span class="sxs-lookup"><span data-stu-id="9d71a-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="9d71a-170">Scelta dell'ambito</span><span class="sxs-lookup"><span data-stu-id="9d71a-170">Choice of Scope</span></span>

<span data-ttu-id="9d71a-171">Quando si dichiara una variabile, è necessario tenere presenti i punti seguenti quando si sceglie l'ambito.</span><span class="sxs-lookup"><span data-stu-id="9d71a-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="9d71a-172">Vantaggi delle variabili locali</span><span class="sxs-lookup"><span data-stu-id="9d71a-172">Advantages of Local Variables</span></span>

<span data-ttu-id="9d71a-173">Le variabili locali rappresentano una scelta ottimale per qualsiasi tipo di calcolo temporaneo, per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="9d71a-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="9d71a-174">**Evitare conflitti di nomi.**</span><span class="sxs-lookup"><span data-stu-id="9d71a-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="9d71a-175">I nomi delle variabili locali non sono suscettibili ai conflitti.</span><span class="sxs-lookup"><span data-stu-id="9d71a-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="9d71a-176">È ad esempio possibile creare diverse procedure contenenti una variabile denominata `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="9d71a-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="9d71a-177">Fino a quando ogni `intTemp` routine viene dichiarata come variabile locale, ogni procedura riconosce solo la propria `intTemp`versione di.</span><span class="sxs-lookup"><span data-stu-id="9d71a-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="9d71a-178">Qualsiasi procedura può modificare il valore nel relativo oggetto locale `intTemp` senza `intTemp` influire sulle variabili in altre routine.</span><span class="sxs-lookup"><span data-stu-id="9d71a-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="9d71a-179">**Consumo di memoria.**</span><span class="sxs-lookup"><span data-stu-id="9d71a-179">**Memory Consumption.**</span></span> <span data-ttu-id="9d71a-180">Le variabili locali utilizzano la memoria solo mentre è in esecuzione la relativa procedura.</span><span class="sxs-lookup"><span data-stu-id="9d71a-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="9d71a-181">La memoria viene rilasciata quando la procedura viene restituita al codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="9d71a-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="9d71a-182">Al contrario, le variabili [condivise](../../../../visual-basic/language-reference/modifiers/shared.md) e [statiche](../../../../visual-basic/language-reference/modifiers/static.md) utilizzano risorse di memoria fino a quando l'applicazione non viene arrestata, quindi utilizzarle solo quando necessario.</span><span class="sxs-lookup"><span data-stu-id="9d71a-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="9d71a-183">Le *variabili di istanza* utilizzano la memoria mentre la loro istanza continua a esistere, rendendole meno efficienti rispetto alle variabili locali, `Shared` ma potenzialmente più efficienti delle variabili o. `Static`</span><span class="sxs-lookup"><span data-stu-id="9d71a-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="9d71a-184">Riduzione dell'ambito</span><span class="sxs-lookup"><span data-stu-id="9d71a-184">Minimizing Scope</span></span>

<span data-ttu-id="9d71a-185">In generale, quando si dichiara una variabile o una costante, è consigliabile fare in modo che l'ambito sia più stretto possibile (l'ambito del blocco è il più piccolo).</span><span class="sxs-lookup"><span data-stu-id="9d71a-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="9d71a-186">Questo consente di conservare la memoria e ridurre al minimo le probabilità che il codice faccia riferimento erroneamente alla variabile non corretta.</span><span class="sxs-lookup"><span data-stu-id="9d71a-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="9d71a-187">Analogamente, è consigliabile dichiarare una variabile come [statica](../../../../visual-basic/language-reference/modifiers/static.md) solo quando è necessario mantenerne il valore tra le chiamate di routine.</span><span class="sxs-lookup"><span data-stu-id="9d71a-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d71a-188">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9d71a-188">See also</span></span>

- [<span data-ttu-id="9d71a-189">Caratteristiche di elementi dichiarati</span><span class="sxs-lookup"><span data-stu-id="9d71a-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="9d71a-190">Procedura: Controllare l'ambito di una variabile</span><span class="sxs-lookup"><span data-stu-id="9d71a-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="9d71a-191">Durata in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d71a-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="9d71a-192">Livelli di accesso in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d71a-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="9d71a-193">Riferimenti a elementi dichiarati</span><span class="sxs-lookup"><span data-stu-id="9d71a-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="9d71a-194">Dichiarazione di variabile</span><span class="sxs-lookup"><span data-stu-id="9d71a-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
