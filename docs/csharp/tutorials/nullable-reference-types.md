---
title: Progettare con tipi riferimento nullable
description: Questa esercitazione avanzata fornisce un'introduzione ai tipi riferimento nullable. Si imparerà a esprimere le finalità della progettazione in merito a quando i valori di riferimento possono essere Null e a configurare il compilatore in modo che stabilisca quando non possono essere Null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 914a1eeee2d3d1843bf597f94761e39d16331b5c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956656"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="006d5-104">Esercitazione: Esprimere più chiaramente le finalità di progettazione con tipi riferimento nullable e non nullable</span><span class="sxs-lookup"><span data-stu-id="006d5-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="006d5-105">In C# 8 sono ora disponibili i **tipi riferimento nullable**, che completano i tipi riferimento allo stesso modo in cui i tipi valore nullable completano i tipi valore.</span><span class="sxs-lookup"><span data-stu-id="006d5-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="006d5-106">Per dichiarare una variabile come **tipo riferimento nullable** basta aggiungere un `?` alla fine del tipo.</span><span class="sxs-lookup"><span data-stu-id="006d5-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="006d5-107">Ad esempio, `string?` rappresenta un tipo `string` nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="006d5-108">È possibile usare questi nuovi tipi per esprimere più chiaramente le finalità della progettazione: alcune variabili *devono avere sempre un valore*, mentre in altre *un valore può mancare*.</span><span class="sxs-lookup"><span data-stu-id="006d5-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="006d5-109">In questa esercitazione si imparerà a:</span><span class="sxs-lookup"><span data-stu-id="006d5-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="006d5-110">Incorporare tipi riferimento nullable e non nullable nelle progettazioni.</span><span class="sxs-lookup"><span data-stu-id="006d5-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="006d5-111">Abilitare i controlli dei tipi riferimento nullable in tutto il codice.</span><span class="sxs-lookup"><span data-stu-id="006d5-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="006d5-112">Scrivere codice in cui il compilatore impone tali decisioni di progettazione.</span><span class="sxs-lookup"><span data-stu-id="006d5-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="006d5-113">Usare la funzionalità dei riferimenti nullable nelle proprie progettazioni.</span><span class="sxs-lookup"><span data-stu-id="006d5-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="006d5-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="006d5-114">Prerequisites</span></span>

<span data-ttu-id="006d5-115">È necessario configurare il computer per l'esecuzione di .NET Core, incluso il C# compilatore 8,0.</span><span class="sxs-lookup"><span data-stu-id="006d5-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="006d5-116">Il C# compilatore 8 è disponibile con [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)o [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="006d5-116">The C# 8 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="006d5-117">Per questa esercitazione si presuppone che l'utente abbia familiarità con C# e .NET, inclusa l'interfaccia della riga di comando di .NET Core o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="006d5-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="006d5-118">Incorporare tipi riferimento nullable nelle progettazioni</span><span class="sxs-lookup"><span data-stu-id="006d5-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="006d5-119">In questa esercitazione si compilerà una libreria che modella l'esecuzione di un sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="006d5-120">Il codice usa tipi riferimento sia nullable che non nullable per rappresentare concetti reali.</span><span class="sxs-lookup"><span data-stu-id="006d5-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="006d5-121">Le domande del sondaggio non possono mai essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-121">The survey questions can never be null.</span></span> <span data-ttu-id="006d5-122">Un partecipante al sondaggio potrebbe preferire non rispondere a una domanda.</span><span class="sxs-lookup"><span data-stu-id="006d5-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="006d5-123">In questo caso, le risposte potrebbero essere `null`.</span><span class="sxs-lookup"><span data-stu-id="006d5-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="006d5-124">Il codice scritto per questo esempio esprime questa intenzione e il compilatore la applica.</span><span class="sxs-lookup"><span data-stu-id="006d5-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="006d5-125">Creare l'applicazione e abilitare i tipi riferimento nullable</span><span class="sxs-lookup"><span data-stu-id="006d5-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="006d5-126">Creare una nuova applicazione console in Visual Studio oppure dalla riga di comando tramite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="006d5-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="006d5-127">Assegnare all'applicazione il nome `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="006d5-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="006d5-128">Dopo aver creato l'applicazione, è necessario specificare che l'intero progetto venga compilato in un **contesto di annotazione nullable**@no__t 0.</span><span class="sxs-lookup"><span data-stu-id="006d5-128">Once you've created the application, you'll need to specify that the entire project compiles in an `enabled` **nullable annotation context**.</span></span> <span data-ttu-id="006d5-129">Aprire il file `csproj` e aggiungere un elemento `Nullable` all'elemento `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="006d5-129">Open the `csproj` file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="006d5-130">Impostarne il valore su `enabled`.</span><span class="sxs-lookup"><span data-stu-id="006d5-130">Set its value to `enabled`.</span></span> <span data-ttu-id="006d5-131">È necessario acconsentire esplicitamente alle funzionalità dei **tipi riferimento nullable**, anche nei progetti C# 8.</span><span class="sxs-lookup"><span data-stu-id="006d5-131">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="006d5-132">Questo perché dopo che la funzionalità viene attivata, le dichiarazioni di variabili di riferimento esistenti diventano **tipi riferimento non nullable**.</span><span class="sxs-lookup"><span data-stu-id="006d5-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="006d5-133">Sebbene questa decisione consenta di individuare i problemi per cui il codice esistente potrebbe non avere controlli null appropriati, potrebbe non riflettere accuratamente la finalità di progettazione originale:</span><span class="sxs-lookup"><span data-stu-id="006d5-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="006d5-134">Progettare i tipi per l'applicazione</span><span class="sxs-lookup"><span data-stu-id="006d5-134">Design the types for the application</span></span>

