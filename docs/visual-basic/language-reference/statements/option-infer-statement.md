---
title: Option Infer (istruzione)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346489"
---
# <a name="option-infer-statement"></a><span data-ttu-id="2e49c-102">Option Infer (istruzione)</span><span class="sxs-lookup"><span data-stu-id="2e49c-102">Option Infer Statement</span></span>

<span data-ttu-id="2e49c-103">Abilita l'uso dell'inferenza del tipo di variabile locale nelle variabili dichiaranti.</span><span class="sxs-lookup"><span data-stu-id="2e49c-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e49c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2e49c-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="2e49c-105">Parti</span><span class="sxs-lookup"><span data-stu-id="2e49c-105">Parts</span></span>

|<span data-ttu-id="2e49c-106">Termine</span><span class="sxs-lookup"><span data-stu-id="2e49c-106">Term</span></span>|<span data-ttu-id="2e49c-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="2e49c-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="2e49c-108">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2e49c-108">Optional.</span></span> <span data-ttu-id="2e49c-109">Abilita l'inferenza del tipo di variabile locale.</span><span class="sxs-lookup"><span data-stu-id="2e49c-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="2e49c-110">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="2e49c-110">Optional.</span></span> <span data-ttu-id="2e49c-111">Disabilita l'inferenza del tipo di variabile locale.</span><span class="sxs-lookup"><span data-stu-id="2e49c-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e49c-112">Note</span><span class="sxs-lookup"><span data-stu-id="2e49c-112">Remarks</span></span>

<span data-ttu-id="2e49c-113">Per impostare `Option Infer` in un file, digitare `Option Infer On` oppure `Option Infer Off` all'inizio del file, prima di qualsiasi altro codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="2e49c-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="2e49c-114">Se il valore impostato per `Option Infer` in un file è in conflitto con il valore impostato nell'IDE o sulla riga di comando, il valore nel file ha precedenza.</span><span class="sxs-lookup"><span data-stu-id="2e49c-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="2e49c-115">Quando si imposta `Option Infer` su `On`, è possibile dichiarare variabili locali senza dichiarare in modo esplicito un tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="2e49c-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="2e49c-116">Tramite l'inferenza, il compilatore deriva il tipo di dati di una variabile dal tipo della relativa espressione di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="2e49c-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="2e49c-117">Nella figura seguente, l'istruzione `Option Infer` è abilitata.</span><span class="sxs-lookup"><span data-stu-id="2e49c-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="2e49c-118">La variabile nella dichiarazione `Dim someVar = 2` viene dichiarata come Integer in base all'inferenza del tipo.</span><span class="sxs-lookup"><span data-stu-id="2e49c-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="2e49c-119">The following screenshot shows IntelliSense when Option Infer is on:</span><span class="sxs-lookup"><span data-stu-id="2e49c-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="2e49c-121">Nella figura seguente, l'istruzione `Option Infer` è disabilitata.</span><span class="sxs-lookup"><span data-stu-id="2e49c-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="2e49c-122">La variabile nella dichiarazione `Dim someVar = 2` viene dichiarata come `Object` in base all'inferenza del tipo.</span><span class="sxs-lookup"><span data-stu-id="2e49c-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="2e49c-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2e49c-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="2e49c-124">The following screenshot shows IntelliSense when Option Infer is off:</span><span class="sxs-lookup"><span data-stu-id="2e49c-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="2e49c-126">Quando una variabile viene dichiarata come `Object`, il tipo di runtime può essere modificato mentre il programma è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="2e49c-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="2e49c-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span><span class="sxs-lookup"><span data-stu-id="2e49c-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="2e49c-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="2e49c-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="2e49c-129">L'inferenza del tipo si applica a livello di routine e non si applica all'esterno di una routine in una classe, una struttura, un modulo o un'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="2e49c-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="2e49c-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2e49c-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="2e49c-131">Quando non è presente un'istruzione Option Infer</span><span class="sxs-lookup"><span data-stu-id="2e49c-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="2e49c-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="2e49c-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="2e49c-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="2e49c-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="2e49c-134">Per impostare Option Infer nell'IDE</span><span class="sxs-lookup"><span data-stu-id="2e49c-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="2e49c-135">Selezionare un progetto in **Esplora soluzioni**.</span><span class="sxs-lookup"><span data-stu-id="2e49c-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="2e49c-136">Scegliere **Proprietà** dal menu **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="2e49c-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="2e49c-137">Fare clic sulla scheda **Compila**.</span><span class="sxs-lookup"><span data-stu-id="2e49c-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="2e49c-138">Set the value in the **Option infer** box.</span><span class="sxs-lookup"><span data-stu-id="2e49c-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="2e49c-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span><span class="sxs-lookup"><span data-stu-id="2e49c-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="2e49c-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="2e49c-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="2e49c-141">Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="2e49c-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="2e49c-142">The initial default setting in **VB Defaults** is `On`.</span><span class="sxs-lookup"><span data-stu-id="2e49c-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="2e49c-143">Per impostare Option Infer nella riga di comando</span><span class="sxs-lookup"><span data-stu-id="2e49c-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="2e49c-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="2e49c-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="2e49c-145">Tipi di dati e valori predefiniti</span><span class="sxs-lookup"><span data-stu-id="2e49c-145">Default Data Types and Values</span></span>

