---
title: Quando scegliere .NET Framework per i contenitori Docker
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Quando scegliere .NET Framework per i contenitori Docker
ms.date: 01/07/2019
ms.openlocfilehash: 53164654710775320f023df9fb56a78506bd3a1a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675738"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="f4a74-103">Quando scegliere .NET Framework per i contenitori Docker</span><span class="sxs-lookup"><span data-stu-id="f4a74-103">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="f4a74-104">Sebbene .NET Core offra vantaggi significativi per le nuove applicazioni e i nuovi schemi di applicazioni, .NET Framework continua a rappresentare la scelta naturale per molti scenari esistenti.</span><span class="sxs-lookup"><span data-stu-id="f4a74-104">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="f4a74-105">Migrazione delle applicazioni esistenti direttamente in un contenitore Windows Server</span><span class="sxs-lookup"><span data-stu-id="f4a74-105">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="f4a74-106">È possibile usare i contenitori Docker anche solo per semplificare la distribuzione, pur non creando microservizi.</span><span class="sxs-lookup"><span data-stu-id="f4a74-106">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="f4a74-107">Ad esempio, se si vuole migliorare il flusso DevOps con Docker, i contenitori possono offrire ambienti di test con un isolamento migliore ed eliminare i problemi di distribuzione causati da dipendenze mancanti al momento dello spostamento in un ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="f4a74-107">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="f4a74-108">In questi casi, anche se si distribuisce un'applicazione monolitica, è consigliabile usare Docker e i contenitori Windows per le applicazioni .NET Framework correnti.</span><span class="sxs-lookup"><span data-stu-id="f4a74-108">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="f4a74-109">Nella maggior parte dei casi per questo scenario, non sarà necessario eseguire la migrazione delle applicazioni esistenti a .NET Core. È possibile usare contenitori Docker che includono .NET Framework tradizionale.</span><span class="sxs-lookup"><span data-stu-id="f4a74-109">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="f4a74-110">Tuttavia, un approccio consigliato prevede di usare .NET Core per estendere un'applicazione esistente, ad esempio con la scrittura di un nuovo servizio in ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-110">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="f4a74-111">Utilizzo di pacchetti NuGet o di librerie .NET di terze parti non disponibili per .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4a74-111">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="f4a74-112">Le librerie di terze parti stanno rapidamente adottando [.NET Standard](../../../standard/net-standard.md), che consente la condivisione di codice tra tutte le versioni di .NET incluso .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-112">Third-party libraries are quickly embracing the [.NET Standard](../../../standard/net-standard.md), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="f4a74-113">Con la libreria .NET Standard 2.0 e versioni successive la compatibilità della superficie dell'API tra framework diversi è aumentata in modo significativo e in .NET Core 2.x le applicazioni possono anche fare riferimento direttamente alle librerie .NET Framework esistenti. Vedere [.NET Framework 4.6.1 supporting .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20) (Supporto di .NET Standard 2.0 in .NET Framework 4.6.1).</span><span class="sxs-lookup"><span data-stu-id="f4a74-113">With the .NET Standard Library 2.0 and beyond the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.x applications can also directly reference existing .NET Framework libraries (see [.NET Framework 4.6.1 supporting .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).</span></span>

<span data-ttu-id="f4a74-114">A novembre 2017 è stato anche rilasciato [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md) che consente di estendere la superficie dell'API disponibile per .NET Standard 2.0 in Windows.</span><span class="sxs-lookup"><span data-stu-id="f4a74-114">In addition, the [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md) was released on NOV-2017 to extend the API surface available for .NET Standard 2.0 on Windows.</span></span> <span data-ttu-id="f4a74-115">Questo pacchetto consente di ricompilare la maggior parte del codice esistente per .NET Standard 2.x con modifiche minime o nulle, da eseguire in Windows.</span><span class="sxs-lookup"><span data-stu-id="f4a74-115">This pack allows recompiling most existing code to .NET Standard 2.x with little or no modification, to run on Windows.</span></span>

