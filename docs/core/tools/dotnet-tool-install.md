---
title: Comando dotnet tool install
description: Il comando dotnet tool install installa lo strumento globale .NET Core specificato nel computer.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117468"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="afe7b-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="afe7b-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="afe7b-104">nome</span><span class="sxs-lookup"><span data-stu-id="afe7b-104">Name</span></span>

<span data-ttu-id="afe7b-105">`dotnet tool install` - Installa lo [strumento globale .NET Core](global-tools.md) specificato nel computer.</span><span class="sxs-lookup"><span data-stu-id="afe7b-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="afe7b-106">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="afe7b-106">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="afe7b-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="afe7b-107">Description</span></span>

<span data-ttu-id="afe7b-108">Il comando `dotnet tool install` consente di installare gli strumenti globali .NET Core nel computer.</span><span class="sxs-lookup"><span data-stu-id="afe7b-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="afe7b-109">Per usare il comando, è necessario specificare che si vuole un'installazione a livello utente con l'opzione `--global` oppure specificare un percorso per l'installazione con l'opzione `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="afe7b-110">Gli strumenti globali vengono installati nelle directory seguenti per impostazione predefinita quando si specifica l'opzione `-g` (o `--global`):</span><span class="sxs-lookup"><span data-stu-id="afe7b-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="afe7b-111">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="afe7b-111">OS</span></span>          | <span data-ttu-id="afe7b-112">Path</span><span class="sxs-lookup"><span data-stu-id="afe7b-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="afe7b-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="afe7b-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="afe7b-114">WINDOWS</span><span class="sxs-lookup"><span data-stu-id="afe7b-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="afe7b-115">Argomenti</span><span class="sxs-lookup"><span data-stu-id="afe7b-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="afe7b-116">Nome/ID del pacchetto NuGet che contiene lo strumento globale .NET Core da installare.</span><span class="sxs-lookup"><span data-stu-id="afe7b-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="afe7b-117">Opzioni</span><span class="sxs-lookup"><span data-stu-id="afe7b-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="afe7b-118">Aggiunge un'altra origine pacchetto NuGet da usare durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="afe7b-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="afe7b-119">File di configurazione NuGet (*nuget.config*) da usare.</span><span class="sxs-lookup"><span data-stu-id="afe7b-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="afe7b-120">Specifica il [framework di destinazione](../../standard/frameworks.md) per cui installare lo strumento.</span><span class="sxs-lookup"><span data-stu-id="afe7b-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="afe7b-121">Per impostazione predefinita, .NET Core SDK tenta di scegliere il framework di destinazione più appropriato.</span><span class="sxs-lookup"><span data-stu-id="afe7b-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="afe7b-122">Specifica che l'installazione è a livello utente.</span><span class="sxs-lookup"><span data-stu-id="afe7b-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="afe7b-123">Non può essere usata con l'opzione `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="afe7b-124">Se non si specifica questa opzione, è necessario specificare l'opzione `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="afe7b-125">Stampa una breve guida per il comando.</span><span class="sxs-lookup"><span data-stu-id="afe7b-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="afe7b-126">Specifica il percorso in cui disinstallare lo strumento globale.</span><span class="sxs-lookup"><span data-stu-id="afe7b-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="afe7b-127">Il valore di PATH può essere assoluto o relativo.</span><span class="sxs-lookup"><span data-stu-id="afe7b-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="afe7b-128">Se PATH non esiste, il comando tenta di creare la variabile.</span><span class="sxs-lookup"><span data-stu-id="afe7b-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="afe7b-129">Non può essere usata con l'opzione `--global`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="afe7b-130">Se non si specifica questa opzione, è necessario specificare l'opzione `--global`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="afe7b-131">Imposta il livello di dettaglio del comando.</span><span class="sxs-lookup"><span data-stu-id="afe7b-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="afe7b-132">I valori consentiti sono `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="afe7b-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="afe7b-133">La versione dello strumento da installare.</span><span class="sxs-lookup"><span data-stu-id="afe7b-133">The version of the tool to install.</span></span> <span data-ttu-id="afe7b-134">Per impostazione predefinita, viene installata la versione del pacchetto stabile più recente.</span><span class="sxs-lookup"><span data-stu-id="afe7b-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="afe7b-135">Usare questa opzione per installare le versioni di anteprima o precedenti dello strumento.</span><span class="sxs-lookup"><span data-stu-id="afe7b-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="afe7b-136">Esempi</span><span class="sxs-lookup"><span data-stu-id="afe7b-136">Examples</span></span>

<span data-ttu-id="afe7b-137">Installa lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nel percorso predefinito:</span><span class="sxs-lookup"><span data-stu-id="afe7b-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="afe7b-138">Installa lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/) in una cartella di Windows specifica:</span><span class="sxs-lookup"><span data-stu-id="afe7b-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="afe7b-139">Installa lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/) in una cartella di Linux/macOS specifica:</span><span class="sxs-lookup"><span data-stu-id="afe7b-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="afe7b-140">Installa la versione 2.0.0 dello strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/):</span><span class="sxs-lookup"><span data-stu-id="afe7b-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="afe7b-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="afe7b-141">See also</span></span>

- [<span data-ttu-id="afe7b-142">Strumenti globali .NET Core</span><span class="sxs-lookup"><span data-stu-id="afe7b-142">.NET Core Global Tools</span></span>](global-tools.md)
