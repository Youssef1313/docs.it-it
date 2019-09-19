---
title: Prerequisiti per .NET Core in Linux
description: Versioni Linux supportate e dipendenze .NET Core necessarie per lo sviluppo, la distribuzione e l'esecuzione di applicazioni .NET Core su computer Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 31c53b2cc0fe576e56685f4a5561258136fd2541
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116584"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="c6cc6-103">Prerequisiti per .NET Core in Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="c6cc6-104">Questo articolo illustra le dipendenze necessarie per sviluppare applicazioni .NET Core in Linux.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="c6cc6-105">Le distribuzioni/versioni Linux supportate e le dipendenze seguenti si applicano alle due modalità di sviluppo di app .NET Core in Linux:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="c6cc6-106">Riga di comando con l'editor preferito</span><span class="sxs-lookup"><span data-stu-id="c6cc6-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="c6cc6-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c6cc6-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="c6cc6-108">Il pacchetto .NET Core SDK non è richiesto per ambienti/server di produzione.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="c6cc6-109">È necessario solo il pacchetto di runtime di .NET Core per le app distribuite in ambienti di produzione.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="c6cc6-110">Il runtime di .NET Core viene distribuito con le app nell'ambito di una distribuzione indipendente, ma deve essere distribuito separatamente per le app dipendenti dal framework.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="c6cc6-111">Per altre informazioni sui tipi di distribuzione indipendenti e dipendenti dal framework, vedere [Distribuzione di applicazioni .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="c6cc6-112">Per linee guida specifiche, vedere anche [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Applicazioni Linux indipendenti).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="c6cc6-113">Versioni di Linux supportate</span><span class="sxs-lookup"><span data-stu-id="c6cc6-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6cc6-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c6cc6-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c6cc6-115">.NET Core 2.x considera Linux come un singolo sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="c6cc6-116">Esiste una sola build di Linux (per l'architettura chip) per le distribuzioni di Linux supportate.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="c6cc6-117">Per i collegamenti per il download e altre informazioni, vedere [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) (Download di .NET Core 2.2) o [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1) (Download di .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="c6cc6-118">.NET Core 2.x è supportato nelle seguenti distribuzioni/versioni Linux:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="c6cc6-119">Red Hat Enterprise Linux 7, 6 a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-120">CentOS 7 a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="c6cc6-121">Oracle Linux 7 a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="c6cc6-122">Fedora 28, 27 a 64-bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="c6cc6-123">Debian 9 (a 64 bit, `arm32`), 8.7 o versioni successive a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-124">Ubuntu 18.04 (a 64 bit `arm32`), 16.04, 14.04 a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-125">Linux Mint 18, 17 a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-126">openSUSE 42.3 o versioni successive a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 o versioni successive a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="c6cc6-128">Alpine Linux 3.7 o versioni successive a 64 bit (`x86_64` o `amd64`)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="c6cc6-129">Per l'elenco completo dei sistemi operativi, delle versioni e delle distribuzioni supportati da .NET Core 2.1 e .NET Core 2.2, nonché delle versioni di sistemi operativi non supportate e dei criteri relativi al ciclo di vita, vedere [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) (.NET Core 2.1 - Versioni di sistemi operativi supportate) e [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) (.NET Core 2.2 - Versioni di sistemi operativi supportate).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6cc6-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c6cc6-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c6cc6-131">Per i collegamenti per il download e altre informazioni, vedere [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) (Download di .NET Core 1.1) o [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0) (Download di .NET Core 1.0).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="c6cc6-132">NET Core 1.x è supportato nelle versioni/distribuzioni di Linux a 64 bit (`x86_64` o `amd64`) seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="c6cc6-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c6cc6-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="c6cc6-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6cc6-134">CentOS 7</span></span>
* <span data-ttu-id="c6cc6-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c6cc6-135">Oracle Linux 7</span></span>
* <span data-ttu-id="c6cc6-136">Fedora 28 (.NET Core 1.1), 27</span><span class="sxs-lookup"><span data-stu-id="c6cc6-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="c6cc6-137">Debian 8.2 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="c6cc6-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="c6cc6-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="c6cc6-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="c6cc6-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="c6cc6-139">Linux Mint 17</span></span>
* <span data-ttu-id="c6cc6-140">openSUSE 42.3 o versioni successive (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="c6cc6-141">Per l'elenco completo di sistemi operativi, supportati da .NET Core 1.x, le versioni di sistemi operativi non supportate e i criteri relativi al ciclo di vita, vedere [.NET Core 1.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (.NET Core 2.x - Versioni di sistemi operativi supportate).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="c6cc6-142">.NET Core 3.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c6cc6-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="c6cc6-143">.NET core 3.0 Preview 1 considera Linux come un singolo sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="c6cc6-144">Esiste una sola build di Linux (per l'architettura chip) per le distribuzioni di Linux supportate.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="c6cc6-145">Per i collegamenti di download e altre informazioni, vedere [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) (Download di .NET Core 3.0).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="c6cc6-146">.NET Core 3.0 Preview 1 è supportato nelle seguenti distribuzioni/versioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="c6cc6-147">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="c6cc6-147">OS</span></span>                            | <span data-ttu-id="c6cc6-148">Versione</span><span class="sxs-lookup"><span data-stu-id="c6cc6-148">Version</span></span>               | <span data-ttu-id="c6cc6-149">Architetture</span><span class="sxs-lookup"><span data-stu-id="c6cc6-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="c6cc6-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="c6cc6-151">6</span><span class="sxs-lookup"><span data-stu-id="c6cc6-151">6</span></span>                     | <span data-ttu-id="c6cc6-152">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-152">x64</span></span>
<span data-ttu-id="c6cc6-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="c6cc6-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="c6cc6-154">CentOS</span></span><br><span data-ttu-id="c6cc6-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-155">Oracle Linux</span></span>  | <span data-ttu-id="c6cc6-156">7</span><span class="sxs-lookup"><span data-stu-id="c6cc6-156">7</span></span>                     | <span data-ttu-id="c6cc6-157">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-157">x64</span></span>
<span data-ttu-id="c6cc6-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="c6cc6-158">Fedora</span></span>                        | <span data-ttu-id="c6cc6-159">28</span><span class="sxs-lookup"><span data-stu-id="c6cc6-159">28</span></span>                    | <span data-ttu-id="c6cc6-160">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-160">x64</span></span>
<span data-ttu-id="c6cc6-161">Debian</span><span class="sxs-lookup"><span data-stu-id="c6cc6-161">Debian</span></span>                        | <span data-ttu-id="c6cc6-162">9</span><span class="sxs-lookup"><span data-stu-id="c6cc6-162">9</span></span>                     | <span data-ttu-id="c6cc6-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="c6cc6-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="c6cc6-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c6cc6-164">Ubuntu</span></span>                        | <span data-ttu-id="c6cc6-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="c6cc6-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="c6cc6-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="c6cc6-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="c6cc6-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="c6cc6-167">Linux Mint</span></span>                    | <span data-ttu-id="c6cc6-168">18</span><span class="sxs-lookup"><span data-stu-id="c6cc6-168">18</span></span>                    | <span data-ttu-id="c6cc6-169">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-169">x64</span></span>
<span data-ttu-id="c6cc6-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c6cc6-170">openSUSE</span></span>                      | <span data-ttu-id="c6cc6-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="c6cc6-171">42.3+</span></span>                 | <span data-ttu-id="c6cc6-172">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-172">x64</span></span>
<span data-ttu-id="c6cc6-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="c6cc6-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="c6cc6-174">12 SP2+</span></span>               | <span data-ttu-id="c6cc6-175">X64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-175">x64</span></span>
<span data-ttu-id="c6cc6-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-176">Alpine Linux</span></span>                  | <span data-ttu-id="c6cc6-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="c6cc6-177">3.8+</span></span>                  | <span data-ttu-id="c6cc6-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="c6cc6-178">x64, ARM64</span></span>