<span data-ttu-id="f4a74-116">Tuttavia, nonostante questo avanzamento eccezionale a partire da .NET Standard 2.0 e .NET Core 2.1, in determinati casi per eseguire alcuni pacchetti NuGet potrebbe essere necessario usare Windows perché questi non supportano .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-116">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.1, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="f4a74-117">Se questi pacchetti sono vitali per l'applicazione, sarà necessario usare .NET Framework in contenitori Windows.</span><span class="sxs-lookup"><span data-stu-id="f4a74-117">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="using-net-technologies-not-available-for-net-core"></a><span data-ttu-id="f4a74-118">Utilizzo di tecnologie .NET non disponibili per .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4a74-118">Using .NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="f4a74-119">Alcune tecnologie .NET Framework non sono disponibili nella versione corrente di .NET Core, ovvero la versione 2.2 al momento della stesura del presente documento.</span><span class="sxs-lookup"><span data-stu-id="f4a74-119">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.2 as of this writing).</span></span> <span data-ttu-id="f4a74-120">Alcune saranno disponibili in versioni future di .NET Core (.NET Core 2.x), ma altre non si applicano ai nuovi schemi di applicazioni basati su .NET Core ed è possibile che non vengano mai rese disponibili.</span><span class="sxs-lookup"><span data-stu-id="f4a74-120">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="f4a74-121">L'elenco seguente illustra la maggior parte delle tecnologie non disponibili in .NET Core 2.x:</span><span class="sxs-lookup"><span data-stu-id="f4a74-121">The following list shows most of the technologies that are not available in .NET Core 2.x:</span></span>

- <span data-ttu-id="f4a74-122">Web Form ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f4a74-122">ASP.NET Web Forms.</span></span> <span data-ttu-id="f4a74-123">Questa tecnologia è disponibile solo in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4a74-123">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="f4a74-124">Attualmente non è previsto il trasferimento di Web Form ASP.NET in .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-124">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

