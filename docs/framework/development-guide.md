---
title: Guida di sviluppo per .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
ms.openlocfilehash: abc392116aec8ffd8aa94f46ef97887c48516ca0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122472"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="4c3c8-102">Guida di sviluppo per .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c3c8-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="4c3c8-103">Questa sezione descrive come creare, configurare, sottoporre a debug, proteggere e distribuire app .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="4c3c8-104">In questa sezione vengono fornite informazioni sulle aree tecnologiche, ad esempio programmazione dinamica, interoperabilità, estendibilità, gestione della memoria e threading.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c3c8-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="4c3c8-105">In This Section</span></span>  
 [<span data-ttu-id="4c3c8-106">Concetti di base sulle applicazioni</span><span class="sxs-lookup"><span data-stu-id="4c3c8-106">Application Essentials</span></span>](../standard/application-essentials.md)  
 <span data-ttu-id="4c3c8-107">Vengono fornite informazioni sulle attività per lo sviluppo di app di base, quali programmazione con assembly e domini applicazione, uso di attributi, formattazione e tipi di base di analisi, uso di raccolte, gestione di eventi ed eccezioni, uso di file, flussi di dati e generics.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="4c3c8-108">Dati e modellazione</span><span class="sxs-lookup"><span data-stu-id="4c3c8-108">Data and Modeling</span></span>](./data/index.md)  
 <span data-ttu-id="4c3c8-109">Vengono fornite informazioni su come accedere ai dati mediante ADO.NET, LINQ (Language Integrated Query), WCF Data Services e XML.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="4c3c8-110">Applicazioni client</span><span class="sxs-lookup"><span data-stu-id="4c3c8-110">Client Applications</span></span>](develop-client-apps.md)  
 <span data-ttu-id="4c3c8-111">Viene illustrato come creare app basate su Windows usando Windows Presentation Foundation (WPF) o Windows Form.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="4c3c8-112">Applicazioni Web con ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4c3c8-112">Web Applications with ASP.NET</span></span>](develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="4c3c8-113">Vengono forniti collegamenti alle informazioni sull'utilizzo di ASP.NET per compilare applicazioni Web di livello aziendale con una codifica minima.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="4c3c8-114">Applicazioni orientate ai servizi con WCF</span><span class="sxs-lookup"><span data-stu-id="4c3c8-114">Service-Oriented Applications with WCF</span></span>](./wcf/index.md)  
 <span data-ttu-id="4c3c8-115">Viene descritto come usare Windows Communication Foundation (WCF) per compilare app orientate ai servizi sicure e affidabili.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="4c3c8-116">[Flussi di lavoro di compilazione con Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="4c3c8-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="4c3c8-117">Vengono fornite informazioni sul modello di programmazione, sugli esempi e sugli strumenti per Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="4c3c8-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="4c3c8-118">Applicazioni di servizi Windows</span><span class="sxs-lookup"><span data-stu-id="4c3c8-118">Windows Service Applications</span></span>](./windows-services/index.md)  
 <span data-ttu-id="4c3c8-119">Viene illustrato come usare Visual Studio e .NET Framework per creare un'app che viene installata come servizio e che avvia, arresta e diversamente controlla il proprio comportamento.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="4c3c8-120">Elaborazione parallela, concorrenza e programmazione asincrona in .NET</span><span class="sxs-lookup"><span data-stu-id="4c3c8-120">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="4c3c8-121">Vengono fornite informazioni sul threading gestito, sulla programmazione parallela e sui modelli di progettazione della programmazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="4c3c8-122">Programmazione di rete in .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c3c8-122">Network Programming in the .NET Framework</span></span>](./network-programming/index.md)  
 <span data-ttu-id="4c3c8-123">Viene descritta l'implementazione gestita, estendibile e a più livelli dei servizi Internet che è possibile integrare nelle app in modo rapido e semplice.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="4c3c8-124">[Configurazione di app .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="4c3c8-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="4c3c8-125">Viene illustrato come usare i file di configurazione per modificare le impostazioni senza dover ricompilare le app .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="4c3c8-126">Compilazione di app con .NET Native</span><span class="sxs-lookup"><span data-stu-id="4c3c8-126">Compiling Apps with .NET Native</span></span>](./net-native/index.md)  
 <span data-ttu-id="4c3c8-127">Descrive come usare la tecnologia di precompilazione di .NET Native per compilare e distribuire app di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-127">Explains how you can use the .NET Native precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="4c3c8-128">.NET Native compila le app scritte in codice gestito (C#) e destinate a .NET Framework in codice nativo.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-128">.NET Native compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="4c3c8-129">Security</span><span class="sxs-lookup"><span data-stu-id="4c3c8-129">Security</span></span>](../standard/security/index.md)  
 <span data-ttu-id="4c3c8-130">Vengono fornite informazioni sulle classi e sui servizi in .NET Framework che semplificano lo sviluppo di app sicure.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="4c3c8-131">Debug, traccia e profilatura</span><span class="sxs-lookup"><span data-stu-id="4c3c8-131">Debugging, Tracing, and Profiling</span></span>](./debug-trace-profile/index.md)  
 <span data-ttu-id="4c3c8-132">Viene illustrato come eseguire test, ottimizzare e profilare le app .NET Framework e l'ambiente dell'app.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="4c3c8-133">Questa sezione include informazioni per amministratori e sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="4c3c8-134">Sviluppo per piattaforme multiple</span><span class="sxs-lookup"><span data-stu-id="4c3c8-134">Developing for Multiple Platforms</span></span>](../standard/cross-platform/index.md)  
 <span data-ttu-id="4c3c8-135">Viene illustrato come usare NET Framework per compilare assembly che possono essere condivisi tra più piattaforme e dispositivi, ad esempio telefoni, computer desktop e dispositivi Web.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="4c3c8-136">Distribuzione</span><span class="sxs-lookup"><span data-stu-id="4c3c8-136">Deployment</span></span>](./deployment/index.md)  
 <span data-ttu-id="4c3c8-137">Viene illustrato come assemblare e distribuire l'app .NET Framework e sono incluse guide di distribuzione sia per sviluppatori che per amministratori.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="4c3c8-138">Prestazioni</span><span class="sxs-lookup"><span data-stu-id="4c3c8-138">Performance</span></span>](./performance/index.md)  
 <span data-ttu-id="4c3c8-139">Vengono fornite informazioni sulla memorizzazione nella cache, l'inizializzazione differita, l'affidabilità e gli eventi ETW.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
 
