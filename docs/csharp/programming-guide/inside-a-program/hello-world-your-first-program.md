---
title: Hello World -- Il primo programma - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589383"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="ac64a-102">Hello World -- Il primo programma (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="ac64a-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="ac64a-103">La procedura seguente crea una versione C# del programma "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ac64a-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="ac64a-104">tradizionale.</span><span class="sxs-lookup"><span data-stu-id="ac64a-104">program.</span></span> <span data-ttu-id="ac64a-105">Il programma visualizza la stringa `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="ac64a-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="ac64a-106">Per altri esempi di concetti introduttivi, vedere [Introduzione a Visual C# e Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac64a-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="ac64a-107">Per creare ed eseguire un'applicazione console</span><span class="sxs-lookup"><span data-stu-id="ac64a-107">To create and run a console application</span></span>

1. <span data-ttu-id="ac64a-108">Avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac64a-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="ac64a-109">Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="ac64a-110">Verrà visualizzata la finestra di dialogo **Nuovo progetto** .</span><span class="sxs-lookup"><span data-stu-id="ac64a-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ac64a-111">Espandere **Installati**, **Modelli** e **Visual C#** e scegliere **Applicazione console**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="ac64a-112">Nella casella **Nome** specificare un nome per il progetto e quindi scegliere il pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="ac64a-113">Il nuovo progetto verrà visualizzato in **Esplora soluzioni**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="ac64a-114">Se Program.cs non è aperto nell'**Editor di codice**, aprire il menu di scelta rapida per **Program.cs** in **Esplora soluzioni** e selezionare **Visualizza codice**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="ac64a-115">Sostituire il contenuto di Program.cs con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="ac64a-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="ac64a-116">Premere F5 per eseguire il progetto.</span><span class="sxs-lookup"><span data-stu-id="ac64a-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="ac64a-117">Viene visualizzata una finestra del prompt dei comandi che contiene la riga `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="ac64a-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="ac64a-118">Successivamente, vengono esaminate le parti importanti del programma.</span><span class="sxs-lookup"><span data-stu-id="ac64a-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="ac64a-119">Commenti</span><span class="sxs-lookup"><span data-stu-id="ac64a-119">Comments</span></span>

<span data-ttu-id="ac64a-120">La prima riga contiene un commento.</span><span class="sxs-lookup"><span data-stu-id="ac64a-120">The first line contains a comment.</span></span> <span data-ttu-id="ac64a-121">I caratteri `//` convertono il resto della riga in un commento.</span><span class="sxs-lookup"><span data-stu-id="ac64a-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="ac64a-122">È anche possibile commentare un blocco di testo racchiudendolo tra i caratteri `/*` e `*/`,</span><span class="sxs-lookup"><span data-stu-id="ac64a-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="ac64a-123">come illustrato nell'esempio riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="ac64a-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="ac64a-124">metodo Main</span><span class="sxs-lookup"><span data-stu-id="ac64a-124">Main method</span></span>

