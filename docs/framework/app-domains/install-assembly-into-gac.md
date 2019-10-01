---
title: 'Procedura: Installare un assembly nella Global Assembly Cache'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972935"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="9f512-102">Procedura: Installare un assembly nella Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9f512-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="9f512-103">Gli assembly condivisi da più applicazioni vengono archiviati nella Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="9f512-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="9f512-104">Installare un assembly nella [Global Assembly Cache](gac.md) con uno dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9f512-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="9f512-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9f512-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="9f512-106">Strumento Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="9f512-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="9f512-107">È possibile installare solo assembly con nome sicuro in Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="9f512-108">Per informazioni sulla creazione di un assembly con nome sicuro, vedere [Procedura: Firmare un assembly con un nome sicuro](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9f512-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="9f512-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9f512-109">Windows Installer</span></span>

<span data-ttu-id="9f512-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), il motore di installazione di Windows, è la scelta consigliata per aggiungere gli assembly alla Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="9f512-111">Windows Installer ottiene il conteggio dei riferimenti degli assembly nella Global Assembly Cache e altre utili funzionalità.</span><span class="sxs-lookup"><span data-stu-id="9f512-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="9f512-112">Per creare un pacchetto di installazione per Windows Installer, usare l'[estensione WiX Toolset per Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="9f512-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="9f512-113">Global Assembly Cache (strumento)</span><span class="sxs-lookup"><span data-stu-id="9f512-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="9f512-114">È possibile utilizzare l' [utilità Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) per aggiungere assembly al Global assembly cache e visualizzare il contenuto del Global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9f512-115">*Gacutil.exe* è progettato esclusivamente per lo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="9f512-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="9f512-116">Non usarlo per installare assembly di produzione nella Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="9f512-117">La sintassi per usare *gacutil.exe* per installare un assembly nella Global Assembly Cache è la seguente:</span><span class="sxs-lookup"><span data-stu-id="9f512-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="9f512-118">In questo comando *\<nome assembly>* è il nome dell'assembly da installare nella Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="9f512-119">Se *gacutil. exe* non è presente nel percorso di sistema, usare il [prompt dei comandi per gli sviluppatori per la  *\<versione*di Visual Studio >](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9f512-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="9f512-120">L'esempio seguente consente di installare un assembly con nome file *hello.dll* nella Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9f512-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="9f512-121">Nelle versioni precedenti di .NET Framework, l'estensione della shell di Windows *Shfusion.dll* consente di installare gli assembly trascinandoli in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="9f512-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="9f512-122">A partire da .NET Framework 4, *Shfusion.dll* è obsoleto.</span><span class="sxs-lookup"><span data-stu-id="9f512-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f512-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f512-123">See also</span></span>

- [<span data-ttu-id="9f512-124">Usare gli assembly e i Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9f512-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="9f512-125">Procedura: Rimuovere un assembly dalla Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9f512-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="9f512-126">Gacutil. exe (strumento Global assembly cache)</span><span class="sxs-lookup"><span data-stu-id="9f512-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="9f512-127">Procedura: Firmare un assembly con un nome sicuro</span><span class="sxs-lookup"><span data-stu-id="9f512-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)