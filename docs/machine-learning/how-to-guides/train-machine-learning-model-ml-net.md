---
title: Eseguire il training di un modello e valutarlo
description: Informazioni su come eseguire il training di modelli di Machine Learning e su come valutarli in ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 3a3f1f672ed078754162dc377cf5c239d206b715
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557844"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="c4883-103">Eseguire il training di un modello e valutarlo</span><span class="sxs-lookup"><span data-stu-id="c4883-103">Train and evaluate a model</span></span>

<span data-ttu-id="c4883-104">Informazioni su come compilare modelli di Machine Learning, estrarre i parametri appresi e misurare le prestazioni con ML.NET.</span><span class="sxs-lookup"><span data-stu-id="c4883-104">Learn how to build machine learning models, extract learned parameters and measure performance with ML.NET.</span></span> <span data-ttu-id="c4883-105">Questo campione esegue il training di un modello di regressione. I concetti, tuttavia, sono applicabili alla maggior parte degli altri algoritmi.</span><span class="sxs-lookup"><span data-stu-id="c4883-105">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="c4883-106">Divisione dei dati per training e test</span><span class="sxs-lookup"><span data-stu-id="c4883-106">Split data for training and testing</span></span>

<span data-ttu-id="c4883-107">L'obiettivo di un modello di Machine Learning è di identificare motivi all'interno dei dati di training.</span><span class="sxs-lookup"><span data-stu-id="c4883-107">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="c4883-108">Questi motivi vengono usati per eseguire stime con nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="c4883-108">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="c4883-109">Dato il modello di dati seguente:</span><span class="sxs-lookup"><span data-stu-id="c4883-109">Given the following data model:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="c4883-110">Caricare i dati in un'interfaccia [`IDataView`](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="c4883-110">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

<span data-ttu-id="c4883-111">Usare il metodo [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) per dividere i dati in set di training e set di test.</span><span class="sxs-lookup"><span data-stu-id="c4883-111">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="c4883-112">Il risultato sarà un oggetto [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) contenente due membri [`IDataView`](xref:Microsoft.ML.IDataView), uno per il set di training e l'altro per il set di test.</span><span class="sxs-lookup"><span data-stu-id="c4883-112">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="c4883-113">La percentuale di suddivisione dei dati è determinata dal parametro `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="c4883-113">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="c4883-114">Il frammento di codice seguente contiene il 20% dei dati originali per il set di test.</span><span class="sxs-lookup"><span data-stu-id="c4883-114">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="c4883-115">Preparare i dati</span><span class="sxs-lookup"><span data-stu-id="c4883-115">Prepare the data</span></span>

<span data-ttu-id="c4883-116">I dati devono essere pre-elaborati prima del training di un modello di Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c4883-116">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="c4883-117">Altre informazioni sulla preparazione dei dati sono reperibili nell'[articolo sulla procedura di preparazione dei dati](prepare-data-ml-net.md), nonché in [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="c4883-117">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="c4883-118">Gli algoritmi ML.NET presentano vincoli per i tipi di colonna di input.</span><span class="sxs-lookup"><span data-stu-id="c4883-118">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="c4883-119">Quando non viene specificato alcun valore, poi, vengono usati valori predefiniti per i nomi delle colonne di input e di output.</span><span class="sxs-lookup"><span data-stu-id="c4883-119">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="c4883-120">Uso di tipi di colonna previsti</span><span class="sxs-lookup"><span data-stu-id="c4883-120">Working with expected column types</span></span>

<span data-ttu-id="c4883-121">Gli algoritmi di Machine Learning in ML.NET prevedono come input un vettore float di dimensione nota.</span><span class="sxs-lookup"><span data-stu-id="c4883-121">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="c4883-122">Applicare l'attributo [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) al modello di dati quando tutti i dati sono già in formato numerico e si intende elaborarli insieme, ad esempio nel caso dei pixel di un'immagine.</span><span class="sxs-lookup"><span data-stu-id="c4883-122">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="c4883-123">Se i dati non sono tutti numerici e si vogliono applicare trasformazioni di dati diverse per ogni colonna singolarmente, usare il metodo [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) dopo che tutte le colonne sono state elaborate, per combinare tutte le colonne singole in un unico vettore di funzionalità che viene restituito come output in una nuova colonna.</span><span class="sxs-lookup"><span data-stu-id="c4883-123">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="c4883-124">Il frammento di codice seguente combina le colonne `Size` e `HistoricalPrices` in un unico vettore di funzionalità che viene restituito come output in una nuova colonna denominata `Features`.</span><span class="sxs-lookup"><span data-stu-id="c4883-124">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="c4883-125">Poiché esiste una differenza di scala, viene applicato il metodo [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) alla colonna `Features` per normalizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="c4883-125">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply tranforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="c4883-126">Uso di nomi di colonna predefiniti</span><span class="sxs-lookup"><span data-stu-id="c4883-126">Working with default column names</span></span>

