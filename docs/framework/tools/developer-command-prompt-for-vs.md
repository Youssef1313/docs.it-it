---
title: Prompt dei comandi per gli sviluppatori per Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044733"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="1b940-102">Prompt dei comandi per gli sviluppatori per Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b940-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="1b940-103">Il Prompt dei comandi per gli sviluppatori per Visual Studio consente di usare più facilmente gli strumenti di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b940-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="1b940-104">Questo prompt dei comandi imposta automaticamente variabili di ambiente specifiche.</span><span class="sxs-lookup"><span data-stu-id="1b940-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="1b940-105">Download di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b940-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="1b940-106">Cercare il prompt dei comandi nel computer</span><span class="sxs-lookup"><span data-stu-id="1b940-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="1b940-107">Si potrebbero avere più prompt dei comandi, in base alla versione di Visual Studio e agli SDK aggiuntivi installati.</span><span class="sxs-lookup"><span data-stu-id="1b940-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="1b940-108">Ad esempio, le versioni a 64 bit di Visual Studio forniscono prompt dei comandi sia a 32 bit che a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="1b940-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="1b940-109">Le versioni a 32 bit e a 64 bit della maggior parte degli strumenti sono uguali; tuttavia, alcuni strumenti apportano modifiche specifiche per gli ambienti a 32 bit e a 64 bit. Se i passaggi seguenti non funzionano, è possibile provare [Trovare manualmente i file nel computer](#manually-locate-the-files-on-your-machine) o [Eseguire il prompt dei comandi dall'interno di Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1b940-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="1b940-110">In Windows 10</span><span class="sxs-lookup"><span data-stu-id="1b940-110">In Windows 10</span></span>