## <a name="reference"></a><span data-ttu-id="4c3c8-140">Reference</span><span class="sxs-lookup"><span data-stu-id="4c3c8-140">Reference</span></span>  
 [<span data-ttu-id="4c3c8-141">Libreria di classi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c3c8-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="4c3c8-142">Offre sintassi, esempi di codice e informazioni sull'uso per ogni classe contenuta negli spazi dei nomi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-142">Supplies syntax, code examples, and usage information for each class that is contained in the .NET Framework namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c3c8-143">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="4c3c8-143">Related Sections</span></span>  
 [<span data-ttu-id="4c3c8-144">Introduzione</span><span class="sxs-lookup"><span data-stu-id="4c3c8-144">Getting Started</span></span>](./get-started/index.md)  
 <span data-ttu-id="4c3c8-145">Offre una panoramica completa di .NET Framework, oltre ai collegamenti a risorse aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="4c3c8-146">Novità</span><span class="sxs-lookup"><span data-stu-id="4c3c8-146">What's New</span></span>](./whats-new/index.md)  
 <span data-ttu-id="4c3c8-147">Vengono descritte le nuove funzionalità e le modifiche principali incluse nella versione più recente di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="4c3c8-148">Sono inclusi gli elenchi di tipi e membri nuovi e obsoleti e viene fornita una guida per eseguire la migrazione delle app dalla versione precedente di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="4c3c8-149">Strumenti</span><span class="sxs-lookup"><span data-stu-id="4c3c8-149">Tools</span></span>](./tools/index.md)  
 <span data-ttu-id="4c3c8-150">Vengono descritti gli strumenti che consentono di sviluppare, configurare e distribuire app tramite le tecnologie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="4c3c8-151">Esempi ed esercitazioni per .NET</span><span class="sxs-lookup"><span data-stu-id="4c3c8-151">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="4c3c8-152">Collegamenti a esempi ed esercitazioni che favoriscono l'apprendimento di .NET.</span><span class="sxs-lookup"><span data-stu-id="4c3c8-152">Provides links to samples and tutorials that help you learn about .NET.</span></span>