- <span data-ttu-id="f4a74-125">Servizi WCF.</span><span class="sxs-lookup"><span data-stu-id="f4a74-125">WCF services.</span></span> <span data-ttu-id="f4a74-126">Anche se, dalla metà del 2017, è disponibile una [libreria WCF client](https://github.com/dotnet/wcf) per l'utilizzo di servizi WCF da .NET Core, l'implementazione di server WCF è disponibile solo in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4a74-126">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core, as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="f4a74-127">Questo scenario potrebbe essere considerato per le versioni future di .NET Core. Anche alcune API sono considerate per l'inclusione in [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f4a74-127">This scenario might be considered for future releases of .NET Core, there are even some APIs considered for inclusion in the [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md).</span></span>

- <span data-ttu-id="f4a74-128">Servizi correlati ai flussi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="f4a74-128">Workflow-related services.</span></span> <span data-ttu-id="f4a74-129">Windows Workflow Foundation (WF), Servizi flusso di lavoro (WCF e WF in un unico servizio) e WCF Data Services (in precedenza "ADO.NET Data Services") sono disponibili solo in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4a74-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="f4a74-130">Al momento non è prevista l'introduzione in .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-130">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="f4a74-131">Oltre alle tecnologie elencate nella [roadmap per .NET Core](https://github.com/aspnet/Home/wiki/Roadmap) ufficiale, è possibile che in .NET Core vengano rese disponibili altre funzionalità.</span><span class="sxs-lookup"><span data-stu-id="f4a74-131">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="f4a74-132">Per un elenco completo, osservare gli elementi contrassegnati come [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) nella pagina CoreFX del sito GitHub.</span><span class="sxs-lookup"><span data-stu-id="f4a74-132">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="f4a74-133">Si noti che questo elenco non rappresenta un impegno da parte di Microsoft per rendere disponibili tali componenti in .NET Core, ma mostra solo il desiderio della community di procedere in tal senso.</span><span class="sxs-lookup"><span data-stu-id="f4a74-133">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core — the items simply capture requests from the community.</span></span> <span data-ttu-id="f4a74-134">Se si è interessati a uno dei componenti elencati in precedenza, è consigliabile partecipare alle discussioni su GitHub per far valere la propria opinione.</span><span class="sxs-lookup"><span data-stu-id="f4a74-134">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="f4a74-135">Inoltre, se si ritiene di dover aggiungere alcune osservazioni, è possibile [inserire un nuovo problema nel repository CoreFX](https://github.com/dotnet/corefx/issues/new).</span><span class="sxs-lookup"><span data-stu-id="f4a74-135">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

<span data-ttu-id="f4a74-136">Anche se .NET Core 3 (in corso di sviluppo al momento della stesura di questo articolo) includerà il supporto per molte delle API di .NET Framework esistenti, queste API sono progettate per il desktop e quindi non sono attualmente utili per i contenitori.</span><span class="sxs-lookup"><span data-stu-id="f4a74-136">Even though .NET Core 3 (at the time of this writing this is in the works) will include support for a lot of existing .NET Framework APIs, these are desktop oriented so, currently, they are of no use in the container world.</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="f4a74-137">Utilizzo di una piattaforma o di un'API che non supporta .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4a74-137">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="f4a74-138">Alcune piattaforme Microsoft o di terze parti non supportano .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-138">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="f4a74-139">Ad esempio, alcuni servizi di Azure forniscono un SDK non ancora disponibile per l'utilizzo in .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-139">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="f4a74-140">Si tratta di un problema temporaneo, perché alla fine tutti i servizi di Azure useranno .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4a74-140">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="f4a74-141">Ad esempio, [Azure DocumentDB SDK per .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) è stato rilasciato in anteprima il 16 novembre 2016 e ora è disponibile a livello generale come versione stabile.</span><span class="sxs-lookup"><span data-stu-id="f4a74-141">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="f4a74-142">Nel frattempo, se una piattaforma o un servizio in Azure ancora non supporta .NET Core tramite l'API client, è possibile usare l'API REST equivalente del servizio di Azure o l'SDK client in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4a74-142">In the meantime, if any platform or service in Azure still doesn't support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4a74-143">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="f4a74-143">Additional resources</span></span>

- <span data-ttu-id="f4a74-144">**Guida a .NET Core**</span><span class="sxs-lookup"><span data-stu-id="f4a74-144">**.NET Core Guide**</span></span>  
    [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- <span data-ttu-id="f4a74-145">**Porting from .NET Framework to .NET Core** (Portabilità da .NET Framework a .NET Core)</span><span class="sxs-lookup"><span data-stu-id="f4a74-145">**Porting from .NET Framework to .NET Core**</span></span>  
    [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- <span data-ttu-id="f4a74-146">**Guida di .NET Core in Docker** [https://docs.microsoft.com/dotnet/core/docker/intro-net-docker](../../../core/docker/intro-net-docker.md)</span><span class="sxs-lookup"><span data-stu-id="f4a74-146">**.NET Core on Docker Guide** [https://docs.microsoft.com/dotnet/core/docker/intro-net-docker](../../../core/docker/intro-net-docker.md)</span></span>

- <span data-ttu-id="f4a74-147">**.NET Components Overview** (Panoramica dei componenti .NET)</span><span class="sxs-lookup"><span data-stu-id="f4a74-147">**.NET Components Overview**</span></span>  
    [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
><span data-ttu-id="f4a74-148">[Precedente](net-core-container-scenarios.md)
>[Successivo](container-framework-choice-factors.md)</span><span class="sxs-lookup"><span data-stu-id="f4a74-148">[Previous](net-core-container-scenarios.md)
[Next](container-framework-choice-factors.md)</span></span>