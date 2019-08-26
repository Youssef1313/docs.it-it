---
title: -errorreport (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dc876f609643b7112c0f54574bd202c7c19cb119
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924775"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="c8b96-102">-errorreport (opzioni del compilatore C#)</span><span class="sxs-lookup"><span data-stu-id="c8b96-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="c8b96-103">Questa opzione rappresenta un modo pratico per segnalare a Microsoft un errore del compilatore interno C#.</span><span class="sxs-lookup"><span data-stu-id="c8b96-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8b96-104">In Windows Vista e Windows Server 2008 le impostazioni di segnalazione errori apportate per Visual Studio non eseguono l'override delle impostazioni apportate tramite Segnalazioni errori Windows.</span><span class="sxs-lookup"><span data-stu-id="c8b96-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="c8b96-105">Le impostazioni di Segnalazione errori Windows hanno sempre la precedenza sulle impostazioni della funzione di segnalazione errori di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8b96-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b96-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c8b96-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8b96-107">Argomenti</span><span class="sxs-lookup"><span data-stu-id="c8b96-107">Arguments</span></span>  
 <span data-ttu-id="c8b96-108">**none**</span><span class="sxs-lookup"><span data-stu-id="c8b96-108">**none**</span></span>  
 <span data-ttu-id="c8b96-109">Le segnalazioni sugli errori interni del compilatore non verranno raccolte o inviate a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c8b96-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="c8b96-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="c8b96-110">**prompt**</span></span>  
 <span data-ttu-id="c8b96-111">Chiede di inviare una segnalazione quando si riceve un errore interno del compilatore.</span><span class="sxs-lookup"><span data-stu-id="c8b96-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="c8b96-112">**prompt** è l'impostazione predefinita se si compila un'applicazione all'interno dell'ambiente di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="c8b96-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="c8b96-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="c8b96-113">**queue**</span></span>  
 <span data-ttu-id="c8b96-114">Accoda la segnalazione errori.</span><span class="sxs-lookup"><span data-stu-id="c8b96-114">Queues the error report.</span></span> <span data-ttu-id="c8b96-115">Se si accede con credenziali amministrative, è possibile segnalare qualsiasi errore dall'ultima volta che è stato effettuato l'accesso.</span><span class="sxs-lookup"><span data-stu-id="c8b96-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="c8b96-116">Non verrà richiesto di inviare report di errori più di una volta ogni tre giorni.</span><span class="sxs-lookup"><span data-stu-id="c8b96-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="c8b96-117">**queue** è l'impostazione predefinita se si compila un'applicazione dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="c8b96-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="c8b96-118">**send**</span><span class="sxs-lookup"><span data-stu-id="c8b96-118">**send**</span></span>  
 <span data-ttu-id="c8b96-119">Invia automaticamente a Microsoft le segnalazioni di errori interni del compilatore.</span><span class="sxs-lookup"><span data-stu-id="c8b96-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="c8b96-120">Per abilitare questa opzione, è necessario prima di tutto accettare i Criteri per la raccolta dati Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c8b96-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="c8b96-121">La prima volta che si specifica **-errorreport:send** in un computer, viene visualizzato un messaggio del compilatore che indirizza a un sito Web contenente questi criteri.</span><span class="sxs-lookup"><span data-stu-id="c8b96-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="c8b96-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c8b96-122">Remarks</span></span>  
 <span data-ttu-id="c8b96-123">Se il compilatore non è in grado di elaborare un file del codice sorgente, viene restituito un errore interno del compilatore (ICE, Internal Compiler Error).</span><span class="sxs-lookup"><span data-stu-id="c8b96-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="c8b96-124">Quando si verifica un ICE, il compilatore non genera né un file di output né informazioni di diagnostica utili per correggere il codice.</span><span class="sxs-lookup"><span data-stu-id="c8b96-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="c8b96-125">Nelle versioni precedenti, quando si riceveva un ICE si riceveva anche l'invito a contattare il Servizio supporto tecnico Microsoft per segnalare il problema.</span><span class="sxs-lookup"><span data-stu-id="c8b96-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="c8b96-126">Con **-errorreport** è possibile offrire informazioni sugli errori interni del compilatore al team Visual C#.</span><span class="sxs-lookup"><span data-stu-id="c8b96-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="c8b96-127">Le segnalazioni degli errori consentono di migliorare le versioni future del compilatore.</span><span class="sxs-lookup"><span data-stu-id="c8b96-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="c8b96-128">La capacità di un utente di inviare report dipende dalle autorizzazioni relative ai criteri utente e computer.</span><span class="sxs-lookup"><span data-stu-id="c8b96-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="c8b96-129">Per altre informazioni sul debugger degli errori, vedere [Descrizione dello strumento Dr. Watson per Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span><span class="sxs-lookup"><span data-stu-id="c8b96-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8b96-130">Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8b96-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c8b96-131">Aprire la pagine **Proprietà** del progetto.</span><span class="sxs-lookup"><span data-stu-id="c8b96-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="c8b96-132">Per altre informazioni, vedere [Pagina Compilazione, Creazione progetti (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="c8b96-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="c8b96-133">Fare clic sulla pagina della proprietà **Compilazione**.</span><span class="sxs-lookup"><span data-stu-id="c8b96-133">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="c8b96-134">Fare clic su **Avanzate** .</span><span class="sxs-lookup"><span data-stu-id="c8b96-134">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="c8b96-135">Modificare la proprietà **Segnalazione errori interni del compilatore**.</span><span class="sxs-lookup"><span data-stu-id="c8b96-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="c8b96-136">Per informazioni su come impostare questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8b96-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b96-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c8b96-137">See also</span></span>

- [<span data-ttu-id="c8b96-138">Opzioni del compilatore C#</span><span class="sxs-lookup"><span data-stu-id="c8b96-138">C# Compiler Options</span></span>](./index.md)
