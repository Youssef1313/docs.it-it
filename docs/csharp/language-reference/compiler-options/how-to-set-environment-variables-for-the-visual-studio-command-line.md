---
title: Come impostare le variabili di ambiente per la riga di comando di Visual Studio
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 3b69a92d28663bbbd34245435a69aea80d20fdc9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972838"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="30170-102">Come impostare le variabili di ambiente per la riga di comando di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30170-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="30170-103">Il file VsDevCmd.bat imposta le variabili di ambiente appropriate per abilitare le compilazioni da riga di comando.</span><span class="sxs-lookup"><span data-stu-id="30170-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="30170-104">Il file VsDevCmd.bat è un nuovo file fornito con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="30170-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="30170-105">Visual Studio 2015 e versioni precedenti usano VSVARS32.bat per gli stessi scopi.</span><span class="sxs-lookup"><span data-stu-id="30170-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="30170-106">Il file era archiviato in \Programmi\Microsoft Visual Studio\\*Versione*\Common7\Tools o Programmi (x86)\Microsoft Visual Studio\\*Versione*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="30170-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="30170-107">Se la versione corrente di Visual Studio è installata in un computer che include anche la versione precedente di Visual Studio, non eseguire VsDevCmd.bat e VSVARS32.BAT da diverse versioni nella stessa finestra del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="30170-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="30170-108">È invece necessario eseguire il comando per ogni versione in una finestra specifica.</span><span class="sxs-lookup"><span data-stu-id="30170-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="30170-109">Per eseguire VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="30170-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="30170-110">Dal menu **Start** aprire il **Prompt dei comandi per gli sviluppatori per VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="30170-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="30170-111">È disponibile nella cartella **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="30170-111">It's in the **Visual Studio 2017** folder.</span></span>

2. <span data-ttu-id="30170-112">Passare alla sottodirectory di installazione \Programmi\Microsoft Visual Studio\\*Versione*\\*Offerta*\Common7\Tools o \Programmi (x86)\Microsoft Visual Studio\\*Versione*\\*Offerta*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="30170-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="30170-113">(*Versione* è *2017* per la versione corrente.</span><span class="sxs-lookup"><span data-stu-id="30170-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="30170-114">*Offerta* è *Enterprise*, *Professional* o *Community*.)</span><span class="sxs-lookup"><span data-stu-id="30170-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="30170-115">Eseguire VsDevCmd.bat digitando **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="30170-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="30170-116">Il file VsDevCmd.bat può variare da computer a computer.</span><span class="sxs-lookup"><span data-stu-id="30170-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="30170-117">Non sostituire un file VsDevCmd.bat mancante o danneggiato con un file VsDevCmd.bat da un altro computer.</span><span class="sxs-lookup"><span data-stu-id="30170-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="30170-118">Rieseguire invece l'installazione per sostituire il file mancante.</span><span class="sxs-lookup"><span data-stu-id="30170-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="30170-119">Opzioni disponibili per VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="30170-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="30170-120">Per visualizzare le opzioni disponibili per VsDevCmd.BAT, eseguire il comando con l'opzione `-help`:</span><span class="sxs-lookup"><span data-stu-id="30170-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="30170-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="30170-121">See also</span></span>

- [<span data-ttu-id="30170-122">Compilazione dalla riga di comando con csc.exe</span><span class="sxs-lookup"><span data-stu-id="30170-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
