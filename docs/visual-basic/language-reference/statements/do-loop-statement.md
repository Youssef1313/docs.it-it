---
title: Istruzione Do...Loop
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351248"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="7adca-102">Istruzione Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7adca-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="7adca-103">Ripete un blocco di istruzioni mentre una condizione `Boolean` viene `True` o finché la condizione non viene `True`.</span><span class="sxs-lookup"><span data-stu-id="7adca-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adca-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7adca-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="7adca-105">Parti</span><span class="sxs-lookup"><span data-stu-id="7adca-105">Parts</span></span>  
  
|<span data-ttu-id="7adca-106">Termine</span><span class="sxs-lookup"><span data-stu-id="7adca-106">Term</span></span>|<span data-ttu-id="7adca-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="7adca-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="7adca-108">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="7adca-108">Required.</span></span> <span data-ttu-id="7adca-109">Avvia la definizione del ciclo `Do`.</span><span class="sxs-lookup"><span data-stu-id="7adca-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="7adca-110">Obbligatorio a meno che non sia usato `Until`.</span><span class="sxs-lookup"><span data-stu-id="7adca-110">Required unless `Until` is used.</span></span> <span data-ttu-id="7adca-111">Ripetere il ciclo finché non viene `False``condition`.</span><span class="sxs-lookup"><span data-stu-id="7adca-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="7adca-112">Obbligatorio a meno che non sia usato `While`.</span><span class="sxs-lookup"><span data-stu-id="7adca-112">Required unless `While` is used.</span></span> <span data-ttu-id="7adca-113">Ripetere il ciclo finché non viene `True``condition`.</span><span class="sxs-lookup"><span data-stu-id="7adca-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="7adca-114">Facoltativa.</span><span class="sxs-lookup"><span data-stu-id="7adca-114">Optional.</span></span> <span data-ttu-id="7adca-115">espressione `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7adca-115">`Boolean` expression.</span></span> <span data-ttu-id="7adca-116">Se `condition` è `Nothing`, Visual Basic lo considera `False`.</span><span class="sxs-lookup"><span data-stu-id="7adca-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="7adca-117">Facoltativa.</span><span class="sxs-lookup"><span data-stu-id="7adca-117">Optional.</span></span> <span data-ttu-id="7adca-118">Una o più istruzioni che vengono ripetute durante o fino a quando `condition` viene `True`.</span><span class="sxs-lookup"><span data-stu-id="7adca-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="7adca-119">Facoltativa.</span><span class="sxs-lookup"><span data-stu-id="7adca-119">Optional.</span></span> <span data-ttu-id="7adca-120">Trasferisce il controllo all'iterazione successiva del ciclo `Do`.</span><span class="sxs-lookup"><span data-stu-id="7adca-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="7adca-121">Facoltativa.</span><span class="sxs-lookup"><span data-stu-id="7adca-121">Optional.</span></span> <span data-ttu-id="7adca-122">Trasferisce il controllo all'esterno del ciclo `Do`.</span><span class="sxs-lookup"><span data-stu-id="7adca-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="7adca-123">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="7adca-123">Required.</span></span> <span data-ttu-id="7adca-124">Termina la definizione del ciclo `Do`.</span><span class="sxs-lookup"><span data-stu-id="7adca-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7adca-125">Note</span><span class="sxs-lookup"><span data-stu-id="7adca-125">Remarks</span></span>  
 <span data-ttu-id="7adca-126">Utilizzare una struttura `Do...Loop` quando si desidera ripetere un set di istruzioni per un numero indefinito di volte, fino a quando non viene soddisfatta una condizione.</span><span class="sxs-lookup"><span data-stu-id="7adca-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="7adca-127">Se si desidera ripetere le istruzioni impostando il numero di volte, [per... L'istruzione successiva](../../../visual-basic/language-reference/statements/for-next-statement.md) è in genere una scelta migliore.</span><span class="sxs-lookup"><span data-stu-id="7adca-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="7adca-128">È possibile utilizzare `While` o `Until` per specificare `condition`, ma non entrambi.</span><span class="sxs-lookup"><span data-stu-id="7adca-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="7adca-129">È possibile testare `condition` solo una volta, sia all'inizio che alla fine del ciclo.</span><span class="sxs-lookup"><span data-stu-id="7adca-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="7adca-130">Se si testa `condition` all'inizio del ciclo (nell'istruzione `Do`), il ciclo potrebbe non essere eseguito neanche una volta.</span><span class="sxs-lookup"><span data-stu-id="7adca-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="7adca-131">Se si esegue il test alla fine del ciclo (nell'istruzione `Loop`), il ciclo viene sempre eseguito almeno una volta.</span><span class="sxs-lookup"><span data-stu-id="7adca-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="7adca-132">La condizione viene in genere generata da un confronto di due valori, ma può trattarsi di qualsiasi espressione che restituisce un valore [booleano di tipo di dati](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` o `False`).</span><span class="sxs-lookup"><span data-stu-id="7adca-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="7adca-133">Sono inclusi i valori di altri tipi di dati, ad esempio i tipi numerici, che sono stati convertiti in `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7adca-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="7adca-134">È possibile annidare `Do` cicli inserendo un ciclo all'interno di un altro.</span><span class="sxs-lookup"><span data-stu-id="7adca-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="7adca-135">È anche possibile annidare diversi tipi di strutture di controllo tra loro.</span><span class="sxs-lookup"><span data-stu-id="7adca-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="7adca-136">Per altre informazioni, vedere [strutture di controlli annidati](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="7adca-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7adca-137">La struttura di `Do...Loop` offre una maggiore flessibilità rispetto al [periodo di tempo... End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , perché consente di decidere se terminare il ciclo quando `condition` viene interrotto `True` o quando viene `True`to per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="7adca-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="7adca-138">Consente inoltre di testare `condition` all'inizio o alla fine del ciclo.</span><span class="sxs-lookup"><span data-stu-id="7adca-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="7adca-139">Esci da do</span><span class="sxs-lookup"><span data-stu-id="7adca-139">Exit Do</span></span>  
 <span data-ttu-id="7adca-140">L'istruzione [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) può fornire un metodo alternativo per uscire da un `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="7adca-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="7adca-141">`Exit Do` trasferisce immediatamente il controllo all'istruzione che segue l'istruzione `Loop`.</span><span class="sxs-lookup"><span data-stu-id="7adca-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="7adca-142">`Exit Do` viene spesso utilizzata dopo la valutazione di una determinata condizione, ad esempio in una struttura di `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="7adca-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="7adca-143">Potrebbe essere necessario uscire da un ciclo se viene rilevata una condizione che rende superfluo o Impossibile continuare l'iterazione, ad esempio un valore errato o una richiesta di terminazione.</span><span class="sxs-lookup"><span data-stu-id="7adca-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="7adca-144">Un utilizzo di `Exit Do` consiste nel verificare la presenza di una condizione che potrebbe causare un *ciclo infinito*, ovvero un ciclo che può eseguire un numero di volte elevato o infinito.</span><span class="sxs-lookup"><span data-stu-id="7adca-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="7adca-145">È possibile utilizzare `Exit Do` per eseguire l'escape del ciclo.</span><span class="sxs-lookup"><span data-stu-id="7adca-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="7adca-146">È possibile includere un numero qualsiasi di istruzioni di `Exit Do` in qualsiasi punto di un `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="7adca-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="7adca-147">Quando viene utilizzato all'interno di cicli di `Do` annidati, `Exit Do` trasferisce il controllo dal ciclo più interno al successivo livello di nidificazione.</span><span class="sxs-lookup"><span data-stu-id="7adca-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7adca-148">Esempio</span><span class="sxs-lookup"><span data-stu-id="7adca-148">Example</span></span>  
 <span data-ttu-id="7adca-149">Nell'esempio seguente, le istruzioni del ciclo continuano a essere eseguite fino a quando la variabile di `index` non è maggiore di 10.</span><span class="sxs-lookup"><span data-stu-id="7adca-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="7adca-150">La clausola `Until` si trova alla fine del ciclo.</span><span class="sxs-lookup"><span data-stu-id="7adca-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="7adca-151">Esempio</span><span class="sxs-lookup"><span data-stu-id="7adca-151">Example</span></span>  
 <span data-ttu-id="7adca-152">Nell'esempio seguente viene usata una clausola `While` anziché una clausola `Until` e `condition` viene testato all'inizio del ciclo anziché alla fine.</span><span class="sxs-lookup"><span data-stu-id="7adca-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="7adca-153">Esempio</span><span class="sxs-lookup"><span data-stu-id="7adca-153">Example</span></span>  
 <span data-ttu-id="7adca-154">Nell'esempio seguente `condition` interrompe il ciclo quando la variabile `index` è maggiore di 100.</span><span class="sxs-lookup"><span data-stu-id="7adca-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="7adca-155">L'istruzione `If` nel ciclo, tuttavia, causa l'arresto del ciclo da parte dell'istruzione `Exit Do` quando la variabile di indice è maggiore di 10.</span><span class="sxs-lookup"><span data-stu-id="7adca-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="7adca-156">Esempio</span><span class="sxs-lookup"><span data-stu-id="7adca-156">Example</span></span>  
 <span data-ttu-id="7adca-157">Nell'esempio seguente vengono lette tutte le righe in un file di testo.</span><span class="sxs-lookup"><span data-stu-id="7adca-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="7adca-158">Il metodo <xref:System.IO.File.OpenText%2A> apre il file e restituisce un <xref:System.IO.StreamReader> che legge i caratteri.</span><span class="sxs-lookup"><span data-stu-id="7adca-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="7adca-159">Nella condizione `Do...Loop` il <xref:System.IO.StreamReader.Peek%2A> metodo del `StreamReader` determina se sono presenti caratteri aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="7adca-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="7adca-160">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7adca-160">See also</span></span>

- [<span data-ttu-id="7adca-161">Strutture di ciclo</span><span class="sxs-lookup"><span data-stu-id="7adca-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="7adca-162">Istruzione For...Next</span><span class="sxs-lookup"><span data-stu-id="7adca-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="7adca-163">Tipo di dati Boolean</span><span class="sxs-lookup"><span data-stu-id="7adca-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="7adca-164">Strutture di controllo annidate</span><span class="sxs-lookup"><span data-stu-id="7adca-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7adca-165">Istruzione Exit</span><span class="sxs-lookup"><span data-stu-id="7adca-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="7adca-166">Istruzione While...End While</span><span class="sxs-lookup"><span data-stu-id="7adca-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
