---
title: 'Esercitazione: analizzare i sentimenti delle revisioni dei film usando un modello TensorFlow con training preliminare'
description: Questa esercitazione illustra come usare un modello TensorFlow con training preliminare per classificare i sentimenti nei commenti dei siti Web. Il classificatore dei sentimenti binari è C# un'applicazione console sviluppata con Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 8c3544b60b1fba1d419ca091b0a1d85fbbdbe2d6
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204928"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Esercitazione: analizzare i sentimenti delle revisioni dei film usando un modello TensorFlow con training preliminare in ML.NET

Questa esercitazione illustra come usare un modello TensorFlow con training preliminare per classificare i sentimenti nei commenti dei siti Web. Il classificatore dei sentimenti binari è C# un'applicazione console sviluppata con Visual Studio.

Il modello TensorFlow usato in questa esercitazione è stato sottoposto a training con le revisioni dei film del database IMDB. Al termine dello sviluppo dell'applicazione, sarà possibile fornire il testo della revisione del film e l'applicazione indica se la revisione ha un sentimento positivo o negativo.

In questa esercitazione si imparerà a:
> [!div class="checklist"]
>
> * Caricare un modello di TensorFlow con training preliminare
> * Trasforma il testo del commento del sito Web in funzionalità appropriate per il modello
> * Usare il modello per eseguire una stima