<span data-ttu-id="006d5-135">Per questa applicazione di sondaggio è necessario creare alcune classi:</span><span class="sxs-lookup"><span data-stu-id="006d5-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="006d5-136">Una classe che modella l'elenco di domande.</span><span class="sxs-lookup"><span data-stu-id="006d5-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="006d5-137">Una classe che modella un elenco di persone contattate per il sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="006d5-138">Una classe che modella le risposte di una persona che ha partecipato al sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="006d5-139">Questi tipi useranno tipi riferimento sia nullable sia non nullable per indicare i membri obbligatori e quelli facoltativi.</span><span class="sxs-lookup"><span data-stu-id="006d5-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="006d5-140">I tipi riferimento nullable comunicano chiaramente questa finalità della progettazione:</span><span class="sxs-lookup"><span data-stu-id="006d5-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="006d5-141">Le domande che fanno parte del sondaggio non possono mai essere Null: non ha senso porre una domanda vuota.</span><span class="sxs-lookup"><span data-stu-id="006d5-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="006d5-142">I partecipanti al sondaggio non possono mai essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-142">The respondents can never be null.</span></span> <span data-ttu-id="006d5-143">Si vuole infatti tenere traccia delle persone che sono state contattate, anche quelle che non hanno accettato di partecipare.</span><span class="sxs-lookup"><span data-stu-id="006d5-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="006d5-144">Una risposta a una domanda può essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-144">Any response to a question may be null.</span></span> <span data-ttu-id="006d5-145">I partecipanti possono infatti rifiutarsi di rispondere ad alcune o a tutte le domande.</span><span class="sxs-lookup"><span data-stu-id="006d5-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="006d5-146">Se è stata eseguita la C#programmazione in, è possibile che si sia abituati a fare riferimento ai tipi che consentono valori `null` che potrebbero avere perso altre opportunità per dichiarare istanze non nullable:</span><span class="sxs-lookup"><span data-stu-id="006d5-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="006d5-147">La raccolta delle domande deve essere non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="006d5-148">La raccolta dei partecipanti deve essere non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="006d5-149">Quando si scrive il codice, si noterà che un tipo di riferimento non nullable come valore predefinito per i riferimenti evita errori comuni che potrebbero causare <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="006d5-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="006d5-150">Una lezione di questa esercitazione consiste nel prendere decisioni sulle variabili che possono o non essere `null`.</span><span class="sxs-lookup"><span data-stu-id="006d5-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="006d5-151">Nelle versioni precedenti il linguaggio non forniva la sintassi necessaria per esprimere queste decisioni.</span><span class="sxs-lookup"><span data-stu-id="006d5-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="006d5-152">Ora invece tutto questo è possibile.</span><span class="sxs-lookup"><span data-stu-id="006d5-152">Now it does.</span></span>

