---
title: Annullare le attività asincrone rimanenti dopo il completamento di una sola attività (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 81aed54d4854ad505971fbf85cf9a080a7c392d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922008"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="8dce8-102">Annullare le attività asincrone rimanenti dopo il completamento di una sola attività (C#)</span><span class="sxs-lookup"><span data-stu-id="8dce8-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="8dce8-103">È possibile usare il metodo <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> insieme a <xref:System.Threading.CancellationToken> per annullare tutte le attività rimanenti dopo il completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="8dce8-104">Il metodo `WhenAny` accetta un argomento che rappresenta una raccolta di attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="8dce8-105">Il metodo avvia tutte le attività e restituisce una singola attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="8dce8-106">La singola attività è completa quando una qualsiasi attività nella raccolta è completata.</span><span class="sxs-lookup"><span data-stu-id="8dce8-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="8dce8-107">Questo esempio illustra come usare un token di annullamento in combinazione con `WhenAny` per terminare il completamento della prima attività della raccolta di attività e annullare le rimanenti attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="8dce8-108">Ogni attività scarica il contenuto di un sito Web.</span><span class="sxs-lookup"><span data-stu-id="8dce8-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="8dce8-109">L'esempio visualizza la lunghezza del contenuto del primo download da completare e annulla gli altri download.</span><span class="sxs-lookup"><span data-stu-id="8dce8-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8dce8-110">Per eseguire gli esempi, è necessario avere installato Visual Studio 2012 o versioni successive e .NET Framework 4.5 o versioni successive nel computer.</span><span class="sxs-lookup"><span data-stu-id="8dce8-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="8dce8-111">Download dell'esempio</span><span class="sxs-lookup"><span data-stu-id="8dce8-111">Downloading the Example</span></span>  
 <span data-ttu-id="8dce8-112">È possibile scaricare i progetti completi di Windows Presentation Foundation (WPF) da [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Esempio di codice asincrono: ottimizzazione dell'applicazione) e quindi seguire questa procedura.</span><span class="sxs-lookup"><span data-stu-id="8dce8-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="8dce8-113">Decomprimere il file scaricato e quindi avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8dce8-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="8dce8-114">Nella barra dei menu scegliere **File**, **Apri**, **Progetto/Soluzione**.</span><span class="sxs-lookup"><span data-stu-id="8dce8-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="8dce8-115">Nella finestra di dialogo **Apri progetto** aprire la cartella che contiene il codice di esempio che è stato decompresso e aprire il file di soluzione (SLN) per AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="8dce8-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="8dce8-116">In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **CancelAfterOneTask** e scegliere **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="8dce8-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="8dce8-117">Premere F5 per eseguire il progetto.</span><span class="sxs-lookup"><span data-stu-id="8dce8-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="8dce8-118">Premere CTRL + F5 per eseguire il progetto senza il debug.</span><span class="sxs-lookup"><span data-stu-id="8dce8-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="8dce8-119">Eseguire il programma più volte per verificare che diversi download terminino prima.</span><span class="sxs-lookup"><span data-stu-id="8dce8-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="8dce8-120">Se non si vuole scaricare il progetto, è possibile rivedere il file MainWindow.xaml.cs alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="8dce8-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="8dce8-121">Compilazione dell'esempio</span><span class="sxs-lookup"><span data-stu-id="8dce8-121">Building the Example</span></span>  
 <span data-ttu-id="8dce8-122">L'esempio riportato in questo argomento aggiunge codice al progetto sviluppato in [Annullare un'attività asincrona o un elenco di attività (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) per annullare un elenco di attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="8dce8-123">L'esempio usa la stessa interfaccia utente, sebbene il pulsante **Annulla** non viene usato in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="8dce8-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="8dce8-124">Per compilare l'esempio passo a passo, seguire le istruzioni nella sezione "Download dell'esempio", ma scegliere **CancelAListOfTasks** come **progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="8dce8-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="8dce8-125">Aggiungere al progetto le modifiche illustrate in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="8dce8-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="8dce8-126">Nel file MainWindow.xaml.cs del progetto **CancelAListOfTasks** avviare la transizione spostando le fasi di elaborazione per ogni sito Web dal ciclo in `AccessTheWebAsync` al metodo asincrono seguente.</span><span class="sxs-lookup"><span data-stu-id="8dce8-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="8dce8-127">In `AccessTheWebAsync`, questo esempio usa una query, il metodo <xref:System.Linq.Enumerable.ToArray%2A> e il metodo `WhenAny` per creare e avviare una matrice di attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="8dce8-128">L'applicazione di `WhenAny` alla matrice restituisce una singola attività che, quando attesa, restituisce la prima attività per raggiungere il completamento della matrice di attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="8dce8-129">Modificare `AccessTheWebAsync` nel modo seguente.</span><span class="sxs-lookup"><span data-stu-id="8dce8-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="8dce8-130">Gli asterischi contrassegnano le modifiche nel file del codice.</span><span class="sxs-lookup"><span data-stu-id="8dce8-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="8dce8-131">Aggiungere un commento o eliminare il ciclo.</span><span class="sxs-lookup"><span data-stu-id="8dce8-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="8dce8-132">Creare una query che, quando eseguita, produce una raccolta di attività generiche.</span><span class="sxs-lookup"><span data-stu-id="8dce8-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="8dce8-133">Ogni chiamata a `ProcessURLAsync` restituisce un oggetto <xref:System.Threading.Tasks.Task%601> dove `TResult` è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="8dce8-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="8dce8-134">Chiamare `ToArray` per eseguire la query e avviare le attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="8dce8-135">L'applicazione del metodo `WhenAny` nel passaggio successivo esegue la query e avvia le attività senza usare `ToArray`, ma altri metodi non farebbero lo stesso.</span><span class="sxs-lookup"><span data-stu-id="8dce8-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="8dce8-136">La procedura più sicura consiste nel forzare l'esecuzione della query in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="8dce8-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="8dce8-137">Chiamare `WhenAny` sulla raccolta di attività.</span><span class="sxs-lookup"><span data-stu-id="8dce8-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="8dce8-138">`WhenAny` restituisce `Task(Of Task(Of Integer))` o `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="8dce8-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="8dce8-139">Ovvero `WhenAny` restituisce un'attività che include un singolo `Task(Of Integer)` o `Task<int>` quando è attesa.</span><span class="sxs-lookup"><span data-stu-id="8dce8-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="8dce8-140">L'attività singola è la prima attività della raccolta da completare.</span><span class="sxs-lookup"><span data-stu-id="8dce8-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="8dce8-141">L'attività completata per prima viene assegnata a `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="8dce8-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="8dce8-142">Il tipo di `firstFinishedTask` è <xref:System.Threading.Tasks.Task%601> dove `TResult` è un numero intero perché è il tipo restituito di `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="8dce8-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="8dce8-143">In questo esempio, si è interessati solo all'attività che termina per prima.</span><span class="sxs-lookup"><span data-stu-id="8dce8-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="8dce8-144">Usare quindi <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> per annullare le attività rimanenti.</span><span class="sxs-lookup"><span data-stu-id="8dce8-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="8dce8-145">Infine, attendere `firstFinishedTask` per recuperare la lunghezza del contenuto scaricato.</span><span class="sxs-lookup"><span data-stu-id="8dce8-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="8dce8-146">Eseguire il programma più volte per verificare che diversi download terminino prima.</span><span class="sxs-lookup"><span data-stu-id="8dce8-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="8dce8-147">Esempio completo</span><span class="sxs-lookup"><span data-stu-id="8dce8-147">Complete Example</span></span>  
 <span data-ttu-id="8dce8-148">Il codice seguente è il file MainWindow.xaml.cs completo per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="8dce8-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="8dce8-149">Gli asterischi contrassegnano gli elementi che sono stati aggiunti per questo esempio.</span><span class="sxs-lookup"><span data-stu-id="8dce8-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="8dce8-150">Si noti che è necessario aggiungere un riferimento per <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="8dce8-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="8dce8-151">È possibile scaricare il progetto da [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Esempio di codice asincrono: ottimizzazione dell'applicazione).</span><span class="sxs-lookup"><span data-stu-id="8dce8-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dce8-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8dce8-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="8dce8-153">Ottimizzazione dell'applicazione Async (C#)</span><span class="sxs-lookup"><span data-stu-id="8dce8-153">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="8dce8-154">Programmazione asincrona con Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="8dce8-154">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- <span data-ttu-id="8dce8-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Esempio di codice asincrono: Ottimizzazione dell'applicazione)</span><span class="sxs-lookup"><span data-stu-id="8dce8-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span></span>
