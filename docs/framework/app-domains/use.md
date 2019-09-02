---
title: Uso dei domini dell'applicazione
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674890"
---
# <a name="using-application-domains"></a><span data-ttu-id="26a5c-102">Uso dei domini dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-102">Using Application Domains</span></span>
<span data-ttu-id="26a5c-103">I domini dell'applicazione offrono un'unità di isolamento per Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="26a5c-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="26a5c-104">Vengono creati ed eseguiti all'interno di un processo.</span><span class="sxs-lookup"><span data-stu-id="26a5c-104">They are created and run inside a process.</span></span> <span data-ttu-id="26a5c-105">I domini dell'applicazione vengono solitamente creati da un host di runtime, che è un'applicazione responsabile del caricamento del runtime in un processo e dell'esecuzione di codice utente all'interno di un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="26a5c-106">L'host di runtime crea un processo e un dominio dell'applicazione predefinito ed esegue codice gestito all'interno di esso.</span><span class="sxs-lookup"><span data-stu-id="26a5c-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="26a5c-107">Gli host di runtime includono ASP.NET, Microsoft Internet Explorer e la shell di Windows.</span><span class="sxs-lookup"><span data-stu-id="26a5c-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="26a5c-108">Per la maggior parte delle applicazioni, non è necessario creare il proprio dominio dell'applicazione. L'host di runtime crea tutti i domini dell'applicazione necessari.</span><span class="sxs-lookup"><span data-stu-id="26a5c-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="26a5c-109">È tuttavia possibile creare e configurare domini dell'applicazione aggiuntivi se l'applicazione necessita di isolare il codice o di usare e scaricare DLL.</span><span class="sxs-lookup"><span data-stu-id="26a5c-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26a5c-110">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="26a5c-110">In This Section</span></span>  
 [<span data-ttu-id="26a5c-111">Procedura: Creare un dominio dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="26a5c-112">Viene descritto come creare a livello di codice un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="26a5c-113">Procedura: Scaricare un dominio dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="26a5c-114">Viene descritto come scaricare a livello di codice un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="26a5c-115">Procedura: Configurare un dominio dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="26a5c-116">Viene presentata un'introduzione alla configurazione di un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="26a5c-117">Recupero di informazioni di installazione da un dominio dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="26a5c-118">Viene descritto come recuperare informazioni di installazione da un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="26a5c-119">Procedura: Caricare assembly in un dominio dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="26a5c-120">Viene descritto come caricare un assembly in un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="26a5c-121">Procedura: Reperire informazioni su tipo e membro da un assembly</span><span class="sxs-lookup"><span data-stu-id="26a5c-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="26a5c-122">Viene descritto come recuperare informazioni su un assembly.</span><span class="sxs-lookup"><span data-stu-id="26a5c-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="26a5c-123">Creazione di copie replicate di assembly</span><span class="sxs-lookup"><span data-stu-id="26a5c-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="26a5c-124">Viene descritto come la copia shadow consente gli aggiornamenti agli assembly mentre sono in uso e come configurare la copia shadow.</span><span class="sxs-lookup"><span data-stu-id="26a5c-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="26a5c-125">Procedura: Ricevere notifiche di eccezioni first-chance</span><span class="sxs-lookup"><span data-stu-id="26a5c-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="26a5c-126">Viene spiegato come è possibile ricevere una notifica della generazione di un'eccezione, prima che Common Language Runtime abbia iniziato la ricerca di gestori di eccezioni.</span><span class="sxs-lookup"><span data-stu-id="26a5c-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="26a5c-127">Risoluzione caricamenti assembly</span><span class="sxs-lookup"><span data-stu-id="26a5c-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="26a5c-128">Vengono offerte indicazioni sull'uso dell'evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> per risolvere gli errori di caricamento di assembly.</span><span class="sxs-lookup"><span data-stu-id="26a5c-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="26a5c-129">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="26a5c-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="26a5c-130">Rappresenta un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-130">Represents an application domain.</span></span> <span data-ttu-id="26a5c-131">Offre metodi per creare e controllare i domini dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="26a5c-132">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="26a5c-132">Related Sections</span></span>  
 [<span data-ttu-id="26a5c-133">Assembly in Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="26a5c-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="26a5c-134">Viene offerta una panoramica delle funzioni svolte dagli assembly.</span><span class="sxs-lookup"><span data-stu-id="26a5c-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="26a5c-135">Programmazione con gli assembly</span><span class="sxs-lookup"><span data-stu-id="26a5c-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="26a5c-136">Descrive come creare, firmare e impostare attributi sugli assembly.</span><span class="sxs-lookup"><span data-stu-id="26a5c-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="26a5c-137">Creazione di assembly e metodi dinamici</span><span class="sxs-lookup"><span data-stu-id="26a5c-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="26a5c-138">Descrive come creare gli assembly dinamici.</span><span class="sxs-lookup"><span data-stu-id="26a5c-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="26a5c-139">Domini dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="26a5c-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="26a5c-140">Viene fornita una panoramica sui concetti di base relativi ai domini applicazione.</span><span class="sxs-lookup"><span data-stu-id="26a5c-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="26a5c-141">Panoramica della reflection</span><span class="sxs-lookup"><span data-stu-id="26a5c-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="26a5c-142">Descrive come usare la classe **Reflection** per ottenere informazioni su un assembly.</span><span class="sxs-lookup"><span data-stu-id="26a5c-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
