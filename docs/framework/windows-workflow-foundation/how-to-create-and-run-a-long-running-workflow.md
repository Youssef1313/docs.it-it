---
title: 'Procedura: Creare ed eseguire un flusso di lavoro con esecuzione prolungata'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 15ee10120f4d4c92bdc95cb48cb3cb838f526343
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044373"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="22498-102">Procedura: Creare ed eseguire un flusso di lavoro con esecuzione prolungata</span><span class="sxs-lookup"><span data-stu-id="22498-102">How to: Create and Run a Long Running Workflow</span></span>

<span data-ttu-id="22498-103">Una delle principali funzionalità di Windows Workflow Foundation (WF) è la capacità del runtime di salvare in modo permanente e scaricare flussi di lavoro inattivi in un database.</span><span class="sxs-lookup"><span data-stu-id="22498-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="22498-104">I passaggi in [procedura: Eseguire un flusso](how-to-run-a-workflow.md) di lavoro ha dimostrato le nozioni di base dell'hosting del flusso di lavoro tramite un'applicazione console</span><span class="sxs-lookup"><span data-stu-id="22498-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="22498-105">Sono stati mostrati esempi relativi all'avvio di flussi di lavoro, di gestori del ciclo di vita del flusso di lavoro e di ripresa dei segnalibri.</span><span class="sxs-lookup"><span data-stu-id="22498-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="22498-106">Per illustrare la persistenza del flusso di lavoro in modo efficace, è necessario un host del flusso di lavoro più complesso che supporta l'avvio e la ripresa di più istanze del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="22498-107">In questo passaggio dell'esercitazione viene illustrato come creare un'applicazione host Windows Form che supporta l'avvio e la ripresa di più istanze del flusso di lavoro e la persistenza del flusso di lavoro e vengono fornite informazioni di base per le funzionalità avanzate, ad esempio il rilevamento e il controllo delle versioni illustrati nei passaggi successivi dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="22498-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="22498-108">Questo passaggio dell'esercitazione e i passaggi successivi usano tutti e tre i [tipi di flusso di lavoro: Creare un flusso](how-to-create-a-workflow.md)di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="22498-109">Se non sono stati completati tutti e tre i tipi, è possibile scaricare una versione completa dei passaggi da [Windows Workflow Foundation (WF45)-Introduzione esercitazione](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="22498-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="22498-110">Per scaricare una versione completa o visualizzare una procedura dettagliata del video dell'esercitazione, vedere [Windows Workflow Foundation (WF45)-Introduzione esercitazione](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="22498-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="22498-111">Contenuto dell'argomento</span><span class="sxs-lookup"><span data-stu-id="22498-111">In this topic</span></span>

- [<span data-ttu-id="22498-112">Per creare il database di persistenza</span><span class="sxs-lookup"><span data-stu-id="22498-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [<span data-ttu-id="22498-113">Per aggiungere il riferimento agli assembly DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="22498-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [<span data-ttu-id="22498-114">Per creare il form host del flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [<span data-ttu-id="22498-115">Per aggiungere le proprietà e i metodi di supporto del form</span><span class="sxs-lookup"><span data-stu-id="22498-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [<span data-ttu-id="22498-116">Per configurare l'archivio di istanze, i gestori del ciclo di vita del flusso di lavoro e le estensioni</span><span class="sxs-lookup"><span data-stu-id="22498-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [<span data-ttu-id="22498-117">Per abilitare l'avvio e la ripresa di più tipi di flussi di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [<span data-ttu-id="22498-118">Per avviare un nuovo flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [<span data-ttu-id="22498-119">Per riprendere un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [<span data-ttu-id="22498-120">Per terminare un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [<span data-ttu-id="22498-121">Per compilare ed eseguire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="22498-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="22498-122">Per creare il database di persistenza</span><span class="sxs-lookup"><span data-stu-id="22498-122">To create the persistence database</span></span>

1. <span data-ttu-id="22498-123">Aprire SQL Server Management Studio e connettersi al server locale, ad esempio **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="22498-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="22498-124">Fare clic con il pulsante destro del mouse sul nodo **database** nel server locale e selezionare **nuovo database**.</span><span class="sxs-lookup"><span data-stu-id="22498-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="22498-125">Assegnare al nuovo database il nome **WF45GettingStartedTutorial**, accettare tutti gli altri valori e selezionare **OK**.</span><span class="sxs-lookup"><span data-stu-id="22498-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="22498-126">Assicurarsi di disporre dell'autorizzazione **create database** nel server locale prima di creare il database.</span><span class="sxs-lookup"><span data-stu-id="22498-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="22498-127">Scegliere **Apri**dal menu **file** .</span><span class="sxs-lookup"><span data-stu-id="22498-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="22498-128">Passare alla cartella seguente: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="22498-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

    <span data-ttu-id="22498-129">Selezionare i due file seguenti e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="22498-129">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="22498-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="22498-130">SqlWorkflowInstanceStoreLogic.sql</span></span>

    - <span data-ttu-id="22498-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="22498-131">SqlWorkflowInstanceStoreSchema.sql</span></span>

3. <span data-ttu-id="22498-132">Scegliere **SqlWorkflowInstanceStoreSchema. SQL** dal menu **finestra** .</span><span class="sxs-lookup"><span data-stu-id="22498-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="22498-133">Verificare che **WF45GettingStartedTutorial** sia selezionato nell'elenco a discesa **database disponibili** e scegliere **Esegui** dal menu **query** .</span><span class="sxs-lookup"><span data-stu-id="22498-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="22498-134">Scegliere **SqlWorkflowInstanceStoreLogic. SQL** dal menu **finestra** .</span><span class="sxs-lookup"><span data-stu-id="22498-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="22498-135">Verificare che **WF45GettingStartedTutorial** sia selezionato nell'elenco a discesa **database disponibili** e scegliere **Esegui** dal menu **query** .</span><span class="sxs-lookup"><span data-stu-id="22498-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="22498-136">È importante eseguire i due passaggi precedenti nell'ordine corretto.</span><span class="sxs-lookup"><span data-stu-id="22498-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="22498-137">Se le query vengono eseguite senza rispettare l'ordine, si verificano degli errori e il database di persistenza non viene configurato correttamente.</span><span class="sxs-lookup"><span data-stu-id="22498-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

### <a name="BKMK_AddReference"></a><span data-ttu-id="22498-138">Per aggiungere il riferimento agli assembly DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="22498-138">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="22498-139">Fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** in **Esplora soluzioni** e scegliere **Aggiungi riferimento**.</span><span class="sxs-lookup"><span data-stu-id="22498-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="22498-140">Selezionare **assembly** dall'elenco **Aggiungi riferimento** e digitare `DurableInstancing` nella casella **Cerca assembly** .</span><span class="sxs-lookup"><span data-stu-id="22498-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="22498-141">In questo modo gli assembly vengono filtrati ed è più semplice selezionare i riferimenti desiderati.</span><span class="sxs-lookup"><span data-stu-id="22498-141">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="22498-142">Selezionare la casella di controllo accanto a **System. Activities. DurableInstancing** e **System. Runtime. DurableInstancing** dall'elenco **dei risultati della ricerca** , quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="22498-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

### <a name="BKMK_CreateForm"></a><span data-ttu-id="22498-143">Per creare il form host del flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-143">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="22498-144">Nei passaggi di questa procedura viene descritto come aggiungere e configurare manualmente il form.</span><span class="sxs-lookup"><span data-stu-id="22498-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="22498-145">Se si desidera, è possibile scaricare i file della soluzione per l'esercitazione e aggiungere il form completato al progetto.</span><span class="sxs-lookup"><span data-stu-id="22498-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="22498-146">Per scaricare i file dell'esercitazione, vedere [Windows Workflow Foundation (WF45)-Introduzione esercitazione](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="22498-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="22498-147">Una volta scaricati i file, fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** e scegliere **Aggiungi riferimento**.</span><span class="sxs-lookup"><span data-stu-id="22498-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="22498-148">Aggiungere un riferimento a **System. Windows. Forms** e **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="22498-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="22498-149">Questi riferimenti vengono aggiunti automaticamente se si aggiunge un nuovo modulo dal menu **Aggiungi**, **nuovo elemento** , ma è necessario aggiungerlo manualmente durante l'importazione di un modulo.</span><span class="sxs-lookup"><span data-stu-id="22498-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="22498-150">Una volta aggiunti i riferimenti, fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** in **Esplora soluzioni** e scegliere **Aggiungi**, **elemento esistente**.</span><span class="sxs-lookup"><span data-stu-id="22498-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="22498-151">Passare `Form` alla cartella nei file di progetto, selezionare **WorkflowHostForm.cs** (o **WorkflowHostForm. vb**) e fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="22498-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="22498-152">Se si sceglie di importare il form, è possibile passare alla sezione successiva [per aggiungere le proprietà e i metodi helper del modulo](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="22498-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>

1. <span data-ttu-id="22498-153">Fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** in **Esplora soluzioni** e scegliere **Aggiungi**, **nuovo elemento**.</span><span class="sxs-lookup"><span data-stu-id="22498-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="22498-154">Nell'elenco modelli **installati** scegliere **Windows Form**, digitare `WorkflowHostForm` nella casella **nome** e fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="22498-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="22498-155">Configurare le seguenti proprietà nel form.</span><span class="sxs-lookup"><span data-stu-id="22498-155">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="22498-156">Proprietà</span><span class="sxs-lookup"><span data-stu-id="22498-156">Property</span></span>|<span data-ttu-id="22498-157">Valore</span><span class="sxs-lookup"><span data-stu-id="22498-157">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="22498-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="22498-158">FormBorderStyle</span></span>|<span data-ttu-id="22498-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="22498-159">FixedSingle</span></span>|
    |<span data-ttu-id="22498-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="22498-160">MaximizeBox</span></span>|<span data-ttu-id="22498-161">False</span><span class="sxs-lookup"><span data-stu-id="22498-161">False</span></span>|
    |<span data-ttu-id="22498-162">Dimensione</span><span class="sxs-lookup"><span data-stu-id="22498-162">Size</span></span>|<span data-ttu-id="22498-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="22498-163">400, 420</span></span>|

4. <span data-ttu-id="22498-164">Aggiungere i controlli seguenti al form nell'ordine specificato e configurare le proprietà come indicato.</span><span class="sxs-lookup"><span data-stu-id="22498-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="22498-165">Control</span><span class="sxs-lookup"><span data-stu-id="22498-165">Control</span></span>|<span data-ttu-id="22498-166">Proprietà Value</span><span class="sxs-lookup"><span data-stu-id="22498-166">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="22498-167">**Pulsante**</span><span class="sxs-lookup"><span data-stu-id="22498-167">**Button**</span></span>|<span data-ttu-id="22498-168">Nome: NewGame</span><span class="sxs-lookup"><span data-stu-id="22498-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="22498-169">Percorso: 13, 13</span><span class="sxs-lookup"><span data-stu-id="22498-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="22498-170">Dimensione: 75, 23</span><span class="sxs-lookup"><span data-stu-id="22498-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="22498-171">Testo Nuova partita</span><span class="sxs-lookup"><span data-stu-id="22498-171">Text: New Game</span></span>|
    |<span data-ttu-id="22498-172">**Etichetta**</span><span class="sxs-lookup"><span data-stu-id="22498-172">**Label**</span></span>|<span data-ttu-id="22498-173">Percorso: 94, 18</span><span class="sxs-lookup"><span data-stu-id="22498-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="22498-174">Testo Immettere un numero da 1 a</span><span class="sxs-lookup"><span data-stu-id="22498-174">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="22498-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="22498-175">**ComboBox**</span></span>|<span data-ttu-id="22498-176">Nome: NumberRange</span><span class="sxs-lookup"><span data-stu-id="22498-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="22498-177">DropDownStyle DropDownList</span><span class="sxs-lookup"><span data-stu-id="22498-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="22498-178">Elementi: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="22498-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="22498-179">Percorso: 228, 12</span><span class="sxs-lookup"><span data-stu-id="22498-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="22498-180">Dimensione: 143, 21</span><span class="sxs-lookup"><span data-stu-id="22498-180">Size: 143, 21</span></span>|
    |<span data-ttu-id="22498-181">**Etichetta**</span><span class="sxs-lookup"><span data-stu-id="22498-181">**Label**</span></span>|<span data-ttu-id="22498-182">Percorso: 13, 43</span><span class="sxs-lookup"><span data-stu-id="22498-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="22498-183">Testo Tipo di flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-183">Text: Workflow type</span></span>|
    |<span data-ttu-id="22498-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="22498-184">**ComboBox**</span></span>|<span data-ttu-id="22498-185">Nome: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="22498-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="22498-186">DropDownStyle DropDownList</span><span class="sxs-lookup"><span data-stu-id="22498-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="22498-187">Elementi: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="22498-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="22498-188">Percorso: 94, 40</span><span class="sxs-lookup"><span data-stu-id="22498-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="22498-189">Dimensione: 277, 21</span><span class="sxs-lookup"><span data-stu-id="22498-189">Size: 277, 21</span></span>|
    |<span data-ttu-id="22498-190">**Etichetta**</span><span class="sxs-lookup"><span data-stu-id="22498-190">**Label**</span></span>|<span data-ttu-id="22498-191">Nome: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="22498-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="22498-192">Percorso: 13, 362</span><span class="sxs-lookup"><span data-stu-id="22498-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="22498-193">Testo Versione flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-193">Text: Workflow version</span></span>|
    |<span data-ttu-id="22498-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="22498-194">**GroupBox**</span></span>|<span data-ttu-id="22498-195">Percorso: 13, 67</span><span class="sxs-lookup"><span data-stu-id="22498-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="22498-196">Dimensione: 358, 287</span><span class="sxs-lookup"><span data-stu-id="22498-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="22498-197">Testo Partita</span><span class="sxs-lookup"><span data-stu-id="22498-197">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="22498-198">Quando si aggiungono i seguenti controlli, inserirli nel GroupBox.</span><span class="sxs-lookup"><span data-stu-id="22498-198">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="22498-199">Control</span><span class="sxs-lookup"><span data-stu-id="22498-199">Control</span></span>|<span data-ttu-id="22498-200">Proprietà Value</span><span class="sxs-lookup"><span data-stu-id="22498-200">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="22498-201">**Etichetta**</span><span class="sxs-lookup"><span data-stu-id="22498-201">**Label**</span></span>|<span data-ttu-id="22498-202">Percorso: 7, 20</span><span class="sxs-lookup"><span data-stu-id="22498-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="22498-203">Testo ID istanza flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-203">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="22498-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="22498-204">**ComboBox**</span></span>|<span data-ttu-id="22498-205">Nome: InstanceId</span><span class="sxs-lookup"><span data-stu-id="22498-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="22498-206">DropDownStyle DropDownList</span><span class="sxs-lookup"><span data-stu-id="22498-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="22498-207">Percorso: 121, 17</span><span class="sxs-lookup"><span data-stu-id="22498-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="22498-208">Dimensione: 227, 21</span><span class="sxs-lookup"><span data-stu-id="22498-208">Size: 227, 21</span></span>|
    |<span data-ttu-id="22498-209">**Etichetta**</span><span class="sxs-lookup"><span data-stu-id="22498-209">**Label**</span></span>|<span data-ttu-id="22498-210">Percorso: 7, 47</span><span class="sxs-lookup"><span data-stu-id="22498-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="22498-211">Testo Proposta</span><span class="sxs-lookup"><span data-stu-id="22498-211">Text: Guess</span></span>|
    |<span data-ttu-id="22498-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="22498-212">**TextBox**</span></span>|<span data-ttu-id="22498-213">Nome: Proposta</span><span class="sxs-lookup"><span data-stu-id="22498-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="22498-214">Percorso: 50, 44</span><span class="sxs-lookup"><span data-stu-id="22498-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="22498-215">Dimensione: 65, 20</span><span class="sxs-lookup"><span data-stu-id="22498-215">Size: 65, 20</span></span>|
    |<span data-ttu-id="22498-216">**Pulsante**</span><span class="sxs-lookup"><span data-stu-id="22498-216">**Button**</span></span>|<span data-ttu-id="22498-217">Nome: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="22498-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="22498-218">Percorso: 121, 42</span><span class="sxs-lookup"><span data-stu-id="22498-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="22498-219">Dimensione: 75, 23</span><span class="sxs-lookup"><span data-stu-id="22498-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="22498-220">Testo Immetti proposta</span><span class="sxs-lookup"><span data-stu-id="22498-220">Text: Enter Guess</span></span>|
    |<span data-ttu-id="22498-221">**Pulsante**</span><span class="sxs-lookup"><span data-stu-id="22498-221">**Button**</span></span>|<span data-ttu-id="22498-222">Nome: QuitGame</span><span class="sxs-lookup"><span data-stu-id="22498-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="22498-223">Percorso: 274, 42</span><span class="sxs-lookup"><span data-stu-id="22498-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="22498-224">Dimensione: 75, 23</span><span class="sxs-lookup"><span data-stu-id="22498-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="22498-225">Testo Esci</span><span class="sxs-lookup"><span data-stu-id="22498-225">Text: Quit</span></span>|
    |<span data-ttu-id="22498-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="22498-226">**TextBox**</span></span>|<span data-ttu-id="22498-227">Nome: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="22498-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="22498-228">Percorso: 10, 73</span><span class="sxs-lookup"><span data-stu-id="22498-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="22498-229">Multiline True</span><span class="sxs-lookup"><span data-stu-id="22498-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="22498-230">ReadOnly True</span><span class="sxs-lookup"><span data-stu-id="22498-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="22498-231">Barre Vertical</span><span class="sxs-lookup"><span data-stu-id="22498-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="22498-232">Dimensione: 338, 208</span><span class="sxs-lookup"><span data-stu-id="22498-232">Size: 338, 208</span></span>|

5. <span data-ttu-id="22498-233">Impostare la proprietà **AcceptButton** del form su **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="22498-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="22498-234">Nell'esempio seguente viene illustrato il form completato.</span><span class="sxs-lookup"><span data-stu-id="22498-234">The following example illustrates the completed form.</span></span>

 ![Screenshot di un modulo host del flusso di lavoro Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="22498-236">Per aggiungere le proprietà e i metodi di supporto del form</span><span class="sxs-lookup"><span data-stu-id="22498-236">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="22498-237">Tramite i passaggi di questa sezione vengono aggiunti proprietà e metodi di supporto alla classe del form tramite cui viene configurata l'interfaccia utente del form per supportare l'esecuzione e la ripresa dei flussi di lavoro per determinare un numero.</span><span class="sxs-lookup"><span data-stu-id="22498-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="22498-238">Fare clic con il pulsante destro del mouse su **WorkflowHostForm** in **Esplora soluzioni** e scegliere **Visualizza codice**.</span><span class="sxs-lookup"><span data-stu-id="22498-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="22498-239">Aggiungere le seguenti istruzioni `using` (o `Imports`) nella parte superiore del file con le altre istruzioni `using` (o `Imports`).</span><span class="sxs-lookup"><span data-stu-id="22498-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    Imports System.Activities.DurableInstancing
    Imports System.Activities
    Imports System.Data.SqlClient
    Imports System.IO
    ```

    ```csharp
    using System.Windows.Forms;
    using System.Activities.DurableInstancing;
    using System.Activities;
    using System.Data.SqlClient;
    using System.IO;
    ```

3. <span data-ttu-id="22498-240">Aggiungere le seguenti dichiarazioni di membro alla classe **WorkflowHostForm** .</span><span class="sxs-lookup"><span data-stu-id="22498-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim WorkflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool WorkflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="22498-241">Se la stringa di connessione è diversa, aggiornare `connectionString` per fare riferimento al database.</span><span class="sxs-lookup"><span data-stu-id="22498-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="22498-242">Aggiungere una proprietà `WorkflowInstanceId` alla classe `WorkflowFormHost`.</span><span class="sxs-lookup"><span data-stu-id="22498-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

    ```vb
    Public ReadOnly Property WorkflowInstanceId() As Guid
        Get
            If InstanceId.SelectedIndex = -1 Then
                Return Guid.Empty
            Else
                Return New Guid(InstanceId.SelectedItem.ToString())
            End If
        End Get
    End Property
    ```

    ```csharp
    public Guid WorkflowInstanceId
    {
        get
        {
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;
        }
    }
    ```

    <span data-ttu-id="22498-243">La `InstanceId` casella combinata Visualizza un elenco di ID di istanze del flusso di lavoro permanente `WorkflowInstanceId` e la proprietà restituisce il flusso di lavoro attualmente selezionato.</span><span class="sxs-lookup"><span data-stu-id="22498-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="22498-244">Aggiungere un gestore per l'evento `Load` del form.</span><span class="sxs-lookup"><span data-stu-id="22498-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="22498-245">Per aggiungere il gestore, passare alla **visualizzazione progettazione** per il modulo, fare clic sull'icona **eventi** nella parte superiore della finestra **proprietà** , quindi fare doppio clic su **carica**.</span><span class="sxs-lookup"><span data-stu-id="22498-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="22498-246">Aggiungere il seguente codice a `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="22498-246">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    'Initialize the store and configure it so that it can be used for
    'multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    'Set default ComboBox selections.
    NumberRange.SelectedIndex = 0
    WorkflowType.SelectedIndex = 0

    ListPersistedWorkflows()
    ```

    ```csharp
    // Initialize the store and configure it so that it can be used for
    // multiple WorkflowApplication instances.
    store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    // Set default ComboBox selections.
    NumberRange.SelectedIndex = 0;
    WorkflowType.SelectedIndex = 0;

    ListPersistedWorkflows();
    ```

    <span data-ttu-id="22498-247">Durante il caricamento del form, viene configurato `SqlWorkflowInstanceStore`, le caselle combinate dell'intervallo e del tipo di flusso di lavoro vengono impostate sui valori predefiniti e le istanze del flusso di lavoro persistente vengono aggiunte alla casella combinata `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="22498-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="22498-248">Aggiungere un gestore `SelectedIndexChanged` per `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="22498-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="22498-249">Per aggiungere il gestore, passare alla **visualizzazione progettazione** per il modulo, selezionare la `InstanceId` casella combinata, fare clic sull'icona **eventi** nella parte superiore della finestra **Proprietà** , quindi fare doppio clic su **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="22498-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="22498-250">Aggiungere il seguente codice a `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="22498-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="22498-251">Ogni volta che l'utente seleziona un flusso di lavoro usando la casella combinata, tramite questo gestore viene aggiornata la finestra di stato.</span><span class="sxs-lookup"><span data-stu-id="22498-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    'Clear the status window.
    WorkflowStatus.Clear()

    'Get the workflow version and display it.
    'If the workflow is just starting then this info will not
    'be available in the persistence store so do not try and retrieve it.
    If Not WorkflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        'Unload the instance.
        instance.Abandon()
    End If
    ```

    ```csharp
    if (InstanceId.SelectedIndex == -1)
    {
        return;
    }

    // Clear the status window.
    WorkflowStatus.Clear();

    // Get the workflow version and display it.
    // If the workflow is just starting then this info will not
    // be available in the persistence store so do not try and retrieve it.
    if (!WorkflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="22498-252">Aggiungere il seguente metodo `ListPersistedWorkflows` alla classe del form.</span><span class="sxs-lookup"><span data-stu-id="22498-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    'Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (SqlConnection localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="22498-253">Tramite `ListPersistedWorkflows` viene eseguita una query sull'archivio di istanze per le istanze del flusso di lavoro persistente, quindi vengono aggiunti gli ID istanza alla casella combinata `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="22498-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="22498-254">Aggiungere il seguente metodo `UpdateStatus` e il delegato corrispondente alla classe del form.</span><span class="sxs-lookup"><span data-stu-id="22498-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="22498-255">Tramite questo metodo viene aggiornata la finestra di stato nel form con lo stato del flusso di lavoro attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="22498-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        'We may be on a different thread so we need to
        'make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            'Ensure that the newly added status is visible.
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length
            WorkflowStatus.ScrollToCaret()
        End If
    End Sub
    ```

    ```csharp
    private delegate void UpdateStatusDelegate(string msg);
    public void UpdateStatus(string msg)
    {
        // We may be on a different thread so we need to
        // make this call using BeginInvoke.
        if (InvokeRequired)
        {
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);
        }
        else
        {
            if (!msg.EndsWith("\r\n"))
            {
                msg += "\r\n";
            }
            WorkflowStatus.AppendText(msg);

            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;
            WorkflowStatus.ScrollToCaret();
        }
    }
    ```

11. <span data-ttu-id="22498-256">Aggiungere il seguente metodo `GameOver` e il delegato corrispondente alla classe del form.</span><span class="sxs-lookup"><span data-stu-id="22498-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="22498-257">Quando un flusso di lavoro viene completato, questo metodo aggiorna l'interfaccia utente del form rimuovendo l'ID istanza del flusso di lavoro completato dalla casella combinata **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="22498-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            'Remove this instance from the InstanceId combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem)
            InstanceId.SelectedIndex = -1
        End If
    End Sub
    ```

    ```csharp
    private delegate void GameOverDelegate();
    private void GameOver()
    {
        if (InvokeRequired)
        {
            BeginInvoke(new GameOverDelegate(GameOver));
        }
        else
        {
            // Remove this instance from the combo box
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

### <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="22498-258">Per configurare l'archivio di istanze, i gestori del ciclo di vita del flusso di lavoro e le estensioni</span><span class="sxs-lookup"><span data-stu-id="22498-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="22498-259">Aggiungere un metodo `ConfigureWorkflowApplication` alla classe del form.</span><span class="sxs-lookup"><span data-stu-id="22498-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="22498-260">Tramite questo metodo viene configurata l'istanza `WorkflowApplication` e vengono aggiunti le estensioni desiderate e i gestori per gli eventi del ciclo di vita del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="22498-261">In `ConfigureWorkflowApplication` specificare `SqlWorkflowInstanceStore` per l'istanza `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="22498-262">Successivamente, creare un'istanza `StringWriter` e aggiungerla alla raccolta `Extensions` dell'istanza `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="22498-263">Quando un `StringWriter` oggetto viene aggiunto alle estensioni, acquisisce tutto `WriteLine` l'output dell'attività.</span><span class="sxs-lookup"><span data-stu-id="22498-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="22498-264">Quando il flusso di lavoro diventa inattivo, l'output `WriteLine` può essere estratto da `StringWriter` e visualizzato nel form.</span><span class="sxs-lookup"><span data-stu-id="22498-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    'Add a StringWriter to the extensions. This captures the output
    'from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    StringWriter sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="22498-265">Aggiungere il gestore seguente per l'evento `Completed`.</span><span class="sxs-lookup"><span data-stu-id="22498-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="22498-266">Quando un flusso di lavoro è stato completato, il numero di tentativi effettuati per determinare il numero viene visualizzato nella finestra di stato.</span><span class="sxs-lookup"><span data-stu-id="22498-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="22498-267">Se il flusso di lavoro viene terminato, vengono visualizzate le informazioni sull'eccezione che ha provocato l'interruzione.</span><span class="sxs-lookup"><span data-stu-id="22498-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="22498-268">Alla fine del gestore viene chiamato il metodo `GameOver` tramite cui il flusso di lavoro completato viene rimosso dall'elenco di flussi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _
                    e.TerminationException.GetType().FullName, _
                    e.TerminationException.Message))
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",
                e.TerminationException.GetType().FullName,
                e.TerminationException.Message));
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="22498-269">Aggiungere i seguenti gestori `Aborted` e `OnUnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="22498-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="22498-270">Il metodo `GameOver` non viene chiamato dal gestore `Aborted` perché quando un'istanza del flusso di lavoro viene interrotta, non viene terminata ed è possibile riprenderla in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="22498-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _
                e.Reason.GetType().FullName, _
                e.Reason.Message))
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _
                e.UnhandledException.GetType().FullName, _
                e.UnhandledException.Message))
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",
                e.Reason.GetType().FullName,
                e.Reason.Message));
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",
                e.UnhandledException.GetType().FullName,
                e.UnhandledException.Message));
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="22498-271">Aggiungere il seguente gestore `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="22498-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="22498-272">Tramite questo gestore viene recuperata l'estensione `StringWriter` che era stata aggiunta, viene estratto l'output dalle attività `WriteLine` che, successivamente, viene visualizzato nella finestra di stato.</span><span class="sxs-lookup"><span data-stu-id="22498-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            'Send the current WriteLine outputs to the status window.
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()
            For Each writer In writers
                UpdateStatus(writer.ToString())
            Next
            Return PersistableIdleAction.Unload
        End Function
    ```

    ```csharp
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
    {
        // Send the current WriteLine outputs to the status window.
        var writers = e.GetInstanceExtensions<StringWriter>();
        foreach (var writer in writers)
        {
            UpdateStatus(writer.ToString());
        }
        return PersistableIdleAction.Unload;
    };
    ```

    <span data-ttu-id="22498-273">L'enumerazione <xref:System.Activities.PersistableIdleAction> ha tre valori:<xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist> e <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="22498-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="22498-274">Tramite il campo <xref:System.Activities.PersistableIdleAction.Persist> il flusso di lavoro viene reso persistente, ma non scaricato.</span><span class="sxs-lookup"><span data-stu-id="22498-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="22498-275"><xref:System.Activities.PersistableIdleAction.Unload> rende il flusso di lavoro persistente e lo scarica.</span><span class="sxs-lookup"><span data-stu-id="22498-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="22498-276">Nell'esempio seguente viene mostrato il metodo `ConfigureWorkflowApplication` completato.</span><span class="sxs-lookup"><span data-stu-id="22498-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        'Configure the persistence store.
        wfApp.InstanceStore = store

        'Add a StringWriter to the extensions. This captures the output
        'from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _
                        e.TerminationException.GetType().FullName, _
                        e.TerminationException.Message))
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _
                    e.Reason.GetType().FullName, _
                    e.Reason.Message))
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _
                    e.UnhandledException.GetType().FullName, _
                    e.UnhandledException.Message))
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                'Send the current WriteLine outputs to the status window.
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()
                For Each writer In writers
                    UpdateStatus(writer.ToString())
                Next
                Return PersistableIdleAction.Unload
            End Function
    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
        // Configure the persistence store.
        wfApp.InstanceStore = store;

        // Add a StringWriter to the extensions. This captures the output
        // from the WriteLine activities so we can display it in the form.
        StringWriter sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",
                    e.TerminationException.GetType().FullName,
                    e.TerminationException.Message));
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",
                    e.Reason.GetType().FullName,
                    e.Reason.Message));
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",
                    e.UnhandledException.GetType().FullName,
                    e.UnhandledException.Message));
            GameOver();
            return UnhandledExceptionAction.Terminate;
        };

        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
        {
            // Send the current WriteLine outputs to the status window.
            var writers = e.GetInstanceExtensions<StringWriter>();
            foreach (var writer in writers)
            {
                UpdateStatus(writer.ToString());
            }
            return PersistableIdleAction.Unload;
        };
    }
    ```

### <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="22498-277">Per abilitare l'avvio e la ripresa di più tipi di flussi di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-277">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="22498-278">Per riprendere un'istanza del flusso di lavoro, tramite l'host deve essere fornita la definizione del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="22498-279">In questa esercitazione sono disponibili tre tipi di flussi di lavoro e nei passaggi successivi dell'esercitazione vengono introdotte più versioni di questi tipi.</span><span class="sxs-lookup"><span data-stu-id="22498-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="22498-280">Tramite `WorkflowIdentity` viene fornito un modo per un'applicazione host per associare le informazioni di identificazione con un'istanza del flusso di lavoro persistente.</span><span class="sxs-lookup"><span data-stu-id="22498-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="22498-281">Nei passaggi di questa sezione viene illustrato come creare una classe di utilità per consentire il mapping dell'identità del flusso di lavoro da un'istanza del flusso di lavoro persistente alla definizione del flusso di lavoro corrispondente.</span><span class="sxs-lookup"><span data-stu-id="22498-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="22498-282">Per altre informazioni su `WorkflowIdentity` e sul controllo delle versioni, vedere [uso di WorkflowIdentity e controllo delle versioni](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="22498-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="22498-283">Fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** in **Esplora soluzioni** e scegliere **Aggiungi**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="22498-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="22498-284">Digitare `WorkflowVersionMap` nella casella **nome** e fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="22498-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="22498-285">Aggiungere le seguenti istruzioni `using` o `Imports` nella parte superiore del file con le altre istruzioni `using` o `Imports`.</span><span class="sxs-lookup"><span data-stu-id="22498-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. <span data-ttu-id="22498-286">Sostituire la dichiarazione di classe `WorkflowVersionMap` con la dichiarazione seguente.</span><span class="sxs-lookup"><span data-stu-id="22498-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
       }
    }
    ```

    <span data-ttu-id="22498-287">In `WorkflowVersionMap` sono contenute tre identità del flusso di lavoro tramite cui viene eseguito il mapping alle tre definizioni del flusso di lavoro di questa esercitazione e viene usato nelle sezioni seguenti quando i flussi di lavoro vengono avviati e ripresi.</span><span class="sxs-lookup"><span data-stu-id="22498-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

