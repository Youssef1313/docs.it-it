---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351714"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="e49e9-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e49e9-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="e49e9-103">Indica al compilatore di considerare la prima occorrenza di un avviso come errore.</span><span class="sxs-lookup"><span data-stu-id="e49e9-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49e9-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e49e9-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e49e9-105">argomenti</span><span class="sxs-lookup"><span data-stu-id="e49e9-105">Arguments</span></span>  
  
|<span data-ttu-id="e49e9-106">Termine</span><span class="sxs-lookup"><span data-stu-id="e49e9-106">Term</span></span>|<span data-ttu-id="e49e9-107">Definizione</span><span class="sxs-lookup"><span data-stu-id="e49e9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e49e9-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="e49e9-108">+ &#124; -</span></span>|<span data-ttu-id="e49e9-109">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e49e9-109">Optional.</span></span> <span data-ttu-id="e49e9-110">Per impostazione predefinita, l'opzione `-warnaserror-` è attiva. Gli avvisi non impediscono al compilatore di produrre un file di output.</span><span class="sxs-lookup"><span data-stu-id="e49e9-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="e49e9-111">Con l'opzione `-warnaserror`, equivalente a `-warnaserror+`, gli avvisi vengono considerati errori.</span><span class="sxs-lookup"><span data-stu-id="e49e9-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="e49e9-112">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e49e9-112">Optional.</span></span> <span data-ttu-id="e49e9-113">Elenco delimitato da virgole di numeri di ID di avviso a cui si applica l'opzione `-warnaserror`.</span><span class="sxs-lookup"><span data-stu-id="e49e9-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="e49e9-114">Se non viene specificato alcun ID di avviso, l'opzione `-warnaserror` si applica a tutti gli avvisi.</span><span class="sxs-lookup"><span data-stu-id="e49e9-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e49e9-115">Note</span><span class="sxs-lookup"><span data-stu-id="e49e9-115">Remarks</span></span>  
 <span data-ttu-id="e49e9-116">L'opzione `-warnaserror` considera tutti gli avvisi come errori.</span><span class="sxs-lookup"><span data-stu-id="e49e9-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="e49e9-117">Qualsiasi messaggio segnalato di norma come avviso viene invece segnalato come errore.</span><span class="sxs-lookup"><span data-stu-id="e49e9-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="e49e9-118">Il compilatore segnala le occorrenze successive dello stesso avviso come avvisi.</span><span class="sxs-lookup"><span data-stu-id="e49e9-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="e49e9-119">Per impostazione predefinita, l'opzione `-warnaserror-` è attiva, pertanto gli avvisi sono solo informativi.</span><span class="sxs-lookup"><span data-stu-id="e49e9-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="e49e9-120">Con l'opzione `-warnaserror`, equivalente a `-warnaserror+`, gli avvisi vengono considerati errori.</span><span class="sxs-lookup"><span data-stu-id="e49e9-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="e49e9-121">Se si vuole che solo determinati avvisi vengano considerati errori, è possibile specificare un elenco delimitato da virgole di numeri di avvisi da considerare errori.</span><span class="sxs-lookup"><span data-stu-id="e49e9-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e49e9-122">L'opzione `-warnaserror` non controlla la modalità di visualizzazione degli avvisi.</span><span class="sxs-lookup"><span data-stu-id="e49e9-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="e49e9-123">Usare l'opzione [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) per disabilitare gli avvisi.</span><span class="sxs-lookup"><span data-stu-id="e49e9-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="e49e9-124">Per impostare -warnaserror in modo da considerare tutti gli avvisi come errori nell'IDE di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e49e9-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="e49e9-125">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="e49e9-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e49e9-126">Scegliere **Proprietà** dal menu **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="e49e9-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e49e9-127">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="e49e9-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e49e9-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="e49e9-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="e49e9-129">4.  Check the **Treat all warnings as errors** check box.</span><span class="sxs-lookup"><span data-stu-id="e49e9-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="e49e9-130">Per impostare -warnaserror in modo da considerare avvisi specifici come errori nell'IDE di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e49e9-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="e49e9-131">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="e49e9-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e49e9-132">Scegliere **Proprietà** dal menu **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="e49e9-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="e49e9-133">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="e49e9-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e49e9-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="e49e9-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="e49e9-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="e49e9-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="e49e9-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span><span class="sxs-lookup"><span data-stu-id="e49e9-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e49e9-137">Esempio</span><span class="sxs-lookup"><span data-stu-id="e49e9-137">Example</span></span>  
 <span data-ttu-id="e49e9-138">Il codice seguente compila `In.vb` e indica al compilatore di visualizzare un errore per la prima occorrenza di ogni avviso rilevato.</span><span class="sxs-lookup"><span data-stu-id="e49e9-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="e49e9-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="e49e9-139">Example</span></span>  
 <span data-ttu-id="e49e9-140">Il codice seguente compila `T2.vb` e considera come errore solo l'avviso per le variabili locali inutilizzate (42024).</span><span class="sxs-lookup"><span data-stu-id="e49e9-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e49e9-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e49e9-141">See also</span></span>

- [<span data-ttu-id="e49e9-142">Compilatore della riga di comando di Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e49e9-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e49e9-143">Esempi di righe di comando di compilazione</span><span class="sxs-lookup"><span data-stu-id="e49e9-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e49e9-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e49e9-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