<span data-ttu-id="ac64a-125">È necessario che un'applicazione console C# contenga un metodo `Main`, in cui il controllo inizia e finisce.</span><span class="sxs-lookup"><span data-stu-id="ac64a-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="ac64a-126">Il metodo `Main` consente di creare oggetti e di eseguire altri metodi.</span><span class="sxs-lookup"><span data-stu-id="ac64a-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="ac64a-127">Il metodo `Main` è un metodo di tipo [static](../../language-reference/keywords/static.md) che si trova all'interno di una classe o di uno struct.</span><span class="sxs-lookup"><span data-stu-id="ac64a-127">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="ac64a-128">Nell'esempio "Hello World!" precedente</span><span class="sxs-lookup"><span data-stu-id="ac64a-128">In the previous "Hello World!"</span></span> <span data-ttu-id="ac64a-129">si trovava in una classe denominata `Hello`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="ac64a-130">È possibile dichiarare il metodo `Main` in uno dei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ac64a-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="ac64a-131">Può restituire un valore `void`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="ac64a-132">Può restituire anche un valore intero.</span><span class="sxs-lookup"><span data-stu-id="ac64a-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="ac64a-133">Con entrambi i tipi restituiti, può accettare argomenti.</span><span class="sxs-lookup"><span data-stu-id="ac64a-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="ac64a-134">-oppure-</span><span class="sxs-lookup"><span data-stu-id="ac64a-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="ac64a-135">Il parametro del metodo `Main`, `args`, è una matrice `string` che contiene gli argomenti della riga di comando usati per richiamare il programma.</span><span class="sxs-lookup"><span data-stu-id="ac64a-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="ac64a-136">A differenza di C++, la matrice non include il nome del file eseguibile con estensione exe.</span><span class="sxs-lookup"><span data-stu-id="ac64a-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="ac64a-137">Per altre informazioni sull'uso degli argomenti della riga di comando, vedere gli esempi in [Main() e argomenti della riga di comando](../main-and-command-args/index.md) e [Procedura: Creare e usare assembly dalla riga di comando](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="ac64a-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="ac64a-138">La chiamata a <xref:System.Console.ReadKey%2A> alla fine del metodo `Main` evita che la finestra della console si chiuda prima che sia possibile leggere l'output quando si esegue il programma in modalità di debug, premendo F5.</span><span class="sxs-lookup"><span data-stu-id="ac64a-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="ac64a-139">Input e output</span><span class="sxs-lookup"><span data-stu-id="ac64a-139">Input and output</span></span>

<span data-ttu-id="ac64a-140">In genere i programmi C# usano i servizi di input/output offerti dalla libreria run-time di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac64a-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="ac64a-141">L'istruzione `System.Console.WriteLine("Hello World!");` usa il metodo <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac64a-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="ac64a-142">Questo è uno dei metodi di output della classe <xref:System.Console> nella libreria di runtime.</span><span class="sxs-lookup"><span data-stu-id="ac64a-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="ac64a-143">Visualizza il parametro di tipo stringa sul flusso di output standard seguito da una nuova riga.</span><span class="sxs-lookup"><span data-stu-id="ac64a-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="ac64a-144">Sono disponibili altri metodi <xref:System.Console> per diverse operazioni di input e output.</span><span class="sxs-lookup"><span data-stu-id="ac64a-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="ac64a-145">Se si include la direttiva `using System;` all'inizio del programma, è possibile usare direttamente le classi e i metodi <xref:System> senza specificarne il nome completo.</span><span class="sxs-lookup"><span data-stu-id="ac64a-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="ac64a-146">Ad esempio, è possibile chiamare `Console.WriteLine` anziché `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="ac64a-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="ac64a-147">Per altre informazioni sui metodi di input/output, vedere <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="ac64a-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="ac64a-148">Esecuzione e compilazione da riga di comando</span><span class="sxs-lookup"><span data-stu-id="ac64a-148">Command-line compilation and execution</span></span>

<span data-ttu-id="ac64a-149">È possibile compilare il programma "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ac64a-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="ac64a-150">usando la riga di comando invece dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac64a-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="ac64a-151">Per compilare ed eseguire codice a un prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="ac64a-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="ac64a-152">Incollare il codice della procedura precedente in un editor di testo e salvare il file come file di testo.</span><span class="sxs-lookup"><span data-stu-id="ac64a-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="ac64a-153">Denominare il file `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="ac64a-154">I file del codice sorgente di C# usano l'estensione `.cs`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="ac64a-155">Eseguire una delle procedure seguenti per aprire una finestra al prompt dei comandi:</span><span class="sxs-lookup"><span data-stu-id="ac64a-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="ac64a-156">In Windows 10 nel menu **Start** cercare `Developer Command Prompt` e toccare o selezionare **Prompt dei comandi per gli sviluppatori per VS2017**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="ac64a-157">Viene visualizzata una finestra del prompt dei comandi per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ac64a-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="ac64a-158">In Windows 7 aprire il menu **Start**, espandere la cartella della versione corrente di Visual Studio, aprire il menu di scelta rapida per **Strumenti di Visual Studio** e selezionare **Prompt dei comandi per gli sviluppatori per VS2017**.</span><span class="sxs-lookup"><span data-stu-id="ac64a-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="ac64a-159">Viene visualizzata una finestra del prompt dei comandi per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ac64a-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="ac64a-160">Abilitare le compilazioni da riga di comando da una finestra del prompt dei comandi standard.</span><span class="sxs-lookup"><span data-stu-id="ac64a-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="ac64a-161">Vedere [Procedura: Impostare le variabili di ambiente per la riga di comando di Visual Studio](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="ac64a-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="ac64a-162">Nella finestra del prompt dei comandi passare alla cartella che contiene il file `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="ac64a-163">Immettere il comando seguente per compilare `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="ac64a-164">Se il programma non presenta errori di compilazione, viene creato un file eseguibile denominato `Hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="ac64a-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="ac64a-165">Nella finestra del prompt dei comandi immettere il comando seguente per eseguire il programma:</span><span class="sxs-lookup"><span data-stu-id="ac64a-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="ac64a-166">Per altre informazioni sul compilatore C# e le relative opzioni, vedere [C# Compiler Options](../../language-reference/compiler-options/index.md) (Opzioni del compilatore C#).</span><span class="sxs-lookup"><span data-stu-id="ac64a-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac64a-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ac64a-167">See also</span></span>

- [<span data-ttu-id="ac64a-168">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="ac64a-168">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ac64a-169">Contenuto di un programma C#</span><span class="sxs-lookup"><span data-stu-id="ac64a-169">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="ac64a-170">Stringhe</span><span class="sxs-lookup"><span data-stu-id="ac64a-170">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="ac64a-171">Esempi ed esercitazioni</span><span class="sxs-lookup"><span data-stu-id="ac64a-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="ac64a-172">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="ac64a-172">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ac64a-173">Main() e argomenti della riga di comando</span><span class="sxs-lookup"><span data-stu-id="ac64a-173">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="ac64a-174">Guida introduttiva a Visual C# e Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac64a-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