### <a name="BKMK_StartWorkflow"></a><span data-ttu-id="22498-288">Per avviare un nuovo flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-288">To start a new workflow</span></span>

1. <span data-ttu-id="22498-289">Aggiungere un gestore `Click` per `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="22498-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="22498-290">Per aggiungere il gestore, passare alla **visualizzazione progettazione** per il form e fare doppio clic su `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="22498-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="22498-291">Viene aggiunto un gestore `NewGame_Click` e si passa alla visualizzazione codice per il form.</span><span class="sxs-lookup"><span data-stu-id="22498-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="22498-292">Ogni volta che l'utente fa clic sul pulsante, viene avviato un nuovo flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-292">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="22498-293">Aggiungere il codice seguente al gestore di eventi Click.</span><span class="sxs-lookup"><span data-stu-id="22498-293">Add the following code to the click handler.</span></span> <span data-ttu-id="22498-294">Tramite questo codice viene creato un dizionario di argomenti di input per il flusso di lavoro, con chiave basata sul nome dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="22498-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="22498-295">Nel dizionario è contenuta una voce in cui è incluso l'intervallo del numero generato casualmente, recuperato dalla casella combinata dell'intervallo.</span><span class="sxs-lookup"><span data-stu-id="22498-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="22498-296">Successivamente, aggiungere il codice seguente tramite cui viene avviato il flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="22498-297">`WorkflowIdentity` e la definizione del flusso di lavoro corrispondente al tipo di flusso di lavoro selezionato vengono recuperati usando la classe di supporto `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="22498-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="22498-298">Successivamente, viene creata una nuova istanza `WorkflowApplication` usando la definizione del flusso di lavoro, `WorkflowIdentity` e il dizionario degli argomenti di input.</span><span class="sxs-lookup"><span data-stu-id="22498-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

    ```vb
    Dim identity As WorkflowIdentity = Nothing
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
    End Select

    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

    Dim wfApp = New WorkflowApplication(wf, inputs, identity)
    ```

    ```csharp
    WorkflowIdentity identity = null;
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;
    };

    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);
    ```