<span data-ttu-id="006d5-153">L'app da compilare esegue i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="006d5-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="006d5-154">Consente di creare un sondaggio e di aggiungere domande.</span><span class="sxs-lookup"><span data-stu-id="006d5-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="006d5-155">Crea un set pseudo-casuale di intervistati per il sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="006d5-156">Contatta gli intervistati fino a quando la dimensione del sondaggio completata raggiunge il numero obiettivo.</span><span class="sxs-lookup"><span data-stu-id="006d5-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="006d5-157">Scrive statistiche importanti sulle risposte del sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="006d5-158">Compilare il sondaggio con tipi nullable e non nullable</span><span class="sxs-lookup"><span data-stu-id="006d5-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="006d5-159">Il primo codice scritto crea il sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="006d5-160">Occorre scrivere le classi necessarie per modellare una domanda del sondaggio e l'esecuzione del sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="006d5-161">Il sondaggio include tre tipi di domande, distinti in base al formato della risposta: risposte Sì/No, risposte numeriche e risposte di testo.</span><span class="sxs-lookup"><span data-stu-id="006d5-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="006d5-162">Creare una classe `public SurveyQuestion`:</span><span class="sxs-lookup"><span data-stu-id="006d5-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="006d5-163">Il compilatore interpreta ogni dichiarazione di variabile del tipo riferimento come tipo riferimento **non nullable** per il codice in un contesto abilitato per nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="006d5-164">È possibile vedere il primo avviso aggiungendo le proprietà del testo della domanda e il tipo di domanda, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="006d5-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="006d5-165">Poiché `QuestionText` non è stato inizializzato, il compilatore genera un avviso che informa che una proprietà non nullable non è stata inizializzata.</span><span class="sxs-lookup"><span data-stu-id="006d5-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="006d5-166">Un requisito della progettazione è che il testo della domanda non sia Null, pertanto occorre aggiunge un costruttore per inizializzare questa proprietà e anche il valore `QuestionType`.</span><span class="sxs-lookup"><span data-stu-id="006d5-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="006d5-167">La definizione finale della classe è simile al codice seguente:</span><span class="sxs-lookup"><span data-stu-id="006d5-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="006d5-168">Aggiungendo il costruttore, l'avviso viene rimosso.</span><span class="sxs-lookup"><span data-stu-id="006d5-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="006d5-169">Anche l'argomento del costruttore è un tipo riferimento non nullable, quindi il compilatore non genera alcun avviso.</span><span class="sxs-lookup"><span data-stu-id="006d5-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="006d5-170">Creare quindi una classe `public` denominata `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="006d5-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="006d5-171">Questa classe contiene un elenco di metodi e oggetti `SurveyQuestion` per aggiungere domande al sondaggio, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="006d5-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="006d5-172">Anche in questo caso occorre inizializzare l'oggetto elenco su un valore non Null per evitare che il compilatore generi un avviso.</span><span class="sxs-lookup"><span data-stu-id="006d5-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="006d5-173">Nel secondo overload di `AddQuestion` non ci sono controlli dei valori Null in quanto non sono necessari: la variabile è stata infatti dichiarata come non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="006d5-174">Il suo valore non può essere `null`.</span><span class="sxs-lookup"><span data-stu-id="006d5-174">Its value can't be `null`.</span></span>