<span data-ttu-id="2e49c-146">Nella tabella seguente vengono descritti i risultati di varie combinazioni della specifica del tipo di dati e dell'inizializzatore in un'istruzione `Dim`.</span><span class="sxs-lookup"><span data-stu-id="2e49c-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="2e49c-147">Tipo di dati specificato?</span><span class="sxs-lookup"><span data-stu-id="2e49c-147">Data type specified?</span></span>|<span data-ttu-id="2e49c-148">Inizializzatore specificato?</span><span class="sxs-lookup"><span data-stu-id="2e49c-148">Initializer specified?</span></span>|<span data-ttu-id="2e49c-149">Esempio</span><span class="sxs-lookup"><span data-stu-id="2e49c-149">Example</span></span>|<span data-ttu-id="2e49c-150">Risultato</span><span class="sxs-lookup"><span data-stu-id="2e49c-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="2e49c-151">No</span><span class="sxs-lookup"><span data-stu-id="2e49c-151">No</span></span>|<span data-ttu-id="2e49c-152">No</span><span class="sxs-lookup"><span data-stu-id="2e49c-152">No</span></span>|`Dim qty`|<span data-ttu-id="2e49c-153">Se `Option Strict` è disabilitato (impostazione predefinita), la variabile è impostata su `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2e49c-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="2e49c-154">Se `Option Strict` è abilitato, si verifica un errore in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="2e49c-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="2e49c-155">No</span><span class="sxs-lookup"><span data-stu-id="2e49c-155">No</span></span>|<span data-ttu-id="2e49c-156">Yes</span><span class="sxs-lookup"><span data-stu-id="2e49c-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="2e49c-157">Se `Option Infer` è abilitato (impostazione predefinita), alla variabile viene assegnato il tipo di dati dell'inizializzatore.</span><span class="sxs-lookup"><span data-stu-id="2e49c-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="2e49c-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2e49c-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="2e49c-159">Se le istruzioni `Option Infer` e `Option Strict` sono disabilitate, il tipo di dati accettato dalla variabile è `Object`.</span><span class="sxs-lookup"><span data-stu-id="2e49c-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="2e49c-160">Se `Option Infer` è disabilitato e `Option Strict` è abilitato, si verifica un errore in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="2e49c-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="2e49c-161">Yes</span><span class="sxs-lookup"><span data-stu-id="2e49c-161">Yes</span></span>|<span data-ttu-id="2e49c-162">No</span><span class="sxs-lookup"><span data-stu-id="2e49c-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="2e49c-163">La variabile viene inizializzata sul valore predefinito per il tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="2e49c-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="2e49c-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2e49c-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|
|<span data-ttu-id="2e49c-165">Yes</span><span class="sxs-lookup"><span data-stu-id="2e49c-165">Yes</span></span>|<span data-ttu-id="2e49c-166">Yes</span><span class="sxs-lookup"><span data-stu-id="2e49c-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="2e49c-167">Se il tipo di dati dell'inizializzatore non è convertibile nel tipo di dati specificato, si verifica un errore in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="2e49c-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="2e49c-168">Esempio</span><span class="sxs-lookup"><span data-stu-id="2e49c-168">Example</span></span>

<span data-ttu-id="2e49c-169">Gli esempi seguenti illustrano come l'istruzione `Option Infer` permette di usare inferenza del tipo di variabile locale.</span><span class="sxs-lookup"><span data-stu-id="2e49c-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="2e49c-170">Esempio</span><span class="sxs-lookup"><span data-stu-id="2e49c-170">Example</span></span>

<span data-ttu-id="2e49c-171">L'esempio seguente dimostra che il tipo di runtime può differire quando una variabile viene identificata come `Object`.</span><span class="sxs-lookup"><span data-stu-id="2e49c-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="2e49c-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2e49c-172">See also</span></span>

- [<span data-ttu-id="2e49c-173">Istruzione Dim</span><span class="sxs-lookup"><span data-stu-id="2e49c-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="2e49c-174">Inferenza del tipo di variabile locale</span><span class="sxs-lookup"><span data-stu-id="2e49c-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2e49c-175">Istruzione Option Compare</span><span class="sxs-lookup"><span data-stu-id="2e49c-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="2e49c-176">Istruzione Option Explicit</span><span class="sxs-lookup"><span data-stu-id="2e49c-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="2e49c-177">Istruzione Option Strict</span><span class="sxs-lookup"><span data-stu-id="2e49c-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2e49c-178">Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni</span><span class="sxs-lookup"><span data-stu-id="2e49c-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="2e49c-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="2e49c-179">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="2e49c-180">Boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="2e49c-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