4. <span data-ttu-id="22498-299">Successivamente, aggiungere il codice seguente tramite cui viene aggiunto il flusso di lavoro al relativo elenco e vengono visualizzate le informazioni sulla versione del flusso di lavoro nel form.</span><span class="sxs-lookup"><span data-stu-id="22498-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    'Add the workflow to the list and display the version information.
    WorkflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    WorkflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    WorkflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    WorkflowStarting = false;
    ```

5. <span data-ttu-id="22498-300">Chiamare `ConfigureWorkflowApplication` per configurare l'archivio di istanze, le estensioni e i gestori del ciclo di vita del flusso di lavoro per questa istanza `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    'Configure the instance store, extensions, and
    'workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="22498-301">Infine, viene chiamato `Run`.</span><span class="sxs-lookup"><span data-stu-id="22498-301">Finally, call `Run`.</span></span>

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="22498-302">Nell'esempio seguente viene mostrato il gestore `NewGame_Click` completato.</span><span class="sxs-lookup"><span data-stu-id="22498-302">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        'Start a new workflow.
        Dim inputs As New Dictionary(Of String, Object)()
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))

        Dim identity As WorkflowIdentity = Nothing
        Select Case WorkflowType.SelectedItem.ToString()
            Case "SequentialNumberGuessWorkflow"
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity

            Case "StateMachineNumberGuessWorkflow"
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

            Case "FlowchartNumberGuessWorkflow"
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
        End Select

        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

        Dim wfApp = New WorkflowApplication(wf, inputs, identity)

        'Add the workflow to the list and display the version information.
        WorkflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        WorkflowStarting = False

        'Configure the instance store, extensions, and
        'workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        'Start the workflow.
        wfApp.Run()
    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {
        var inputs = new Dictionary<string, object>();
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));

        WorkflowIdentity identity = null;
        switch (WorkflowType.SelectedItem.ToString())
        {
            case "SequentialNumberGuessWorkflow":
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
                break;

            case "StateMachineNumberGuessWorkflow":
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
                break;

            case "FlowchartNumberGuessWorkflow":
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
                break;
        };

        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        WorkflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        WorkflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