1. <span data-ttu-id="1b940-111">Nella casella di ricerca della barra delle applicazioni iniziare a digitare il nome dello strumento, ad esempio `dev` o `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="1b940-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="1b940-112">Verrà visualizzato un elenco di app installate che corrispondono ai criteri di ricerca.</span><span class="sxs-lookup"><span data-stu-id="1b940-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="1b940-113">Se si sta cercando un prompt dei comandi diverso, provare a immettere un termine di ricerca diverso, ad esempio `prompt`.</span><span class="sxs-lookup"><span data-stu-id="1b940-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="1b940-114">Scegliere **Prompt dei comandi per gli sviluppatori per Visual Studio** (o il prompt dei comandi che si vuole usare).</span><span class="sxs-lookup"><span data-stu-id="1b940-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="1b940-115">In Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1b940-115">In Windows 8.1</span></span>

1. <span data-ttu-id="1b940-116">Andare alla schermata **Start** ad esempio premendo il tasto WINDOWS![tasto WINDOWS sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="1b940-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="1b940-117">sulla tastiera.</span><span class="sxs-lookup"><span data-stu-id="1b940-117">on your keyboard for example.</span></span>

2. <span data-ttu-id="1b940-118">Nella schermata **Start** premere **CTRL**+**TAB** per aprire l'elenco **App** e quindi immettere `V`.</span><span class="sxs-lookup"><span data-stu-id="1b940-118">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="1b940-119">Verrà visualizzato un elenco che include tutti i prompt dei comandi di Visual Studio installati.</span><span class="sxs-lookup"><span data-stu-id="1b940-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="1b940-120">Scegliere **Prompt dei comandi per gli sviluppatori** (o il prompt dei comandi che si vuole usare).</span><span class="sxs-lookup"><span data-stu-id="1b940-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="1b940-121">In Windows 8</span><span class="sxs-lookup"><span data-stu-id="1b940-121">In Windows 8</span></span>

1. <span data-ttu-id="1b940-122">Andare alla schermata **Start** ad esempio premendo il tasto WINDOWS![tasto WINDOWS sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="1b940-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="1b940-123">sulla tastiera.</span><span class="sxs-lookup"><span data-stu-id="1b940-123">on your keyboard for example.</span></span>

2. <span data-ttu-id="1b940-124">Nella schermata **Start** premere il tasto WINDOWS![tasto WINDOWS sulla tastiera.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="1b940-124">On the **Start** screen, press the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="1b940-125">[https://login.microsoftonline.com/consumers/](`+ Z`).</span><span class="sxs-lookup"><span data-stu-id="1b940-125">`+ Z`.</span></span>

3. <span data-ttu-id="1b940-126">Scegliere l'icona **Visualizzazione App** nella parte inferiore della schermata e quindi immettere `V`.</span><span class="sxs-lookup"><span data-stu-id="1b940-126">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="1b940-127">Verrà visualizzato un elenco che include tutti i prompt dei comandi di Visual Studio installati.</span><span class="sxs-lookup"><span data-stu-id="1b940-127">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="1b940-128">Scegliere **Prompt dei comandi per gli sviluppatori** (o il prompt dei comandi che si vuole usare).</span><span class="sxs-lookup"><span data-stu-id="1b940-128">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="1b940-129">In Windows 7</span><span class="sxs-lookup"><span data-stu-id="1b940-129">In Windows 7</span></span>

1. <span data-ttu-id="1b940-130">Scegliere **Start**, espandere **Tutti i programmi** e quindi espandere **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1b940-130">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="1b940-131">A seconda della versione di Visual Studio installata, scegliere **Strumenti di Visual Studio**, **Prompt dei comandi di Visual Studio** o il prompt dei comandi che si vuole usare.</span><span class="sxs-lookup"><span data-stu-id="1b940-131">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="1b940-132">Se ci sono altri SDK installati, ad esempio [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) o [versioni precedenti](https://developer.microsoft.com/windows/downloads/sdk-archive), si potranno notare prompt dei comandi aggiuntivi per le architetture ARM, x86 o x64.</span><span class="sxs-lookup"><span data-stu-id="1b940-132">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="1b940-133">Consultare la documentazione dei diversi strumenti per determinare quale versione del prompt dei comandi usare.</span><span class="sxs-lookup"><span data-stu-id="1b940-133">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="1b940-134">Trovare manualmente i file nel computer</span><span class="sxs-lookup"><span data-stu-id="1b940-134">Manually locate the files on your machine</span></span>

<span data-ttu-id="1b940-135">In genere, i collegamenti per i prompt dei comandi installati verranno posizionati nella cartella **Menu Start** per Visual Studio, ad esempio in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="1b940-135">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="1b940-136">Tuttavia, se per qualche motivo la ricerca del prompt dei comandi non produce i risultati previsti, è possibile provare a trovare manualmente il collegamento nel computer.</span><span class="sxs-lookup"><span data-stu-id="1b940-136">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="1b940-137">Provare a cercare il nome del file del prompt dei comandi, ad esempio *VsDevCmd.bat* o passare alla cartella Tools, ad esempio C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (il percorso cambierà a seconda del percorso di installazione, della versione e dell'edizione di Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="1b940-137">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="1b940-138">Eseguire il prompt dei comandi dall'interno di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b940-138">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="1b940-139">Per semplificare l'accesso, è possibile aggiungere il prompt dei comandi per gli sviluppatori Visual Studio o qualsiasi altro prompt dei comandi al menu **Strumenti** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b940-139">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="1b940-140">Per rendere lo strumento disponibile, aggiungerlo all'elenco degli strumenti esterni.</span><span class="sxs-lookup"><span data-stu-id="1b940-140">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="1b940-141">Di seguito la procedura:</span><span class="sxs-lookup"><span data-stu-id="1b940-141">Here are the steps:</span></span>

1. <span data-ttu-id="1b940-142">Aprire Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b940-142">Open Visual Studio.</span></span>

2. <span data-ttu-id="1b940-143">Selezionare il menu **Strumenti** e quindi scegliere **Strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="1b940-143">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="1b940-144">Nella finestra di dialogo **Strumenti esterni** scegliere il pulsante **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="1b940-144">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="1b940-145">Verrà visualizzata una nuova voce.</span><span class="sxs-lookup"><span data-stu-id="1b940-145">A new entry appears.</span></span>

4. <span data-ttu-id="1b940-146">Immettere un **titolo** per la nuova voce di menu, ad esempio `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="1b940-146">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="1b940-147">Nel campo **Comando** specificare il file che si vuole avviare, ad esempio `%comspec%` o `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="1b940-147">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="1b940-148">Nel campo **Argomenti** specificare dove trovare il prompt dei comandi specifico da usare, ad esempio `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (verrà avviato il Prompt dei comandi per gli sviluppatori installato con Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="1b940-148">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="1b940-149">Modificare questo valore in base al percorso di installazione, alla versione e all'edizione di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b940-149">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="1b940-150">Scegliere un valore per il campo **Directory iniziale**, ad esempio **Directory di progetto**.</span><span class="sxs-lookup"><span data-stu-id="1b940-150">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="1b940-151">Fare clic sul pulsante **OK** .</span><span class="sxs-lookup"><span data-stu-id="1b940-151">Choose the **OK** button.</span></span>

   <span data-ttu-id="1b940-152">Verrà aggiunta la nuova voce di menu e sarà possibile accedere al prompt dei comandi dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="1b940-152">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Voce di menu del prompt dei comandi in Visual Studio](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="1b940-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1b940-154">See also</span></span>

- [<span data-ttu-id="1b940-155">Strumenti</span><span class="sxs-lookup"><span data-stu-id="1b940-155">Tools</span></span>](index.md)
- [<span data-ttu-id="1b940-156">Gestione di strumenti esterni</span><span class="sxs-lookup"><span data-stu-id="1b940-156">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