<span data-ttu-id="c6cc6-179">\* Il supporto di ARM64 e ARM32 inizia con Debian 9 e Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="c6cc6-180">Le versioni precedenti di queste distribuzioni non sono supportate nei chip ARM.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="c6cc6-181">Per l'elenco completo dei sistemi operativi, delle versioni e delle distribuzioni supportate da .NET Core 3.0, nonché delle versioni di sistemi operativi non supportate e dei criteri relativi al ciclo di vita, vedere [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) (.NET Core 3.0 - Versioni di sistemi operativi supportate).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="c6cc6-182">Per altre informazioni su come installare .NET Core 3.0 su ARM64, vedere [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213) (Installazione di .NET Core 3.0 su Linux ARM64).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="c6cc6-183">Dipendenze delle distribuzioni Linux</span><span class="sxs-lookup"><span data-stu-id="c6cc6-183">Linux distribution dependencies</span></span>

<span data-ttu-id="c6cc6-184">Quelli che seguono sono esempi.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-184">The following are intended to be examples.</span></span> <span data-ttu-id="c6cc6-185">Le versioni e i nomi esatti possono variare leggermente nella distribuzione di Linux scelta.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="c6cc6-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c6cc6-186">Ubuntu</span></span>

<span data-ttu-id="c6cc6-187">Le distribuzioni Ubuntu richiedono che siano installate le librerie seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="c6cc6-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="c6cc6-188">liblttng-ust0</span></span>
* <span data-ttu-id="c6cc6-189">libcurl3 (per 14.x e 16.x)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="c6cc6-190">libcurl4 (per 18.x)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="c6cc6-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="c6cc6-191">libssl1.0.0</span></span>
* <span data-ttu-id="c6cc6-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="c6cc6-192">libkrb5-3</span></span>
* <span data-ttu-id="c6cc6-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="c6cc6-193">zlib1g</span></span>
* <span data-ttu-id="c6cc6-194">libicu52 (per 14.X)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="c6cc6-195">libicu55 (per 16.X)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="c6cc6-196">libicu57 (per 17.X)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="c6cc6-197">libicu60 (per 18.x)</span><span class="sxs-lookup"><span data-stu-id="c6cc6-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="c6cc6-198">Per le versioni precedenti a .NET Core 2.1, sono richieste anche le dipendenze seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="c6cc6-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="c6cc6-199">libunwind8</span></span>
* <span data-ttu-id="c6cc6-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="c6cc6-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="c6cc6-201">CentOS e Fedora</span><span class="sxs-lookup"><span data-stu-id="c6cc6-201">CentOS and Fedora</span></span>