<span data-ttu-id="006d5-175">Passare a *Program.cs* nell'editor e sostituire il contenuto di `Main` con le righe di codice seguenti:</span><span class="sxs-lookup"><span data-stu-id="006d5-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="006d5-176">Dato che l'intero progetto è in un contesto abilitato per nullable, verranno generati avvisi quando si passa `null` a qualsiasi metodo che prevede un tipo riferimento non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-176">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="006d5-177">Provare ad aggiungere la riga seguente a `Main`:</span><span class="sxs-lookup"><span data-stu-id="006d5-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="006d5-178">Creare i partecipanti e ottenere le risposte al sondaggio</span><span class="sxs-lookup"><span data-stu-id="006d5-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="006d5-179">A questo punto occorre scrivere il codice che genera le risposte al sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="006d5-180">Questo processo include varie piccole attività:</span><span class="sxs-lookup"><span data-stu-id="006d5-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="006d5-181">Compilare un metodo che generi gli oggetti partecipante.</span><span class="sxs-lookup"><span data-stu-id="006d5-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="006d5-182">Questi oggetti rappresentano le persone a cui è stato chiesto di completare il sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="006d5-183">Creare la logica per simulare la formulazione delle domande a un partecipante e la raccolta delle risposte oppure di nessun dato, se il partecipante non ha risposto.</span><span class="sxs-lookup"><span data-stu-id="006d5-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="006d5-184">Ripetere finché non ha risposto al sondaggio un numero sufficiente di partecipanti.</span><span class="sxs-lookup"><span data-stu-id="006d5-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="006d5-185">A questo punto occorre aggiungere una classe che rappresenti una risposta al sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="006d5-186">Abilitare il supporto dei tipi riferimento nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-186">Enable nullable support.</span></span> <span data-ttu-id="006d5-187">Aggiungere una proprietà `Id` e un costruttore che la inizializza, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="006d5-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="006d5-188">Quindi aggiungere un metodo `static` per la creazione di nuovi partecipanti tramite la generazione di un ID casuale:</span><span class="sxs-lookup"><span data-stu-id="006d5-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="006d5-189">La responsabilità principale di questa classe è generare le risposte di un partecipante alle domande del sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="006d5-190">A questo scopo è necessario eseguire i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="006d5-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="006d5-191">Chiedere di partecipare al sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-191">Ask for participation in the survey.</span></span> <span data-ttu-id="006d5-192">Se la persona non acconsente, restituire una risposta mancante (o Null).</span><span class="sxs-lookup"><span data-stu-id="006d5-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="006d5-193">Porre ogni domanda e registrare la risposta.</span><span class="sxs-lookup"><span data-stu-id="006d5-193">Ask each question and record the answer.</span></span> <span data-ttu-id="006d5-194">Ogni risposta può anche essere mancante (o Null).</span><span class="sxs-lookup"><span data-stu-id="006d5-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="006d5-195">Aggiungere il codice seguente alla classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="006d5-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="006d5-196">L'archivio per le risposte del sondaggio è un `Dictionary<int, string>?`, a indicare che può essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="006d5-197">Si sta usando la nuova funzionalità del linguaggio per dichiarare la finalità della progettazione, sia al compilatore che a chiunque legga il codice successivamente.</span><span class="sxs-lookup"><span data-stu-id="006d5-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="006d5-198">Se si dereferenziano `surveyResponses` senza prima verificare il valore di `null`, verrà visualizzato un avviso del compilatore.</span><span class="sxs-lookup"><span data-stu-id="006d5-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="006d5-199">Non si riceve un avviso nel metodo `AnswerSurvey` perché il compilatore è in grado di determinare che la variabile `surveyResponses` è stata impostata su un valore non Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="006d5-200">L'uso di `null` per le risposte mancanti evidenzia un aspetto essenziale per l'utilizzo dei tipi riferimento nullable, ovvero l'obiettivo non è rimuovere tutti i valori `null` dal programma.</span><span class="sxs-lookup"><span data-stu-id="006d5-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="006d5-201">L'obiettivo è invece quello di assicurarsi che il codice scritto esprima lo scopo della progettazione.</span><span class="sxs-lookup"><span data-stu-id="006d5-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="006d5-202">I valori mancanti sono un concetto necessario da esprimere nel codice.</span><span class="sxs-lookup"><span data-stu-id="006d5-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="006d5-203">Il valore `null` rappresenta un modo chiaro per esprimere tali valori mancanti.</span><span class="sxs-lookup"><span data-stu-id="006d5-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="006d5-204">Il tentativo di rimuovere tutti i valori `null` porta solo alla definizione di un altro modo per esprimere i valori mancanti senza `null`.</span><span class="sxs-lookup"><span data-stu-id="006d5-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="006d5-205">A questo punto occorre scrivere il metodo `PerformSurvey` nella classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="006d5-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="006d5-206">Aggiungere il codice seguente nella classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="006d5-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="006d5-207">Anche in questo caso la scelta di un `List<SurveyResponse>?` nullable indica che la risposta può essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="006d5-208">Indica che il sondaggio non è ancora stato distribuito ad alcun partecipante.</span><span class="sxs-lookup"><span data-stu-id="006d5-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="006d5-209">Si noti che i partecipanti continuano a essere aggiunti finché non acconsente un numero sufficiente.</span><span class="sxs-lookup"><span data-stu-id="006d5-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="006d5-210">L'ultimo passaggio dell'esecuzione del sondaggio consiste nell'aggiungere una chiamata per eseguire il sondaggio alla fine del metodo `Main`:</span><span class="sxs-lookup"><span data-stu-id="006d5-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="006d5-211">Esaminare le risposte al sondaggio</span><span class="sxs-lookup"><span data-stu-id="006d5-211">Examine survey responses</span></span>

