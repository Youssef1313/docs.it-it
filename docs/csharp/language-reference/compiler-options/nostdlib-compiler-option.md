---
title: -nostdlib (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602694"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="ec234-102">-nostdlib (opzioni del compilatore C#)</span><span class="sxs-lookup"><span data-stu-id="ec234-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="ec234-103">**-nostdlib** impedisce l'importazione di mscorlib.dll, che definisce l'intero spazio dei nomi di sistema.</span><span class="sxs-lookup"><span data-stu-id="ec234-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec234-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ec234-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="ec234-105">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ec234-105">Remarks</span></span>

<span data-ttu-id="ec234-106">Usare questa opzione se si vuole definire o creare uno spazio dei nomi e oggetti System personalizzati.</span><span class="sxs-lookup"><span data-stu-id="ec234-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="ec234-107">Se non si specifica **-nostdlib**, mscorlib.dll viene importata nel programma (equivale a specificare **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="ec234-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="ec234-108">Specificare **-nostdlib** equivale a specificare **-nostdlib+** .</span><span class="sxs-lookup"><span data-stu-id="ec234-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="ec234-109">Per impostare questa opzione del compilatore in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec234-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="ec234-110">Le istruzioni seguenti si applicano solo a Visual Studio 2015 (e versioni precedenti).</span><span class="sxs-lookup"><span data-stu-id="ec234-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="ec234-111">La proprietà di compilazione **Ometti riferimenti a mscorlib.dll** non esiste in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ec234-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="ec234-112">Aprire la pagina **Proprietà** del progetto.</span><span class="sxs-lookup"><span data-stu-id="ec234-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="ec234-113">Fare clic sulla pagina di proprietà **Compilazione** .</span><span class="sxs-lookup"><span data-stu-id="ec234-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="ec234-114">Fare clic su **Avanzate** .</span><span class="sxs-lookup"><span data-stu-id="ec234-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="ec234-115">Modificare la proprietà **Ometti riferimenti a libreria standard (mscorlib.dll)** .</span><span class="sxs-lookup"><span data-stu-id="ec234-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="ec234-116">Per impostare l'opzione del compilatore a livello di codice</span><span class="sxs-lookup"><span data-stu-id="ec234-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="ec234-117">Per informazioni su come impostare questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec234-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec234-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec234-118">See also</span></span>

- [<span data-ttu-id="ec234-119">Opzioni del compilatore C#</span><span class="sxs-lookup"><span data-stu-id="ec234-119">C# Compiler Options</span></span>](./index.md)