### <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="22498-303">Per riprendere un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-303">To resume a workflow</span></span>

1. <span data-ttu-id="22498-304">Aggiungere un gestore `Click` per `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="22498-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="22498-305">Per aggiungere il gestore, passare alla **visualizzazione progettazione** per il form e fare doppio clic su `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="22498-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="22498-306">Ogni volta che l'utente fa clic sul pulsante, viene ripreso un flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-306">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="22498-307">Aggiungere il codice seguente per assicurarsi che un flusso di lavoro venga selezionato nell'elenco di flussi di lavoro e che il tentativo dell'utente sia valido.</span><span class="sxs-lookup"><span data-stu-id="22498-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim userGuess As Integer
    If Not Int32.TryParse(Guess.Text, userGuess) Then
        MessageBox.Show("Please enter an integer.")
        Guess.SelectAll()
        Guess.Focus()
        Return
    End If
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    int guess;
    if (!Int32.TryParse(Guess.Text, out guess))
    {
        MessageBox.Show("Please enter an integer.");
        Guess.SelectAll();
        Guess.Focus();
        return;
    }
    ```

3. <span data-ttu-id="22498-308">Successivamente, recuperare l'istanza `WorkflowApplicationInstance` dell'istanza del flusso di lavoro persistente.</span><span class="sxs-lookup"><span data-stu-id="22498-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="22498-309">Un'istanza `WorkflowApplicationInstance` rappresenta un'istanza del flusso di lavoro persistente che non è ancora stata associata a una definizione del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="22498-310">In `DefinitionIdentity` dell'istanza `WorkflowApplicationInstance` è contenuto `WorkflowIdentity` dell'istanza del flusso di lavoro persistente.</span><span class="sxs-lookup"><span data-stu-id="22498-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="22498-311">In questa esercitazione la classe di utilità `WorkflowVersionMap` viene usata per eseguire il mapping di `WorkflowIdentity` alla definizione del flusso di lavoro corretta.</span><span class="sxs-lookup"><span data-stu-id="22498-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="22498-312">Una volta recuperata la definizione del flusso di lavoro, viene creata un'istanza `WorkflowApplication` usando la definizione del flusso di lavoro corretta.</span><span class="sxs-lookup"><span data-stu-id="22498-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    'Use the persisted WorkflowIdentity to retrieve the correct workflow
    'definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    'Associate the WorkflowApplication with the correct definition
    Dim wfApp As WorkflowApplication = _
        New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    WorkflowApplication wfApp =
        new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="22498-313">Una volta creata l'istanza `WorkflowApplication`, configurare l'archivio di istanze, i gestori del ciclo di vita del flusso di lavoro e le estensioni chiamando `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="22498-314">Questi passaggi devono essere effettuati ogni volta che viene creata una nuova istanza `WorkflowApplication` e prima che l'istanza del flusso di lavoro venga caricata nell'istanza `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="22498-315">Una volta caricato il flusso di lavoro, viene ripreso con il tentativo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="22498-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    'Configure the extensions and lifecycle handlers.
    'Do this before the instance is loaded. Once the instance is
    'loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    'Load the workflow.
    wfApp.Load(instance)

    'Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", userGuess)
    ```

    ```csharp
    // Configure the extensions and lifecycle handlers.
    // Do this before the instance is loaded. Once the instance is
    // loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", guess);
    ```

