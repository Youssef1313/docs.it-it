---
title: Compilare un'applicazione Hello World usando C# con .NET Core in Visual Studio 2017
description: Informazioni su come compilare una semplice applicazione console .NET Core con C# usando Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cc7d78006998b79fe9d522e71883ce1af817c051
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428552"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Compilare un'applicazione Hello World usando C# con .NET Core SDK in Visual Studio 2017

This article provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017. Visual Studio 2017 offre un ambiente di sviluppo completo per la creazione di applicazioni .NET Core. Se l'applicazione non ha alcuna dipendenza specifica della piattaforma, è possibile eseguirla su qualsiasi piattaforma usata come destinazione da .NET Core o su qualsiasi sistema in cui è installato .NET Core.

## <a name="prerequisites"></a>Prerequisites

[Visual Studio 2017 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed. You can develop your app with .NET Core 2.1 or later versions.

For more information, see the [.NET Core dependencies and requirements](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio)article.

## <a name="a-simple-hello-world-application"></a>Semplice applicazione Hello World

Di seguito viene descritta la creazione di una semplice applicazione console "Hello World". Attenersi ai passaggi riportati di seguito.

1. Avviare Visual Studio. Selezionare **File** > **Nuovo** > **Progetto** dalla barra dei menu. Nella finestra di dialogo **Nuovo progetto** selezionare il nodo **Visual C#** seguito dal nodo **.NET Core**. Selezionare quindi il modello di progetto **App Console (.NET Core)** . Nella casella di testo **Nome** digitare "HelloWorld". Selezionare il pulsante **OK** .

   ![Finestra di dialogo Nuovo progetto con App console selezionata](./media/with-visual-studio/visual-studio-new-project.png)

1. Visual Studio usa il modello per creare il progetto. Il modello C# Console Application per .NET Core definisce automaticamente una classe, `Program`, con un singolo metodo, `Main`, che accetta una matrice <xref:System.String> come argomento. `Main` è il punto di ingresso dell'applicazione, ovvero il metodo chiamato automaticamente dal runtime quando viene avviata l'applicazione. Gli argomenti della riga di comando forniti all'avvio dell'applicazione sono disponibili nella matrice *args*.

   ![Visual Studio e il nuovo progetto HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

   Il modello crea una semplice applicazione "Hello World". Chiama il metodo <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> per visualizzare la stringa letterale "Hello World!" nella finestra della console. Facendo clic sul pulsante **HelloWorld** con la freccia verde sulla barra degli strumenti è possibile eseguire il programma in modalità debug. Se si esegue questa operazione, la finestra della console rimane visibile solo per un intervallo di tempo molto breve. Questo si verifica perché il metodo `Main` termina e l'applicazione viene chiusa non appena viene eseguita l'unica istruzione del metodo `Main`.

1. Per impostare l'applicazione in modo che sospenda la finestra della console prima di chiuderla, aggiungere il codice seguente immediatamente dopo la chiamata al metodo <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Il codice chiede all'utente di premere un tasto qualsiasi e quindi sospende il programma fino a quando non viene premuto un tasto.

1. Nella barra dei menu selezionare **Compila** > **Compila soluzione**. Il programma viene compilato in un linguaggio intermedio (IL) che viene successivamente convertito in codice binario da un compilatore JIT (Just-In-Time).

1. Eseguire il programma facendo clic sul pulsante **HelloWorld** con la freccia verde sulla barra degli strumenti.

   ![Finestra della console con il messaggio Hello World che chiede di premere un tasto qualsiasi per continuare](./media/with-visual-studio/hello-world-console.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console.

## <a name="enhancing-the-hello-world-application"></a>Miglioramento dell'applicazione Hello World

Migliorare l'applicazione per richiedere il nome dell'utente e visualizzarlo insieme alla data e ora. Per modificare e testare il programma, seguire questa procedura:

1. Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing curly bracket:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Questo codice sostituisce il contenuto del metodo `Main`.

   ![File C# programma Visual Studio con il metodo Main aggiornato](./media/with-visual-studio/visual-csharp-code-window.png)

   Il codice visualizza "What is your name?" nella console e attende che l'utente inserisca una stringa e prema INVIO. Archivia la stringa in una variabile denominata `name`. Recupera inoltre il valore della proprietà <xref:System.DateTime.Now?displayProperty=nameWithType>, contenente l'ora locale corrente, e lo assegna a una variabile denominata `date`. Usa infine una [stringa interpolata](../../csharp/language-reference/tokens/interpolated.md) per visualizzare questi valori nella finestra della console.

1. Compilare il programma scegliendo **Compila** > **Compila soluzione**.

1. Eseguire il programma in modalità debug in Visual Studio selezionando la freccia verde sulla barra degli strumenti, premendo F5 oppure scegliendo la voce di menu **Debug** > **Avvia debug**. Rispondere alla richiesta immettendo un nome e premendo il tasto INVIO.

   ![Finestra della console con output del programma modificato](./media/with-visual-studio/hello-world-update.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console.

L'applicazione è stata creata ed eseguita. Per sviluppare un'applicazione professionale, eseguire alcuni passaggi aggiuntivi per rendere un'applicazione pronta per il rilascio:

- Per informazioni sul debug dell'applicazione, vedere [Eseguire il debug dell'applicazione .NET Core Hello World con Visual Studio 2017](debugging-with-visual-studio.md).

- Per informazioni sullo sviluppo e la pubblicazione di una versione distribuibile dell'applicazione, vedere [Pubblicare l'applicazione .NET Core Hello World con Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-articles"></a>Articoli correlati

Anziché un'applicazione console, è possibile creare una libreria di classi con .NET Core e Visual Studio 2017. Per un'introduzione dettagliata, vedere [Creazione di una libreria di classi con C# e .NET Core in Visual Studio 2017](library-with-visual-studio.md).

È anche possibile sviluppare un'app console .NET Core in Mac, Linux e Windows usando [Visual Studio Code](https://code.visualstudio.com/), un editor di codice scaricabile gratuitamente. Per un'esercitazione dettagliata, vedere [Introduzione a Visual Studio Code](with-visual-studio-code.md).
