---
title: Creazione di una soluzione .NET Core completa in macOS con Visual Studio per Mac
description: Questo argomento descrive il processo di creazione di una soluzione .NET Core contenente una libreria riutilizzabile e unit test.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: a2459bfdc50e64b1d6710853b556c1bf226f07e7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849563"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Creazione di una soluzione .NET Core completa in macOS con Visual Studio per Mac

Visual Studio per Mac offre un ambiente di sviluppo integrato completo per lo sviluppo di applicazioni .NET Core. Questo argomento descrive il processo di creazione di una soluzione .NET Core contenente una libreria riutilizzabile e unit test.

In questa esercitazione viene illustrato come creare un'applicazione che accetta una parola di ricerca e una stringa di testo dall'utente, conta il numero di volte in cui la parola di ricerca appare nella stringa usando un metodo in una libreria di classi e restituisce il risultato all'utente. La soluzione include anche unit test per la libreria di classi come introduzione ai concetti relativi al testing unità. Se si preferisce continuare l'esercitazione con un esempio completo, scaricare la [soluzione di esempio](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Per istruzioni sul download, vedere [Esempi ed esercitazioni](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Microsoft considera di fondamentale importanza i commenti e i suggerimenti degli utenti. Sono disponibili due modi per comunicare al team di sviluppatori la propria opinione su Visual Studio per Mac:
> - In Visual Studio per Mac scegliere **Aiuto** > **Segnala un problema** dal menu o **Segnala un problema** dalla schermata iniziale per visualizzare una finestra per la registrazione di un report sul bug. È possibile tenere traccia dei commenti e dei suggerimenti inviati nel portale della [community di sviluppatori](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Per inviare un suggerimento, scegliere **Aiuto** > **Invia un suggerimento** dal menu o **Invia un suggerimento** dalla schermata iniziale per aprire la [pagina Web Developer Community di Visual Studio per Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Prerequisiti

- OpenSSL (se è in esecuzione .NET Core 1.1): Vedere l'argomento [Prerequisiti per .NET Core in Mac](../macos-prerequisites.md).
- [.NET Core SDK 1.1 o versione successiva](https://dotnet.microsoft.com/download)
- [Visual Studio 2017 per Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Per altre informazioni sui prerequisiti, vedere [Prerequisiti per .NET Core in Mac](../macos-prerequisites.md). Per informazioni su tutti i requisiti di sistema per Visual Studio 2017 per Mac, vedere [Requisiti di sistema della famiglia di prodotti Visual Studio 2017 per Mac](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Creazione di una libreria

1. Nella schermata iniziale selezionare **Nuovo progetto**. Nella finestra di dialogo **Nuovo progetto**, nel nodo **.NET Core**, selezionare il modello **Libreria .NET Standard**. Verrà creata una libreria .NET Standard che ha come destinazione .NET Core, nonché qualsiasi altra implementazione .NET che supporta la versione 2.0 di [.NET Standard](../../standard/net-standard.md). Selezionare **Avanti**.

   ![Finestra di dialogo Nuovo progetto di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Assegnare al progetto il nome "TextUtils" (nome breve per "Text Utilities") e alla soluzione il nome "WordCounter". Lasciare selezionata la casella **Crea una directory del progetto nella directory della soluzione**. Selezionare **Create**.

   ![Opzioni della finestra di dialogo Nuovo progetto di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Nella barra laterale **Soluzione** espandere il nodo `TextUtils` per visualizzare il file di classe fornito dal modello: *Class1.cs*. Fare clic con il pulsante destro del mouse sul file, scegliere **Rinomina** dal menu di scelta rapida e rinominare il file in *WordCount.cs*. Aprire il file e sostituire il contenuto con il codice seguente:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Salvare il file adottando uno di questi tre metodi: usare la scelta rapida da tastiera <kbd>&#8984;</kbd>+<kbd>s</kbd>, scegliere **File** > **Salva** dal menu o fare clic con il pulsante destro del mouse sulla scheda del file e scegliere **Salva** dal menu di scelta rapida. Nell'immagine seguente viene visualizzata la finestra dell'IDE:

   ![Finestra dell'IDE di Visual Studio per Mac con file e metodo della di libreria di classi](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Selezionare **Errori** nel margine inferiore della finestra dell'IDE per aprire il pannello **Errori**. Selezionare il pulsante **Output di compilazione**.

   ![Margine inferiore della finestra dell'IDE di Visual Studio per Mac con il pulsante Errori](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Scegliere **Compila** > **Compila tutto** dal menu.

   La soluzione viene compilata e il riquadro dell'output di compilazione indica che la compilazione ha avuto esito positivo.

   ![Riquadro dell'output di compilazione del pannello Errori con il messaggio di compilazione riuscita di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Creazione di un progetto di test

Gli unit test forniscono test software automatici durante le fasi di sviluppo e pubblicazione. Il framework di test usato in questa esercitazione è [xUnit (versione 2.2.0 o successiva)](https://xunit.github.io/), installato automaticamente quando il progetto di test xUnit viene aggiunto alla soluzione nella procedura seguente:

1. Nella barra laterale **Soluzione** fare clic con il pulsante destro del mouse sulla soluzione `WordCounter` e scegliere **Aggiungi** > **Aggiungi nuovo progetto**.

1. Nella finestra di dialogo **Nuovo progetto** selezionare **Test** sotto il nodo **.NET Core**. Selezionare **xUnit Test Project** (Progetto di test xUnit) e quindi scegliere **Avanti**.

   ![Finestra di dialogo Nuovo progetto di Visual Studio per Mac in cui si crea il progetto di test xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Assegnare al nuovo progetto il nome "TestLibrary" e scegliere **Crea**.

   ![Finestra di dialogo Nuovo progetto di Visual Studio per Mac in cui si specifica il nome del progetto](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aggiungere un riferimento al progetto `TextUtils` per consentire l'interazione tra la libreria di test e la classe `WordCount`. Nella barra laterale **Soluzione** fare clic con il pulsante destro del mouse su **Dipendenze** in **TestLibrary**. Scegliere **Modifica riferimenti** dal menu di scelta rapida.

1. Nella finestra di dialogo **Modifica riferimenti** selezionare il progetto **TextUtils** nella scheda **Progetti**. Selezionare **OK**.

   ![Finestra di dialogo Modifica riferimenti di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. Nel progetto **TestLibrary** rinominare il file *UnitTest1.cs* in *TextUtilsTests.cs*.

1. Aprire il file e sostituire il codice con il seguente:

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   Nell'immagine seguente viene visualizzato l'IDE con il codice dell'unit test. Prestare attenzione all'istruzione `Assert.NotEqual`.

   ![Unit test iniziale di Visual Studio per Mac nella finestra principale dell'IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   È importante fare in modo che il nuovo test la prima volta abbia esito negativo per verificare che la logica di test sia corretta. Il metodo passa il nome "Jack" (lettere maiuscole) e una stringa con "Jack" e "jack" (lettere maiuscole e minuscole). Se il metodo `GetWordCount` funziona correttamente, viene restituito un conteggio di due istanze della parola di ricerca. Per fare in modo che il test non riesca, è necessario prima implementare il test asserendo che dal metodo `GetWordCount` non vengono restituite due istanze della parola di ricerca "Jack". Andare quindi al passaggio successivo per fare in modo che il test abbia esito negativo.

1. Aprire il pannello **Unit test** sul lato destro dello schermo.

   ![Pannello degli unit test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Fare clic sull'icona **Ancora** per mantenere aperto il pannello.

   ![Icona di ancoraggio del pannello degli unit test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Fare clic sul pulsante **Esegui tutto**.

   Il test ha esito negativo, che è il risultato previsto. Il metodo di test indica che dalla stringa "Jack Jack" fornita al metodo `GetWordCount` non vengono restituite due istanze della stringa `inputString`, "Jack". Poiché nel metodo `GetWordCount` è stato escluso l'uso delle maiuscole/minuscole, vengono invece restituite due istanze. L'asserzione che 2 *non è uguale a* 2 ha esito negativo. Questo è il risultato previsto e la logica del test è corretta.

   ![Visualizzazione dell'esito negativo del test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Modificare il metodo di test `IgnoreCasing` sostituendo `Assert.NotEqual` con `Assert.Equal`. Salvare il file usando la scelta rapida da tastiera <kbd>&#8984;</kbd>+<kbd>s</kbd>, selezionando **File** > **Salva** dal menu o facendo clic con il pulsante destro del mouse sulla scheda del file e scegliendo **Salva** dal menu di scelta rapida.

   Si prevede che l'oggetto `searchWord` "Jack" restituisca due istanze con la stringa `inputString` "Jack jack" passata a `GetWordCount`. Eseguire di nuovo il test: fare clic sul pulsante **Esegui test** nel pannello **Unit test** o sul pulsante **Riesegui test** nel pannello **Risultati test** nella parte inferiore della schermata. Il test ha esito positivo. Nella stringa "Jack jack" (senza distinzione tra maiuscole e minuscole) sono presenti due istanze di "Jack" e l'asserzione del test è `true`.

   ![Visualizzazione dell'esito positivo del test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. La restituzione di singoli valori di test con un oggetto `Fact` è solo una delle operazioni che è possibile eseguire con gli unit test. Grazie a un'altra tecnica molto efficace, è possibile eseguire il test di più valori contemporaneamente usando un oggetto `Theory`. Aggiungere il metodo seguente alla classe `TextUtils_GetWordCountShould`. Dopo aver aggiunto il metodo alla classe sono disponibili due metodi:

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` verifica che il metodo `GetWordCount` esegua il conteggio in modo corretto. L'oggetto `InlineData` fornisce un conteggio, una parola di ricerca e una stringa di input da verificare. Il metodo di test viene eseguito una volta per ogni riga di dati. Tenere presente che, ancora una volta, si sta asserendo un esito negativo prima di tutto tramite `Assert.NotEqual`, anche se si è certi che i conteggi dei dati siano corretti e che i valori corrispondano ai conteggi restituiti dal metodo `GetWordCount`. Anche se, in un primo momento, l'esecuzione del test con esito negativo sembra una perdita di tempo, la verifica della logica del test tramite la generazione di un esito negativo consente in realtà di attestarne la correttezza. Quando si riscontra un metodo di test che ha esito positivo quando invece dovrebbe avere esito negativo, si è trovato un bug nella logica del test. Vale quindi la pena eseguire questo passaggio ogni volta che si crea un metodo di test.

1. Salvare il file ed eseguire di nuovo i test. Il test delle maiuscole/minuscole ha esito positivo, mentre i tre test del conteggio hanno esito negativo. Questo è esattamente il risultato previsto.

   ![Esito negativo previsto del test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Modificare il metodo di test `CountInstancesCorrectly` sostituendo `Assert.NotEqual` con `Assert.Equal`. Salvare il file. Eseguire di nuovo i test. Tutti i test hanno esito positivo.

   ![Esito positivo previsto del test di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Aggiunta di un'app console

1. Nella barra laterale **Soluzione** fare clic con il pulsante destro del mouse sulla soluzione `WordCounter`. Aggiungere un nuovo progetto **Applicazione console** selezionando il modello corrispondente dai modelli **.NET Core** > **App**. Scegliere **Avanti**. Assegnare al progetto il nome **WordCounterApp**. Scegliere **Crea** per creare il progetto nella soluzione.

1. Nella barra laterale **Soluzioni** fare clic con il pulsante destro del mouse sul nodo **Dipendenze** del nuovo progetto **WordCounterApp**. Nella finestra di dialogo **Modifica riferimenti** selezionare **TextUtils** e scegliere **OK**.

1. Aprire il file *Program.cs*. Sostituire il codice con quello seguente:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Per eseguire l'app in una finestra della console anziché nell'IDE, fare clic con il pulsante destro del mouse sul progetto `WordCounterApp`, scegliere **Opzioni** e aprire il nodo **Predefinito** in **Configurazioni**. Selezionare la casella di controllo **Esegui in console esterna**. Lasciare selezionata l'opzione **Sospendi output della console**. Con questa impostazione l'app viene generata in una finestra della console in cui è possibile digitare l'input per le istruzioni `Console.ReadLine`. Se invece si lascia che l'app venga eseguita nell'ambiente IDE, è possibile vedere solo l'output delle istruzioni `Console.WriteLine`. Le istruzioni `Console.ReadLine` non funzionano nel pannello **Output applicazione** dell'ambiente IDE.

   ![Finestra delle opzioni del progetto di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Dato che la versione corrente di Visual Studio per Mac non supporta l'esecuzione dei test quando è in esecuzione la soluzione, si esegue direttamente l'app console. Fare clic con il pulsante destro del mouse sul progetto `WordCounterApp` e scegliere **Run item** (Esegui elemento) dal menu di scelta rapida. Se si prova a eseguire l'applicazione con il pulsante di riproduzione, l'esecuzione del Test Runner e dell'app avranno esito negativo. Per altre informazioni sullo stato del lavoro inerente a questo problema, vedere [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Con l'app in esecuzione, specificare i valori relativi alla parola di ricerca e alla stringa di input quando vengono richiesti nella finestra della console. L'app indica il numero di volte in cui la parola di ricerca appare nella stringa.

   ![Finestra della console di Visual Studio per Mac con l'app in esecuzione](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Si esaminerà infine la funzionalità di debug con Visual Studio per Mac. Impostare un punto di interruzione nell'istruzione `Console.WriteLine`: selezionare il margine sinistro della riga 23. Verrà visualizzato un cerchio rosso accanto alla riga di codice. In alternativa, selezionare un punto qualsiasi nella riga di codice e scegliere **Esegui** > **Imposta/Rimuovi punto di interruzione** dal menu.

   ![Impostazione punto di interruzione in Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Fare clic con il pulsante destro del mouse sul progetto `WordCounterApp`. Scegliere l'elemento **Avvia debug** dal menu di scelta rapida. Quando si esegue l'app, immettere la parola di ricerca "cat" e "The dog chased the cat, but the cat escaped." come stringa in cui eseguire la ricerca. Quando viene raggiunta l'istruzione `Console.WriteLine`, l'esecuzione del programma si interrompe per consentire l'esecuzione dell'istruzione. Nella scheda **Variabili locali** sono presenti i valori `searchWord`, `inputString`, `wordCount` e `pluralChar`.

   ![Esecuzione del programma di debug di Visual Studio per Mac arrestata](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. Nel riquadro **Immediato** digitare "wordCount = 999;" e premere INVIO. Alla variabile `wordCount` viene assegnato un valore senza senso di 999 per indicare che è possibile sostituire i valori della variabile durante il debug.

   ![Valori di Visual Studio per Mac modificati nella finestra Immediato](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Sulla barra degli strumenti fare clic sulla freccia per *continuare*. Esaminare l'output nella finestra della console. Viene visualizzato il valore non corretto 999 impostato durante il debug dell'app.

   ![Pulsante per continuare nella barra degli strumenti di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Output della finestra della console di Visual Studio per Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Vedere anche

- [Note sulla versione di Visual Studio 2017 per Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