5. <span data-ttu-id="22498-316">Infine, deselezionare la casella di testo del tentativo e preparare il form per accettare un altro tentativo.</span><span class="sxs-lookup"><span data-stu-id="22498-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    'Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="22498-317">Nell'esempio seguente viene mostrato il gestore `EnterGuess_Click` completato.</span><span class="sxs-lookup"><span data-stu-id="22498-317">The following example is the completed `EnterGuess_Click` handler.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click
        If WorkflowInstanceId = Guid.Empty Then
            MessageBox.Show("Please select a workflow.")
            Return
        End If

        Dim userGuess As Integer
        If Not Int32.TryParse(Guess.Text, userGuess) Then
            MessageBox.Show("Please enter an integer.")
            Guess.SelectAll()
            Guess.Focus()
            Return
        End If

        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        'Use the persisted WorkflowIdentity to retrieve the correct workflow
        'definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        'Associate the WorkflowApplication with the correct definition
        Dim wfApp As WorkflowApplication = _
            New WorkflowApplication(wf, instance.DefinitionIdentity)

        'Configure the extensions and lifecycle handlers.
        'Do this before the instance is loaded. Once the instance is
        'loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        'Load the workflow.
        wfApp.Load(instance)

        'Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        'Clear the Guess textbox.
        Guess.Clear()
        Guess.Focus()
    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {
        if (WorkflowInstanceId == Guid.Empty)
        {
            MessageBox.Show("Please select a workflow.");
            return;
        }

        int guess;
        if (!Int32.TryParse(Guess.Text, out guess))
        {
            MessageBox.Show("Please enter an integer.");
            Guess.SelectAll();
            Guess.Focus();
            return;
        }

        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);

        // Use the persisted WorkflowIdentity to retrieve the correct workflow
        // definition from the dictionary.
        Activity wf =
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

        // Associate the WorkflowApplication with the correct definition
        WorkflowApplication wfApp =
            new WorkflowApplication(wf, instance.DefinitionIdentity);

        // Configure the extensions and lifecycle handlers.
        // Do this before the instance is loaded. Once the instance is
        // loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp);

        // Load the workflow.
        wfApp.Load(instance);

        // Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", guess);

        // Clear the Guess textbox.
        Guess.Clear();
        Guess.Focus();
    }
    ```

### <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="22498-318">Per terminare un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="22498-318">To terminate a workflow</span></span>

1. <span data-ttu-id="22498-319">Aggiungere un gestore `Click` per `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="22498-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="22498-320">Per aggiungere il gestore, passare alla **visualizzazione progettazione** per il form e fare doppio clic su `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="22498-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="22498-321">Ogni volta che l'utente fa clic sul pulsante, il flusso di lavoro selezionato viene interrotto.</span><span class="sxs-lookup"><span data-stu-id="22498-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="22498-322">Aggiungere al gestore `QuitGame_Click` il codice riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="22498-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="22498-323">Tramite il codice viene innanzitutto verificato che un flusso di lavoro venga selezionato nell'elenco di flussi di controllo.</span><span class="sxs-lookup"><span data-stu-id="22498-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="22498-324">Successivamente viene caricata l'istanza persistente in un'istanza `WorkflowApplicationInstance`, viene usato `DefinitionIdentity` per determinare la definizione del flusso di lavoro corretta e, infine, viene inizializzata l'istanza `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="22498-325">In seguito, le estensioni e i gestori del ciclo di vita del flusso di lavoro vengono configurati con una chiamata al metodo `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="22498-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="22498-326">Una volta configurata, l'istanza `WorkflowApplication` viene caricata e viene chiamato `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="22498-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    'Use the persisted WorkflowIdentity to retrieve the correct workflow
    'definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    'Associate the WorkflowApplication with the correct definition.
    Dim wfApp As WorkflowApplication = _
        New WorkflowApplication(wf, instance.DefinitionIdentity)

    'Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    'Load the workflow.
    wfApp.Load(instance)

    'Terminate the workflow.
    wfApp.Terminate("User resigns.")
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    WorkflowApplication wfApp =
        new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="22498-327">Per compilare ed eseguire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="22498-327">To build and run the application</span></span>

