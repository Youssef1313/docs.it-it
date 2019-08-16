---
title: Indicazioni generali
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Indicazioni generali
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675798"
---
# <a name="general-guidance"></a><span data-ttu-id="286c5-103">Indicazioni generali</span><span class="sxs-lookup"><span data-stu-id="286c5-103">General guidance</span></span>

<span data-ttu-id="286c5-104">Questa sezione contiene un riepilogo dei casi in cui è consigliabile scegliere .NET Core o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="286c5-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="286c5-105">Altri dettagli su questo tipo di scelta sono disponibili nelle sezioni successive.</span><span class="sxs-lookup"><span data-stu-id="286c5-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="286c5-106">È consigliabile usare .NET Core, con contenitori Linux o Windows, per l'applicazione server Docker in contenitori nei casi seguenti:</span><span class="sxs-lookup"><span data-stu-id="286c5-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="286c5-107">Si hanno esigenze multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="286c5-107">You have cross-platform needs.</span></span> <span data-ttu-id="286c5-108">Ad esempio, si vogliono usare sia contenitori Windows sia contenitori Linux.</span><span class="sxs-lookup"><span data-stu-id="286c5-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="286c5-109">L'architettura dell'applicazione si basa su microservizi.</span><span class="sxs-lookup"><span data-stu-id="286c5-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="286c5-110">I contenitori devono essere avviati in modo rapido e il footprint per ogni contenitore deve essere ridotto al fine di garantire una migliore densità o più contenitori per unità hardware e ridurre al tempo stesso i costi.</span><span class="sxs-lookup"><span data-stu-id="286c5-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="286c5-111">In breve, quando si creano nuove applicazioni .NET in contenitori, considerare .NET Core come scelta predefinita.</span><span class="sxs-lookup"><span data-stu-id="286c5-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="286c5-112">Offre più vantaggi e si adatta meglio alla filosofia dei contenitori e allo stile di lavoro.</span><span class="sxs-lookup"><span data-stu-id="286c5-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="286c5-113">Un altro vantaggio dato dall'uso di .NET Core consiste nel fatto che è possibile eseguire in modo affiancato le versioni .NET delle applicazioni che si trovano all'interno dello stesso computer.</span><span class="sxs-lookup"><span data-stu-id="286c5-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="286c5-114">Questo vantaggio è più importante per i server o le macchine virtuali che non usano i contenitori, in quanto i contenitori isolano le versioni di .NET necessarie all'app.</span><span class="sxs-lookup"><span data-stu-id="286c5-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="286c5-115">È tuttavia necessario che siano compatibili con il sistema operativo sottostante.</span><span class="sxs-lookup"><span data-stu-id="286c5-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="286c5-116">È consigliabile usare .NET Framework per l'applicazione server Docker in contenitori nei casi seguenti:</span><span class="sxs-lookup"><span data-stu-id="286c5-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="286c5-117">L'applicazione attualmente usa .NET Framework ed è fortemente dipendente da Windows.</span><span class="sxs-lookup"><span data-stu-id="286c5-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="286c5-118">È necessario usare API Windows che non sono supportate da .NET Core.</span><span class="sxs-lookup"><span data-stu-id="286c5-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="286c5-119">È necessario usare librerie .NET di terze parti o pacchetti NuGet che non sono disponibili per .NET Core.</span><span class="sxs-lookup"><span data-stu-id="286c5-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="286c5-120">L'uso di .NET Framework in Docker può migliorare le esperienze di distribuzione e ridurne al minimo i problemi.</span><span class="sxs-lookup"><span data-stu-id="286c5-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="286c5-121">Questo [scenario di trasferimento in modalità lift-and-shift](https://aka.ms/liftandshiftwithcontainersebook) è importante per l'inserimento in contenitori di applicazioni legacy che sono state originariamente sviluppate con .NET Framework tradizionale, ad esempio Web Form ASP.NET, app Web MVC o servizi WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="286c5-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="286c5-122">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="286c5-122">Additional resources</span></span>

- <span data-ttu-id="286c5-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers** (eBook: Modernizzare le applicazioni .NET Framework esistenti con i contenitori di Azure e Windows)</span><span class="sxs-lookup"><span data-stu-id="286c5-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="286c5-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers** (App di esempio: Modernizzazione delle app Web ASP.NET legacy usando contenitori Windows)</span><span class="sxs-lookup"><span data-stu-id="286c5-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="286c5-125">[Precedente](index.md)
>[Successivo](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="286c5-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>