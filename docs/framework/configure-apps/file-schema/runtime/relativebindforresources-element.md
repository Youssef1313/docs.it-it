---
title: <relativeBindForResources> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 859e8a12421ea92aa48c54317e052683eb8e83f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663490"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="28a14-102">\<Elemento > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="28a14-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="28a14-103">Ottimizza le ricerche degli assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="28a14-104">\<Configuration >-elemento</span><span class="sxs-lookup"><span data-stu-id="28a14-104">\<configuration> Element</span></span>  
<span data-ttu-id="28a14-105">\<Elemento runtime ></span><span class="sxs-lookup"><span data-stu-id="28a14-105">\<runtime> Element</span></span>  
<span data-ttu-id="28a14-106">\<Elemento > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="28a14-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a14-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="28a14-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28a14-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="28a14-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28a14-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="28a14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28a14-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="28a14-110">Attributes</span></span>  
  
|<span data-ttu-id="28a14-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="28a14-111">Attribute</span></span>|<span data-ttu-id="28a14-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="28a14-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="28a14-113">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="28a14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="28a14-114">Specifica se tramite Common Language Runtime vengono ottimizzate le ricerche degli assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28a14-115">Attributo enabled</span><span class="sxs-lookup"><span data-stu-id="28a14-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="28a14-116">Valore</span><span class="sxs-lookup"><span data-stu-id="28a14-116">Value</span></span>|<span data-ttu-id="28a14-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="28a14-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="28a14-118">Tramite il runtime non vengono ottimizzate le ricerche degli assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="28a14-119">Rappresenta il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="28a14-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="28a14-120">Tramite il runtime vengono ottimizzate le ricerche degli assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28a14-121">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="28a14-121">Child Elements</span></span>  
 <span data-ttu-id="28a14-122">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="28a14-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28a14-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="28a14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="28a14-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="28a14-124">Element</span></span>|<span data-ttu-id="28a14-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="28a14-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28a14-126">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28a14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28a14-127">Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="28a14-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28a14-128">Note</span><span class="sxs-lookup"><span data-stu-id="28a14-128">Remarks</span></span>  
 <span data-ttu-id="28a14-129">In generale, Gestione risorse Probe per le risorse, come documentato nell'argomento Creazione di [pacchetti e distribuzione delle risorse](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="28a14-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="28a14-130">Ciò significa che per la ricerca di una particolare versione localizzata di una risorsa da parte di Gestione risorse l'operazione potrebbe essere eseguita nella Global Assembly Cache, in una cartella di impostazioni cultura specifiche nella codebase dell'applicazione, potrebbe essere eseguita una query su Windows Installer per gli assembly satellite e potrebbe essere generato l'evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="28a14-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="28a14-131">Tramite l'elemento `<relativeBindForResources>` viene ottimizzata la modalità di ricerca degli assembly satellite tramite Gestione Risorse.</span><span class="sxs-lookup"><span data-stu-id="28a14-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="28a14-132">Le prestazioni possono migliorare durante la ricerca delle risorse nei seguenti casi:</span><span class="sxs-lookup"><span data-stu-id="28a14-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="28a14-133">Quando l'assembly satellite viene distribuito nello stesso percorso dell'assembly di codice.</span><span class="sxs-lookup"><span data-stu-id="28a14-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="28a14-134">In altre parole, se l'assembly di codice è installato nella Global Assembly Cache, anche gli assembly satellite devono essere installati in questa posizione.</span><span class="sxs-lookup"><span data-stu-id="28a14-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="28a14-135">Se l'assembly di codice è installato nella codebase dell'applicazione, anche gli assembly satellite devono essere installati in una cartella di impostazioni cultura specifiche nella codebase.</span><span class="sxs-lookup"><span data-stu-id="28a14-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="28a14-136">Quando Windows Installer non viene utilizzato o viene utilizzato solo raramente per installazioni su richiesta di assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="28a14-137">Quando l'evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> non viene gestito dal codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="28a14-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="28a14-138">L'impostazione dell'attributo `enabled` dell'elemento `<relativeBindForResources>` su `true` consente di ottimizzare la ricerca di assembly satellite da parte di Gestione risorse nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="28a14-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="28a14-139">Viene utilizzato il percorso dell'assembly del codice padre per cercare l'assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="28a14-140">Non viene eseguita una query su Windows Installer per gli assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="28a14-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="28a14-141">Non viene generato l'evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="28a14-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a14-142">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="28a14-142">See also</span></span>

- [<span data-ttu-id="28a14-143">Creazione del pacchetto e distribuzione delle risorse</span><span class="sxs-lookup"><span data-stu-id="28a14-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="28a14-144">Schema delle impostazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="28a14-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28a14-145">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="28a14-145">Configuration File Schema</span></span>](../index.md)