<span data-ttu-id="c6cc6-202">Le distribuzioni CentOS richiedono che siano installate le librerie seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="c6cc6-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="c6cc6-203">lttng-ust</span></span>
* <span data-ttu-id="c6cc6-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="c6cc6-204">libcurl</span></span>
* <span data-ttu-id="c6cc6-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="c6cc6-205">openssl-libs</span></span>
* <span data-ttu-id="c6cc6-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="c6cc6-206">krb5-libs</span></span>
* <span data-ttu-id="c6cc6-207">libicu</span><span class="sxs-lookup"><span data-stu-id="c6cc6-207">libicu</span></span>
* <span data-ttu-id="c6cc6-208">zlib</span><span class="sxs-lookup"><span data-stu-id="c6cc6-208">zlib</span></span>

<span data-ttu-id="c6cc6-209">Utenti Fedora: se la versione di openssl in uso è maggiore o uguale a 1.1, è necessario installare compat-openssl10.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="c6cc6-210">Per le versioni precedenti a .NET Core 2.1, sono richieste anche le dipendenze seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="c6cc6-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="c6cc6-211">libunwind</span></span>
* <span data-ttu-id="c6cc6-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="c6cc6-212">libuuid</span></span>

<span data-ttu-id="c6cc6-213">Per altre informazioni sulle dipendenze, vedere [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Applicazioni Linux autonome).</span><span class="sxs-lookup"><span data-stu-id="c6cc6-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="c6cc6-214">Installazione delle dipendenze di .NET Core con i programmi di installazione nativi</span><span class="sxs-lookup"><span data-stu-id="c6cc6-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="c6cc6-215">Sono disponibili programmi di installazione .NET Core nativi per le distribuzioni/versioni di Linux supportate.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="c6cc6-216">I programmi di installazione richiedono l'accesso amministratore (sudo) al server.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="c6cc6-217">L'uso di un programma di installazione nativo offre il vantaggio di installare tutte le dipendenze native .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="c6cc6-218">I programmi di installazione nativi installano.NET Core SDK a livello di sistema.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="c6cc6-219">In Linux sono disponibili due opzioni relative al pacchetto di installazione:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="c6cc6-220">L'utilizzo di un sistema di gestione pacchetti basato su feed, ad esempio apt-get per Ubuntu o yum per CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="c6cc6-221">L'utilizzo dei pacchetti stessi, DEB o RPM.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="c6cc6-222">Gli script vengono installati con lo script di installazione di .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cc6-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="c6cc6-223">Gli [script dotnet-install](./tools/dotnet-install-script.md) vengono usati per eseguire un'installazione senza privilegi di amministratore della toolchain dell'interfaccia della riga di comando e del runtime condiviso.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="c6cc6-224">È possibile scaricare lo script da <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="c6cc6-225">Lo script assume come impostazione predefinita l'installazione della versione "LTS" più recente, che è attualmente .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="c6cc6-226">Per installare .NET Core 2.1, eseguire lo script con l'opzione seguente:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="c6cc6-227">Lo script bash del programma di installazione viene usato negli scenari di automazione e nelle installazioni non di amministratore.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="c6cc6-228">Questo script legge anche le opzioni PowerShell, che possono quindi essere usate con lo script nei sistemi Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="c6cc6-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="c6cc6-229">Risolvere i problemi</span><span class="sxs-lookup"><span data-stu-id="c6cc6-229">Troubleshoot</span></span>

<span data-ttu-id="c6cc6-230">Se si verificano problemi in fase di installazione di .NET Core in una distribuzione/versione Linux supportata, vedere i seguenti argomenti per le distribuzioni/versioni installate in uso:</span><span class="sxs-lookup"><span data-stu-id="c6cc6-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="c6cc6-231">Problemi noti relativi a .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c6cc6-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="c6cc6-232">Problemi noti relativi a .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c6cc6-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="c6cc6-233">Problemi noti relativi a .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c6cc6-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="c6cc6-234">Problemi noti relativi a .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="c6cc6-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="c6cc6-235">Problemi noti relativi a .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c6cc6-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
