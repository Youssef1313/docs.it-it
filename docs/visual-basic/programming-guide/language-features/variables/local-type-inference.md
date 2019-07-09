---
title: Inferenza del tipo di variabile locale (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 786466cb0b94a96e629a1f173388ed7d40be7256
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661915"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="003d1-102">Inferenza del tipo di variabile locale (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="003d1-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="003d1-103">Usa il compilatore Visual Basic *inferenza* per determinare i tipi di dati delle variabili locali dichiarate senza un `As` clausola.</span><span class="sxs-lookup"><span data-stu-id="003d1-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="003d1-104">Il compilatore deduce il tipo della variabile dal tipo dell'espressione di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="003d1-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="003d1-105">In questo modo è possibile dichiarare variabili senza specificare esplicitamente un tipo, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="003d1-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="003d1-106">Come risultato le dichiarazioni, entrambe `num1` e `num2` sono fortemente tipizzati come numeri interi.</span><span class="sxs-lookup"><span data-stu-id="003d1-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="003d1-107">Se non si desidera `num2` nell'esempio precedente per essere digitato come un' `Integer`, è possibile specificare un altro tipo mediante una dichiarazione simile `Dim num3 As Object = 3` o `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="003d1-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="003d1-108">L'inferenza del tipo può essere usato solo per le variabili locali statiche; non è utilizzabile per determinare il tipo di campi della classe, proprietà o le funzioni.</span><span class="sxs-lookup"><span data-stu-id="003d1-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="003d1-109">L'inferenza del tipo locale si applica a livello di routine.</span><span class="sxs-lookup"><span data-stu-id="003d1-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="003d1-110">Non è utilizzabile per dichiarare le variabili a livello di modulo (all'interno di una classe, struttura, modulo o interfaccia, ma non all'interno di una routine o un blocco).</span><span class="sxs-lookup"><span data-stu-id="003d1-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="003d1-111">Se `num2` nell'esempio precedente sono stati un campo di una classe anziché una variabile locale in una procedura, la dichiarazione provoca un errore con `Option Strict` e classificazione `num2` come un' `Object` con `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="003d1-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="003d1-112">Analogamente, l'inferenza del tipo locale non si applica alle variabili a livello di procedure dichiarate come `Static`.</span><span class="sxs-lookup"><span data-stu-id="003d1-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="003d1-113">Inferenza del tipo e. Associazione tardiva</span><span class="sxs-lookup"><span data-stu-id="003d1-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="003d1-114">Codice che usa l'inferenza del tipo è simile al codice che si basa sull'associazione tardiva.</span><span class="sxs-lookup"><span data-stu-id="003d1-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="003d1-115">Tuttavia, l'inferenza del tipo tipizzare fortemente la variabile anziché lasciarlo come `Object`.</span><span class="sxs-lookup"><span data-stu-id="003d1-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="003d1-116">Il compilatore Usa l'inizializzatore della variabile per determinare il tipo della variabile in fase di compilazione per produrre il codice con associazione anticipata.</span><span class="sxs-lookup"><span data-stu-id="003d1-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="003d1-117">Nell'esempio precedente, `num2`, ad esempio `num1`, viene tipizzato come un `Integer`.</span><span class="sxs-lookup"><span data-stu-id="003d1-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="003d1-118">Il comportamento delle variabili con associazione anticipata è diverso da quello delle variabili con associazione tardiva, per cui il tipo è noto solo in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="003d1-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="003d1-119">Conoscendo in anticipo, il tipo consente al compilatore di identificare i problemi prima dell'esecuzione, allocazione della memoria in modo preciso ed eseguire altre ottimizzazioni.</span><span class="sxs-lookup"><span data-stu-id="003d1-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="003d1-120">Associazione anticipata consente inoltre l'ambiente di sviluppo integrato (IDE) per fornire una Guida di IntelliSense sui membri di un oggetto di Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="003d1-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="003d1-121">È preferibile per le prestazioni anche l'associazione anticipata.</span><span class="sxs-lookup"><span data-stu-id="003d1-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="003d1-122">Infatti, devono essere eseguito il wrapping di tutti i dati archiviati in una variabile di associazione tardiva come tipo `Object`, e l'accesso ai membri del tipo in fase di esecuzione esegue il programma più lento.</span><span class="sxs-lookup"><span data-stu-id="003d1-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="003d1-123">Esempi</span><span class="sxs-lookup"><span data-stu-id="003d1-123">Examples</span></span>  
 <span data-ttu-id="003d1-124">L'inferenza del tipo si verifica quando una variabile locale viene dichiarata senza una `As` clausola e inizializzato.</span><span class="sxs-lookup"><span data-stu-id="003d1-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="003d1-125">Il compilatore utilizza il tipo del valore iniziale assegnato come il tipo della variabile.</span><span class="sxs-lookup"><span data-stu-id="003d1-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="003d1-126">Ad esempio, ognuna delle righe di codice seguente dichiara una variabile di tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="003d1-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="003d1-127">Il codice seguente illustra due modi equivalenti per creare una matrice di interi.</span><span class="sxs-lookup"><span data-stu-id="003d1-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="003d1-128">È consigliabile usare l'inferenza del tipo per determinare il tipo di una variabile di controllo del ciclo.</span><span class="sxs-lookup"><span data-stu-id="003d1-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="003d1-129">Nel codice seguente, il compilatore deduce che `number` è un `Integer` perché `someNumbers2` dall'esempio precedente è una matrice di numeri interi.</span><span class="sxs-lookup"><span data-stu-id="003d1-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="003d1-130">L'inferenza del tipo locale è utilizzabile in `Using` istruzioni per stabilire il tipo del nome della risorsa, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="003d1-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="003d1-131">Il tipo di una variabile può anche essere dedotto dai valori restituiti delle funzioni, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="003d1-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="003d1-132">Entrambe `pList1` e `pList2` sono le matrici dei processi perché `Process.GetProcesses` restituisce una matrice dei processi.</span><span class="sxs-lookup"><span data-stu-id="003d1-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="003d1-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="003d1-133">Option Infer</span></span>  
 <span data-ttu-id="003d1-134">`Option Infer` Consente di specificare se è consentita l'inferenza del tipo locale in un determinato file.</span><span class="sxs-lookup"><span data-stu-id="003d1-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="003d1-135">Per consentire o bloccare l'opzione, digitare una delle istruzioni seguenti all'inizio del file.</span><span class="sxs-lookup"><span data-stu-id="003d1-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="003d1-136">Se non si specifica un valore per `Option Infer` nel codice, il valore predefinito del compilatore è `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="003d1-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> 
  
 <span data-ttu-id="003d1-137">Se il valore impostato per `Option Infer` in un file è in conflitto con il valore impostato nell'IDE o sulla riga di comando, il valore nel file ha precedenza.</span><span class="sxs-lookup"><span data-stu-id="003d1-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="003d1-138">Per altre informazioni, vedere [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [pagina compilazione, creazione progetti (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="003d1-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003d1-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="003d1-139">See also</span></span>

- [<span data-ttu-id="003d1-140">Tipi anonimi</span><span class="sxs-lookup"><span data-stu-id="003d1-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="003d1-141">Associazione anticipata e tardiva</span><span class="sxs-lookup"><span data-stu-id="003d1-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="003d1-142">Istruzione For Each...Next</span><span class="sxs-lookup"><span data-stu-id="003d1-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="003d1-143">Istruzione For...Next</span><span class="sxs-lookup"><span data-stu-id="003d1-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="003d1-144">Istruzione Option Infer</span><span class="sxs-lookup"><span data-stu-id="003d1-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="003d1-145">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="003d1-145">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="003d1-146">Introduzione a LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="003d1-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