<span data-ttu-id="006d5-212">L'ultimo passaggio è la visualizzazione dei risultati del sondaggio.</span><span class="sxs-lookup"><span data-stu-id="006d5-212">The last step is to display survey results.</span></span> <span data-ttu-id="006d5-213">Occorre aggiungere codice a molte delle classi scritte.</span><span class="sxs-lookup"><span data-stu-id="006d5-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="006d5-214">Questo codice dimostra il valore della distinzione fra i tipi riferimento nullable e non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="006d5-215">Per iniziare, aggiungere i due membri con corpo di espressione seguenti alla classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="006d5-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="006d5-216">Poiché `surveyResponses` è un tipo di riferimento Nullable, i controlli null sono necessari prima di dereferenziarli.</span><span class="sxs-lookup"><span data-stu-id="006d5-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="006d5-217">Il metodo `Answer` restituisce una stringa che non ammette i valori null, pertanto è necessario coprire il caso di una risposta mancante usando l'operatore di Unione null.</span><span class="sxs-lookup"><span data-stu-id="006d5-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="006d5-218">Aggiungere quindi questi tre membri con corpo di espressione alla classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="006d5-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="006d5-219">Il membro `AllParticipants` deve tenere conto del fatto che la variabile `respondents` potrebbe essere Null, ma il valore restituito non può essere Null.</span><span class="sxs-lookup"><span data-stu-id="006d5-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="006d5-220">Se si modifica l'espressione rimuovendo `??` e la sequenza vuota che segue, il compilatore avvisa che il metodo potrebbe restituire `null` e la sua firma restituita restituisce un tipo non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="006d5-221">Infine, aggiungere il ciclo seguente alla fine del metodo `Main`:</span><span class="sxs-lookup"><span data-stu-id="006d5-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="006d5-222">Non è necessario eseguire alcun controllo dei valori `null` in questo codice perché le interfacce sottostanti sono state progettate in modo che restituiscano tutte tipi di riferimento non nullable.</span><span class="sxs-lookup"><span data-stu-id="006d5-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="006d5-223">Ottenere il codice</span><span class="sxs-lookup"><span data-stu-id="006d5-223">Get the code</span></span>

<span data-ttu-id="006d5-224">Il codice dell'esercitazione completata è disponibile nel repository [samples](https://github.com/dotnet/samples) nella cartella [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="006d5-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="006d5-225">È possibile fare delle prove cambiando le dichiarazioni di tipo fra tipi riferimento nullable e non nullable</span><span class="sxs-lookup"><span data-stu-id="006d5-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="006d5-226">e osservare come vengono generati avvisi diversi per assicurare che non venga dereferenziato accidentalmente un valore `null`.</span><span class="sxs-lookup"><span data-stu-id="006d5-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="006d5-227">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="006d5-227">Next steps</span></span>

<span data-ttu-id="006d5-228">Ottenere altre informazioni eseguendo la migrazione di un'applicazione esistente per usare i tipi riferimento nullable:</span><span class="sxs-lookup"><span data-stu-id="006d5-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="006d5-229">Aggiornare un'app per i tipi riferimento nullable</span><span class="sxs-lookup"><span data-stu-id="006d5-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