1. <span data-ttu-id="22498-328">Fare doppio clic su **Program.cs** (o **Module1. vb**) in **Esplora soluzioni** per visualizzare il codice.</span><span class="sxs-lookup"><span data-stu-id="22498-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="22498-329">Aggiungere la seguente istruzione `using` (o `Imports`) nella parte superiore del file con le altre istruzioni `using` (o `Imports`).</span><span class="sxs-lookup"><span data-stu-id="22498-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="22498-330">Rimuovere o impostare come commento il codice di hosting del [flusso di lavoro esistente da procedura: Eseguire un flusso](how-to-run-a-workflow.md)di lavoro e sostituirlo con il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="22498-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

    ```vb
    Sub Main()
        Application.EnableVisualStyles()
        Application.Run(New WorkflowHostForm())
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        Application.EnableVisualStyles();
        Application.Run(new WorkflowHostForm());
    }
    ```

4. <span data-ttu-id="22498-331">Fare clic con il pulsante destro del mouse su **NumberGuessWorkflowHost** in **Esplora soluzioni** e scegliere **proprietà**.</span><span class="sxs-lookup"><span data-stu-id="22498-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="22498-332">Nella scheda **applicazione** specificare **applicazione Windows** per il tipo di **output**.</span><span class="sxs-lookup"><span data-stu-id="22498-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="22498-333">Questo passaggio è facoltativo, ma se non viene effettuato, oltre al form viene visualizzata anche la finestra della console.</span><span class="sxs-lookup"><span data-stu-id="22498-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="22498-334">Premere CTRL+MAIUSC+B per compilare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="22498-334">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="22498-335">Verificare che **NumberGuessWorkflowHost** sia impostato come applicazione di avvio e premere CTRL + F5 per avviare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="22498-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="22498-336">Selezionare un intervallo per il gioco Guess e il tipo di flusso di lavoro da avviare, quindi fare clic su **nuovo gioco**.</span><span class="sxs-lookup"><span data-stu-id="22498-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="22498-337">Immettere una supposizione nella casella **Guess** e fare clic su **go** per inviare l'ipotesi.</span><span class="sxs-lookup"><span data-stu-id="22498-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="22498-338">Si noti che l'output dalle attività `WriteLine` viene visualizzato nel form.</span><span class="sxs-lookup"><span data-stu-id="22498-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="22498-339">Avviare diversi flussi di lavoro usando diversi tipi di flussi di lavoro e intervalli di numeri, immettere alcune ipotesi e passare tra i flussi di lavoro selezionando dall'elenco **ID istanza del flusso** di lavoro.</span><span class="sxs-lookup"><span data-stu-id="22498-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="22498-340">Si noti che quando si passa a un nuovo flusso di lavoro, i tentativi precedenti e lo stato di avanzamento del flusso di lavoro non vengono visualizzati nella finestra di stato.</span><span class="sxs-lookup"><span data-stu-id="22498-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="22498-341">Lo stato non è disponibile poiché non è stato acquisito e salvato da nessuna parte.</span><span class="sxs-lookup"><span data-stu-id="22498-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="22498-342">Nel passaggio successivo dell'esercitazione, [procedura: Creare un partecipante](how-to-create-a-custom-tracking-participant.md)del rilevamento personalizzato. viene creato un partecipante del rilevamento personalizzato che salva queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="22498-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
