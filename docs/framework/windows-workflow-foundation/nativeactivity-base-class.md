---
title: Classe di base NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989556"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="8abd0-102">Classe di base NativeActivity</span><span class="sxs-lookup"><span data-stu-id="8abd0-102">NativeActivity Base Class</span></span>

<span data-ttu-id="8abd0-103"><xref:System.Activities.NativeActivity> è una classe astratta con un costruttore protetto.</span><span class="sxs-lookup"><span data-stu-id="8abd0-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="8abd0-104">Come l'oggetto <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> viene usato per la scrittura del comportamento imperativo implementando un metodo <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="8abd0-105">A differenza dell'oggetto <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> dispone di accesso a tutte le funzionalità esposte dell'esecuzione del flusso di lavoro tramite l'oggetto <xref:System.Activities.NativeActivityContext> passato al metodo <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="8abd0-106">Uso di NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="8abd0-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="8abd0-107">L'accesso a funzionalità dell'esecuzione del flusso di lavoro può essere eseguito dall'interno del metodo <xref:System.Activities.NativeActivity.Execute%2A> tramite i membri del parametro `context`, di tipo <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="8abd0-108">Tra le funzionalità disponibili tramite l'oggetto <xref:System.Activities.NativeActivityContext> sono incluse le seguenti:</span><span class="sxs-lookup"><span data-stu-id="8abd0-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="8abd0-109">Recupero e impostazione di argomenti e variabili.</span><span class="sxs-lookup"><span data-stu-id="8abd0-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="8abd0-110">Pianificazione delle attività figlio con il metodo <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="8abd0-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="8abd0-111">Interruzione dell'esecuzione di attività tramite il metodo <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="8abd0-112">Annullamento dell'esecuzione di oggetti figlio tramite i metodi <xref:System.Activities.NativeActivityContext.CancelChild%2A> e <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="8abd0-113">Accesso ai segnalibri delle attività tramite metodi come <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> e <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="8abd0-114">Funzionalità di rilevamento personalizzate tramite <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="8abd0-115">Accesso alle proprietà di esecuzione e a quelle del valore dell'attività tramite i metodi <xref:System.Activities.CodeActivityContext.GetProperty%2A> e <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="8abd0-116">Pianificazione di azioni e funzioni di attività tramite <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> e <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="8abd0-117">Per creare un'attività personalizzata che eredita da NativeActivity</span><span class="sxs-lookup"><span data-stu-id="8abd0-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="8abd0-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8abd0-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="8abd0-119">Selezionare **file**, **nuovo**e quindi **progetto**.</span><span class="sxs-lookup"><span data-stu-id="8abd0-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="8abd0-120">Selezionare **Workflow 4,0** in **Visual C#**  nella finestra **Tipi progetto** e selezionare il nodo **v2010** .</span><span class="sxs-lookup"><span data-stu-id="8abd0-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="8abd0-121">Selezionare **libreria attività** nella finestra **modelli** .</span><span class="sxs-lookup"><span data-stu-id="8abd0-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="8abd0-122">Assegnare al nuovo progetto il nome HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="8abd0-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="8abd0-123">Fare clic con il pulsante destro del mouse su Activity1. XAML nel progetto HelloActivity e selezionare **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="8abd0-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="8abd0-124">Fare clic con il pulsante destro del mouse sul progetto HelloActivity, scegliere **Aggiungi**, quindi **classe**.</span><span class="sxs-lookup"><span data-stu-id="8abd0-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="8abd0-125">Assegnare alla nuova classe il nome HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="8abd0-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="8abd0-126">Nel file HelloActivity.cs aggiungere le seguenti istruzioni `using`.</span><span class="sxs-lookup"><span data-stu-id="8abd0-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="8abd0-127">Assicurarsi che la nuova classe erediti dall'oggetto <xref:System.Activities.NativeActivity> aggiungendo una classe base alla dichiarazione di classe.</span><span class="sxs-lookup"><span data-stu-id="8abd0-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="8abd0-128">Aggiungere la funzionalità alla classe aggiungendo un metodo <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="8abd0-129">Eseguire l'override del metodo <xref:System.Activities.NativeActivity.CacheMetadata%2A> e chiamare il metodo Add appropriato per inviare al runtime del flusso di lavoro le informazioni sulle variabili, gli argomenti, gli elementi figlio e i delegati dell'attività personalizzata.</span><span class="sxs-lookup"><span data-stu-id="8abd0-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="8abd0-130">Per altre informazioni, vedere la classe <xref:System.Activities.NativeActivityMetadata>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="8abd0-131">Usare l'oggetto <xref:System.Activities.NativeActivityContext> per pianificare un segnalibro.</span><span class="sxs-lookup"><span data-stu-id="8abd0-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="8abd0-132">Per informazioni dettagliate sulla creazione, pianificazione e ripresa di un segnalibro, vedere <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>.</span><span class="sxs-lookup"><span data-stu-id="8abd0-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
