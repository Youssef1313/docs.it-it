---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005345"
---
# <a name="-optionstrict"></a><span data-ttu-id="d3a92-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="d3a92-102">-optionstrict</span></span>
<span data-ttu-id="d3a92-103">Applica una semantica dei tipi rigorosa per limitare le conversioni implicite dei tipi.</span><span class="sxs-lookup"><span data-stu-id="d3a92-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a92-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d3a92-104">Syntax</span></span>  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3a92-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="d3a92-105">Arguments</span></span>  
 <span data-ttu-id="d3a92-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d3a92-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d3a92-107">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="d3a92-107">Optional.</span></span> <span data-ttu-id="d3a92-108">L'opzione `-optionstrict+` limita la conversione implicita di tipi.</span><span class="sxs-lookup"><span data-stu-id="d3a92-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="d3a92-109">Il valore predefinito per questa opzione è `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="d3a92-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="d3a92-110">L'opzione `-optionstrict+` corrisponde a `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="d3a92-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="d3a92-111">È possibile utilizzare entrambi per la semantica di tipo permissivo.</span><span class="sxs-lookup"><span data-stu-id="d3a92-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="d3a92-112">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d3a92-112">Required.</span></span> <span data-ttu-id="d3a92-113">Avvisa quando la semantica del linguaggio strict non viene rispettata.</span><span class="sxs-lookup"><span data-stu-id="d3a92-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3a92-114">Note</span><span class="sxs-lookup"><span data-stu-id="d3a92-114">Remarks</span></span>  
 <span data-ttu-id="d3a92-115">Quando `-optionstrict+` è attivo, è possibile rendere implicite solo le conversioni verso un tipo più ampio.</span><span class="sxs-lookup"><span data-stu-id="d3a92-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="d3a92-116">Le conversioni implicite di tipi più restrittivi, ad esempio l'assegnazione di un oggetto di tipo `Decimal` a un oggetto di tipo Integer, vengono segnalate come errori.</span><span class="sxs-lookup"><span data-stu-id="d3a92-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="d3a92-117">Per generare avvisi per le conversioni implicite di tipi più restrittivi, utilizzare `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="d3a92-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="d3a92-118">Utilizzare `-nowarn:numberlist` per ignorare determinati avvisi e `-warnaserror:numberlist` per considerare determinati avvisi come errori.</span><span class="sxs-lookup"><span data-stu-id="d3a92-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="d3a92-119">Per impostare-optionstrict (nell'IDE di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3a92-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="d3a92-120">Selezionare un progetto in **Esplora soluzioni**.</span><span class="sxs-lookup"><span data-stu-id="d3a92-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d3a92-121">Scegliere Proprietà dal menu **progetto** **.**</span><span class="sxs-lookup"><span data-stu-id="d3a92-121">On the **Project** menu, click **Properties.**</span></span>   
  
2. <span data-ttu-id="d3a92-122">Fare clic sulla scheda **Compila**.</span><span class="sxs-lookup"><span data-stu-id="d3a92-122">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="d3a92-123">Modificare il valore nella casella **Option Strict** .</span><span class="sxs-lookup"><span data-stu-id="d3a92-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="d3a92-124">Per impostare-optionstrict (a livello di codice</span><span class="sxs-lookup"><span data-stu-id="d3a92-124">To set -optionstrict programmatically</span></span>  
  
- <span data-ttu-id="d3a92-125">Vedere [istruzione Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3a92-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3a92-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="d3a92-126">Example</span></span>  
 <span data-ttu-id="d3a92-127">Il codice seguente compila `Test.vb` usando la semantica di tipo strict.</span><span class="sxs-lookup"><span data-stu-id="d3a92-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3a92-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3a92-128">See also</span></span>

- [<span data-ttu-id="d3a92-129">Compilatore della riga di comando di Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3a92-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d3a92-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="d3a92-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="d3a92-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="d3a92-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="d3a92-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d3a92-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="d3a92-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="d3a92-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="d3a92-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3a92-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="d3a92-135">Esempi di righe di comando di compilazione</span><span class="sxs-lookup"><span data-stu-id="d3a92-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d3a92-136">Istruzione Option Strict</span><span class="sxs-lookup"><span data-stu-id="d3a92-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d3a92-137">Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni</span><span class="sxs-lookup"><span data-stu-id="d3a92-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
