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
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- Il primo programma (Guida per programmatori C#)

La procedura seguente crea una versione C# del programma "Hello World!" tradizionale. Il programma visualizza la stringa `Hello World!`

Per altri esempi di concetti introduttivi, vedere [Introduzione a Visual C# e Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Per creare ed eseguire un'applicazione console

1. Avviare Visual Studio.

2. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Espandere **Installati**, **Modelli** e **Visual C#** e scegliere **Applicazione console**.

4. Nella casella **Nome** specificare un nome per il progetto e quindi scegliere il pulsante **OK**.

     Il nuovo progetto verrà visualizzato in **Esplora soluzioni**.

5. Se Program.cs non è aperto nell'**Editor di codice**, aprire il menu di scelta rapida per **Program.cs** in **Esplora soluzioni** e selezionare **Visualizza codice**.

6. Sostituire il contenuto di Program.cs con il codice seguente.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Premere F5 per eseguire il progetto. Viene visualizzata una finestra del prompt dei comandi che contiene la riga `Hello World!`

Successivamente, vengono esaminate le parti importanti del programma.

## <a name="comments"></a>Commenti

La prima riga contiene un commento. I caratteri `//` convertono il resto della riga in un commento.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

È anche possibile commentare un blocco di testo racchiudendolo tra i caratteri `/*` e `*/`, come illustrato nell'esempio riportato di seguito.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>metodo Main

È necessario che un'applicazione console C# contenga un metodo `Main`, in cui il controllo inizia e finisce. Il metodo `Main` consente di creare oggetti e di eseguire altri metodi.

Il metodo `Main` è un metodo di tipo [static](../../language-reference/keywords/static.md) che si trova all'interno di una classe o di uno struct. Nell'esempio "Hello World!" precedente si trovava in una classe denominata `Hello`. È possibile dichiarare il metodo `Main` in uno dei modi seguenti:

- Può restituire un valore `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Può restituire anche un valore intero.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Con entrambi i tipi restituiti, può accettare argomenti.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     -oppure-

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Il parametro del metodo `Main`, `args`, è una matrice `string` che contiene gli argomenti della riga di comando usati per richiamare il programma. A differenza di C++, la matrice non include il nome del file eseguibile con estensione exe.

Per altre informazioni sull'uso degli argomenti della riga di comando, vedere gli esempi in [Main() e argomenti della riga di comando](../main-and-command-args/index.md) e [Procedura: Creare e usare assembly dalla riga di comando](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

La chiamata a <xref:System.Console.ReadKey%2A> alla fine del metodo `Main` evita che la finestra della console si chiuda prima che sia possibile leggere l'output quando si esegue il programma in modalità di debug, premendo F5.

## <a name="input-and-output"></a>Input e output

In genere i programmi C# usano i servizi di input/output offerti dalla libreria run-time di .NET Framework. L'istruzione `System.Console.WriteLine("Hello World!");` usa il metodo <xref:System.Console.WriteLine%2A>. Questo è uno dei metodi di output della classe <xref:System.Console> nella libreria di runtime. Visualizza il parametro di tipo stringa sul flusso di output standard seguito da una nuova riga. Sono disponibili altri metodi <xref:System.Console> per diverse operazioni di input e output. Se si include la direttiva `using System;` all'inizio del programma, è possibile usare direttamente le classi e i metodi <xref:System> senza specificarne il nome completo. Ad esempio, è possibile chiamare `Console.WriteLine` anziché `System.Console.WriteLine`:

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Per altre informazioni sui metodi di input/output, vedere <xref:System.IO>.

## <a name="command-line-compilation-and-execution"></a>Esecuzione e compilazione da riga di comando

È possibile compilare il programma "Hello World!" usando la riga di comando invece dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) di Visual Studio.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Per compilare ed eseguire codice a un prompt dei comandi

1. Incollare il codice della procedura precedente in un editor di testo e salvare il file come file di testo. Denominare il file `Hello.cs`. I file del codice sorgente di C# usano l'estensione `.cs`.

2. Eseguire una delle procedure seguenti per aprire una finestra al prompt dei comandi:

    - In Windows 10 nel menu **Start** cercare `Developer Command Prompt` e toccare o selezionare **Prompt dei comandi per gli sviluppatori per VS2017**.

         Viene visualizzata una finestra del prompt dei comandi per gli sviluppatori.

    - In Windows 7 aprire il menu **Start**, espandere la cartella della versione corrente di Visual Studio, aprire il menu di scelta rapida per **Strumenti di Visual Studio** e selezionare **Prompt dei comandi per gli sviluppatori per VS2017**.

         Viene visualizzata una finestra del prompt dei comandi per gli sviluppatori.

    - Abilitare le compilazioni da riga di comando da una finestra del prompt dei comandi standard.

         Vedere [Procedura: Impostare le variabili di ambiente per la riga di comando di Visual Studio](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

3. Nella finestra del prompt dei comandi passare alla cartella che contiene il file `Hello.cs`.

4. Immettere il comando seguente per compilare `Hello.cs`.

     `csc Hello.cs`

     Se il programma non presenta errori di compilazione, viene creato un file eseguibile denominato `Hello.exe`.

5. Nella finestra del prompt dei comandi immettere il comando seguente per eseguire il programma:

     `Hello`

 Per altre informazioni sul compilatore C# e le relative opzioni, vedere [C# Compiler Options](../../language-reference/compiler-options/index.md) (Opzioni del compilatore C#).

## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Contenuto di un programma C#](./index.md)
- [Stringhe](../strings/index.md)
- [Esempi ed esercitazioni](../../../samples-and-tutorials/index.md)
- [Riferimenti per C#](../../language-reference/index.md)
- [Main() e argomenti della riga di comando](../main-and-command-args/index.md)
- [Guida introduttiva a Visual C# e Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