È possibile trovare il codice sorgente per questa esercitazione nel repository [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Prerequisiti

* [Visual Studio 2017 versione 15,6 o successiva](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) con il carico di lavoro "sviluppo multipiattaforma .NET Core" installato.

## <a name="setup"></a>Configurazione

### <a name="create-the-application"></a>Creare l'applicazione

1. Creare un' **applicazione console .NET Core** denominata "TextClassificationTF".

2. Creare una directory denominata *Dati* nel progetto per salvare i file del set di dati.

3. Installare il **pacchetto NuGet Microsoft.ML**:

    In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e selezionare **Gestisci pacchetti NuGet**. Scegliere "nuget.org" come origine del pacchetto, quindi selezionare la scheda **Sfoglia** . cercare **Microsoft.ml**, selezionare il pacchetto desiderato e quindi fare clic sul pulsante **Installa** . Procedere con l'installazione accettando le condizioni di licenza per il pacchetto scelto. Ripetere questi passaggi per **Microsoft. ml. TensorFlow** e **SciSharp. TensorFlow. Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Aggiungere il modello TensorFlow al progetto

> [!NOTE]
> Il modello per questa esercitazione è del repository GitHub [DotNet/machinelearning-TESTDATA](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) . Il modello è in formato TensorFlow SavedModel.

1. Scaricare il [file zip di sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)e decomprimere.

    Il file zip contiene:

    * `saved_model.pb`: modello TensorFlow. Il modello accetta una matrice di valori interi di lunghezza fissa (dimensione 600) che rappresenta il testo in una stringa di revisione di IMDB e restituisce due probabilità che sommano a 1: la probabilità che la revisione di input abbia un sentimento positivo e la probabilità che la revisione di input abbia sentimento negativo.
    * `imdb_word_index.csv`: un mapping da singole parole a un valore integer. Il mapping viene utilizzato per generare le funzionalità di input per il modello TensorFlow.

2. Copiare il contenuto della directory `sentiment_model` più interna nella directory del progetto *TextClassificationTF* `sentiment_model`. Questa directory contiene il modello e i file di supporto aggiuntivi necessari per questa esercitazione, come illustrato nell'immagine seguente:

   ![contenuto della directory sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. In Esplora soluzioni fare clic con il pulsante destro del mouse su ogni file nella directory `sentiment_model` e nella sottodirectory e selezionare **Proprietà**. In **Avanzate** impostare il valore di **Copia nella directory di output** su **Copia se più recente**.

### <a name="add-using-statements-and-global-variables"></a>Aggiungere istruzioni using e variabili globali

1. Aggiungere le istruzioni `using` seguenti all'inizio del file *Program.cs*:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. Creare due variabili globali immediatamente sopra il metodo `Main` per conservare il percorso del file del modello salvato e la lunghezza del vettore di funzionalità.

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath` è il percorso del file del modello sottoposto a training.
    * `FeatureLength` è la lunghezza della matrice di funzionalità Integer prevista per il modello.

### <a name="model-the-data"></a>Modellare i dati

Le revisioni del film sono testo in formato libero. L'applicazione converte il testo nel formato di input previsto dal modello in diverse fasi discrete.

Il primo consiste nel suddividere il testo in parole separate e utilizzare il file di mapping specificato per eseguire il mapping di ogni parola a una codifica di tipo Integer. Il risultato di questa trasformazione è una matrice integer a lunghezza variabile con una lunghezza corrispondente al numero di parole nella frase.

|Proprietà| Value|Type|
|-------------|-----------------------|------|
|ReviewText|Questo film è molto valido|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

La matrice di funzionalità a lunghezza variabile viene quindi ridimensionata a una lunghezza fissa di 600. Si tratta della lunghezza prevista dal modello TensorFlow.

|Proprietà| Value|Type|
|-------------|-----------------------|------|
|ReviewText|Questo film è molto valido|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Funzionalità|14, 22, 9, 66, 78,... |int [600]|

1. Creare una classe per i dati di input, dopo il metodo `Main`:

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    La classe di dati di input, `MovieReview`, dispone di un `string` per i commenti degli utenti (`ReviewText`).

1. Creare una classe per le funzionalità a lunghezza variabile, dopo il metodo `Main`:

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    La proprietà `VariableLengthFeatures` dispone di un attributo [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) per designarla come vettore.  Tutti gli elementi Vector devono essere dello stesso tipo. Nei set di dati con un numero elevato di colonne, il caricamento di più colonne come un singolo vettore riduce il numero di passaggi di dati quando si applicano le trasformazioni dei dati.

    Questa classe viene utilizzata nell'azione `ResizeFeatures`. I nomi delle proprietà (in questo caso solo uno) vengono utilizzati per indicare quali colonne del DataView possono essere utilizzate come _input_ per l'azione di mapping personalizzata.

1. Creare una classe per le funzionalità a lunghezza fissa, dopo il metodo `Main`:

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    Questa classe viene utilizzata nell'azione `ResizeFeatures`. I nomi delle proprietà (in questo caso solo uno) vengono utilizzati per indicare quali colonne del DataView possono essere utilizzate come _output_ dell'azione di mapping personalizzata.

    Si noti che il nome della proprietà `Features` è determinato dal modello TensorFlow. Non è possibile modificare questo nome di proprietà.

1. Creare una classe per la stima dopo il metodo `Main`:

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` è la classe di stima usata dopo il training del modello. `MovieReviewSentimentPrediction` dispone di una singola matrice di `float` (`Prediction`) e di un attributo `VectorType`.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Creare il MLContext, il dizionario di ricerca e l'azione per ridimensionare le funzionalità

La [classe MLContext](xref:Microsoft.ML.MLContext) è un punto di partenza per tutte le operazioni ML.NET. L'inizializzazione di `mlContext` crea un nuovo ambiente ML.NET che può essere condiviso tra gli oggetti del flusso di lavoro della creazione del modello. Dal punto di vista concettuale è simile a `DBContext` in Entity Framework.

1. Sostituire la riga `Console.WriteLine("Hello World!")` nel metodo `Main` con il codice seguente per dichiarare e inizializzare la variabile mlContext:

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. Creare un dizionario per codificare le parole come numeri interi usando il metodo [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) per caricare i dati di mapping da un file, come illustrato nella tabella seguente:

    |Word     |Indice    |
    |---------|---------|
    |bambini     |  362    |
    |desidera     |  181    |
    |errato    |  355    |
    |effetti  |  302    |
    |ci si sente  |  547    |

    Aggiungere il codice seguente per creare la mappa di ricerca:

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. Aggiungere un `Action` per ridimensionare la matrice di tipo Integer a lunghezza variabile in una matrice di numeri interi di dimensioni fisse, con le righe di codice seguenti:

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Caricare il modello di TensorFlow con training preliminare

1. Aggiungere codice per caricare il modello di TensorFlow:

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    Una volta caricato il modello, è possibile estrarne lo schema di input e di output. Gli schemi vengono visualizzati solo per interesse e apprendimento. Questo codice non è necessario per il funzionamento dell'applicazione finale:

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    Lo schema di input è la matrice a lunghezza fissa di parole con codifica Integer. Lo schema di output è una matrice di probabilità float che indica se il sentimento di una verifica è negativo o positivo. Questi valori vengono sommati a 1, in quanto la probabilità di essere positivi è il complemento della probabilità che il sentimento sia negativo.

## <a name="create-the-mlnet-pipeline"></a>Creare la pipeline ML.NET

1. Creare la pipeline e suddividere il testo di input in parole usando la trasformazione [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) per suddividere il testo in parole come riga di codice successiva:

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   La trasformazione [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) usa gli spazi per analizzare la stringa di testo in parole. Crea una nuova colonna e suddivide ogni stringa di input in un vettore di sottostringhe in base al separatore definito dall'utente.

1. Eseguire il mapping delle parole sulla codifica Integer usando la tabella di ricerca dichiarata in precedenza:

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. Ridimensionare le codifiche Integer a lunghezza variabile a una lunghezza fissa richiesta dal modello:

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. Classificare l'input con il modello TensorFlow caricato:

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    L'output del modello TensorFlow è denominato `Prediction/Softmax`. Si noti che il nome `Prediction/Softmax` è determinato dal modello TensorFlow. Non è possibile modificare questo nome.

1. Crea una nuova colonna per la stima di output:

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    È necessario copiare la colonna `Prediction/Softmax` in una colonna con un nome che può essere usato come proprietà in una C# classe: `Prediction`. Il carattere `/` non è consentito in un C# nome di proprietà.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Creare il modello ML.NET dalla pipeline

1. Aggiungere il codice per creare il modello dalla pipeline:

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    Un modello ML.NET viene creato dalla catena di estimatori nella pipeline chiamando il metodo `Fit`. In questo caso, i dati non vengono adattati per la creazione del modello, perché è già stato eseguito il training del modello TensorFlow. Viene fornito un oggetto visualizzazione dati vuoto per soddisfare i requisiti del metodo `Fit`.

## <a name="use-the-model-to-make-a-prediction"></a>Usare il modello per eseguire una stima

1. Aggiungere il metodo `PredictSentiment` al di sotto del metodo `Main`:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Aggiungere il codice seguente per creare il `PredictionEngine` come prima riga nel metodo `PredictSentiment()`:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) è un'API di praticità, che consente di eseguire una stima su una singola istanza di dati. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) non è thread-safe. È accettabile usare in ambienti a thread singolo o prototipi. Per migliorare le prestazioni e thread safety negli ambienti di produzione, usare il servizio `PredictionEnginePool`, che consente di creare un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) di [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oggetti da usare nell'applicazione. Vedere questa guida su come [usare `PredictionEnginePool` in un'API Web di ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L'estensione del servizio `PredictionEnginePool` è attualmente in anteprima.

1. Aggiungere un commento per testare la stima del modello sottoposto a training nel metodo `Predict()` creando un'istanza di `MovieReview`:

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. Passare i dati di commento del test al `Prediction Engine` aggiungendo le righe di codice seguenti nel metodo `PredictSentiment()`:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. La funzione [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) esegue una stima su una singola riga di dati:

    |Proprietà| Value|Type|
    |-------------|-----------------------|------|
    |Stima|[0,5459937, 0,454006255]|float []|

1. Visualizzare la stima del sentimento usando il codice seguente:

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. Aggiungere una chiamata a `PredictSentiment` alla fine del metodo `Main`:

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Risultati

Compilare ed eseguire l'applicazione.

I risultati dovrebbero essere simili a quanto riportato di seguito. Durante l'elaborazione, vengono visualizzati alcuni messaggi. Possono essere mostrati avvisi o messaggi relativi all'elaborazione. Questi messaggi sono stati rimossi dai risultati seguenti per maggiore chiarezza.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

La procedura è stata completata. A questo punto è stato creato un modello di apprendimento automatico per la classificazione e la stima dei sentimenti dei messaggi riutilizzando un modello di `TensorFlow` pre-sottoposto a training in ML.NET.

È possibile trovare il codice sorgente per questa esercitazione nel repository [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

In questa esercitazione si è appreso come:
> [!div class="checklist"]
>
> * Caricare un modello di TensorFlow con training preliminare
> * Trasforma il testo del commento del sito Web in funzionalità appropriate per il modello
> * Usare il modello per eseguire una stima