<span data-ttu-id="c4883-127">Quando non vengono specificati nomi di colonna, gli algoritmi ML.NET usano nomi di colonna predefiniti.</span><span class="sxs-lookup"><span data-stu-id="c4883-127">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="c4883-128">Tutti gli strumenti di training hanno un parametro denominato `featureColumnName` per gli input dell'algoritmo e, quando applicabile, hanno anche un parametro per il valore previsto, denominato `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="c4883-128">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="c4883-129">Per impostazione predefinita, tali valori sono rispettivamente `Features` e `Label`.</span><span class="sxs-lookup"><span data-stu-id="c4883-129">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="c4883-130">Se si usa il metodo [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) durante la pre-elaborazione per creare una nuova colonna denominata `Features`, non è necessario specificare la colonna Features nei parametri dell'algoritmo, perché è già presente nell'interfaccia `IDataView` pre-elaborata.</span><span class="sxs-lookup"><span data-stu-id="c4883-130">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="c4883-131">La colonna Label è `CurrentPrice`, ma, poiché l'attributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) viene usato nel modello di dati, ML.NET rinomina la colonna `CurrentPrice` in `Label`. Questa operazione elimina la necessità di specificare il parametro `labelColumnName` per la stima dell'algoritmo di Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c4883-131">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="c4883-132">Se non si vogliono usare i nomi di colonna predefiniti, passare i nomi delle colonne Features e Label come parametri quando si definisce la stima dell'algoritmo di Machine Learning, come illustrato dal frammento di codice seguente:</span><span class="sxs-lookup"><span data-stu-id="c4883-132">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="c4883-133">Eseguire il training del modello di Machine Learning</span><span class="sxs-lookup"><span data-stu-id="c4883-133">Train the machine learning model</span></span>

<span data-ttu-id="c4883-134">Dopo che i dati sono stati pre-elaborati, usare il metodo [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) per eseguire il training del modello di Machine Learning con l'algoritmo di regressione [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).</span><span class="sxs-lookup"><span data-stu-id="c4883-134">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoodrinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="c4883-135">Estrarre i parametri del modello</span><span class="sxs-lookup"><span data-stu-id="c4883-135">Extract model parameters</span></span>

<span data-ttu-id="c4883-136">Dopo il training del modello, estrarre i parametri [`ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase%601) appresi per l'ispezione o la riesecuzione del training.</span><span class="sxs-lookup"><span data-stu-id="c4883-136">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="c4883-137">I parametri [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) offrono il valore di distorsione e i coefficienti o i pesi appresi del modello con training.</span><span class="sxs-lookup"><span data-stu-id="c4883-137">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="c4883-138">Altri modelli hanno parametri specifici per le proprie attività.</span><span class="sxs-lookup"><span data-stu-id="c4883-138">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="c4883-139">L'[algoritmo K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer), ad esempio, inserisce dati in un cluster in base al baricentro e [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contiene una proprietà che archivia i baricentri appresi.</span><span class="sxs-lookup"><span data-stu-id="c4883-139">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="c4883-140">Per altre informazioni, vedere la [ documentazione dell'API `Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) e cercare le classi con un nome contenente `ModelParameters`.</span><span class="sxs-lookup"><span data-stu-id="c4883-140">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="c4883-141">Valutare la qualità del modello</span><span class="sxs-lookup"><span data-stu-id="c4883-141">Evaluate model quality</span></span>

<span data-ttu-id="c4883-142">Per facilitare la scelta del modello dalle prestazioni migliori, è essenziale valutarne le prestazioni su dati di test.</span><span class="sxs-lookup"><span data-stu-id="c4883-142">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="c4883-143">Usare il metodo [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) per misurare diverse metriche del modello con training.</span><span class="sxs-lookup"><span data-stu-id="c4883-143">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="c4883-144">Il metodo `Evaluate` genera metriche diverse a seconda dell'attività di Machine Learning eseguita.</span><span class="sxs-lookup"><span data-stu-id="c4883-144">The `Evaluate` method produces different metrics depending on which machine learning task was was performed.</span></span> <span data-ttu-id="c4883-145">Per altri dettagli, vedere la [ documentazione dell'API `Microsoft.ML.Data`](xref:Microsoft.ML.Data) e cercare le classi con un nome contenente `Metrics`.</span><span class="sxs-lookup"><span data-stu-id="c4883-145">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="c4883-146">Nel codice di esempio precedente:</span><span class="sxs-lookup"><span data-stu-id="c4883-146">In the previous code sample:</span></span>  
1. <span data-ttu-id="c4883-147">Il set di dati di test viene pre-elaborato tramite le trasformazioni di preparazione dei dati definite in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c4883-147">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="c4883-148">Il modello di Machine Learning con training viene usato per eseguire stime sui dati di test.</span><span class="sxs-lookup"><span data-stu-id="c4883-148">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="c4883-149">Nel metodo `Evaluate` i valori nella colonna `CurrentPrice` del set di dati di test vengono confrontati con la colonna `Score` delle stime appena generate come output per calcolare le metriche per il modello di regressione, una delle quali, R quadrato, viene memorizzata nella variabile `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="c4883-149">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="c4883-150">In questo breve esempio, R quadrato è un numero non compreso nell'intervallo 0-1 a causa della dimensione limitata dei dati.</span><span class="sxs-lookup"><span data-stu-id="c4883-150">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="c4883-151">In uno scenario reale, si deve prevedere un valore compreso tra 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="c4883-151">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>