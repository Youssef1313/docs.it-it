---
title: URI di tipo pack in WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: ad928fb223ce22c65bb86a78c7d4cd006651a2d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950762"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="af100-102">URI di tipo pack in WPF</span><span class="sxs-lookup"><span data-stu-id="af100-102">Pack URIs in WPF</span></span>

<span data-ttu-id="af100-103">In Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] vengono usati per identificare e caricare i file in molti modi, inclusi i seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="af100-104">Che specifica [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] l'oggetto da visualizzare all'avvio iniziale di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="af100-105">Caricando immagini.</span><span class="sxs-lookup"><span data-stu-id="af100-105">Loading images.</span></span>

- <span data-ttu-id="af100-106">Spostandosi sulle pagine.</span><span class="sxs-lookup"><span data-stu-id="af100-106">Navigating to pages.</span></span>

- <span data-ttu-id="af100-107">Caricando file di dati non eseguibili.</span><span class="sxs-lookup"><span data-stu-id="af100-107">Loading non-executable data files.</span></span>

<span data-ttu-id="af100-108">Inoltre, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] può essere utilizzato per identificare e caricare i file da diverse posizioni, tra cui:</span><span class="sxs-lookup"><span data-stu-id="af100-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="af100-109">L'assembly corrente.</span><span class="sxs-lookup"><span data-stu-id="af100-109">The current assembly.</span></span>

- <span data-ttu-id="af100-110">Un assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-110">A referenced assembly.</span></span>

- <span data-ttu-id="af100-111">Un percorso relativo a un assembly.</span><span class="sxs-lookup"><span data-stu-id="af100-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="af100-112">L'applicazione del sito di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-112">The application's site of origin.</span></span>

<span data-ttu-id="af100-113">Per fornire un meccanismo coerente per l'identificazione e il caricamento di questi tipi di file da [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] questi percorsi, sfrutta l'estendibilità dello *schema URI*di tipo pack.</span><span class="sxs-lookup"><span data-stu-id="af100-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="af100-114">In questo argomento viene fornita una panoramica dello schema, viene illustrato come creare [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] un pacchetto per un'ampia gamma di scenari, viene [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] illustrata l'assoluta e la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativa risoluzione, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] prima di illustrare l'utilizzo di Pack da entrambi i markup e codice.</span><span class="sxs-lookup"><span data-stu-id="af100-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="af100-115">Schema URI di tipo pack</span><span class="sxs-lookup"><span data-stu-id="af100-115">The Pack URI Scheme</span></span>

<span data-ttu-id="af100-116">Lo schema [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] di tipo pack viene usato dalla specifica [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC), che descrive un modello per organizzare e identificare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="af100-117">Gli elementi chiave di questo modello sono i pacchetti e le parti, dove un *pacchetto* è un contenitore logico per una o più *parti*logiche.</span><span class="sxs-lookup"><span data-stu-id="af100-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="af100-118">La figura seguente illustra questo concetto.</span><span class="sxs-lookup"><span data-stu-id="af100-118">The following figure illustrates this concept.</span></span>

![Diagramma di package e parti](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="af100-120">Per identificare le parti, la specifica OPC sfrutta l'estendibilità di RFC 2396 (Uniform Resource Identifier (URI): Sintassi generica) per definire lo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schema di pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af100-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="af100-121">Lo schema specificato da un oggetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] viene definito dal relativo prefisso. http, FTP e file sono esempi noti.</span><span class="sxs-lookup"><span data-stu-id="af100-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="af100-122">Lo schema [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] di pacchetto utilizza "Pack" come schema e contiene due componenti: Authority e Path.</span><span class="sxs-lookup"><span data-stu-id="af100-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="af100-123">Di seguito è riportato il formato di un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af100-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="af100-124">*percorso* dell'*autorità*/Pack://</span><span class="sxs-lookup"><span data-stu-id="af100-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="af100-125">L' *autorità* specifica il tipo di pacchetto in cui è contenuta una parte, mentre il *percorso* specifica la posizione di una parte all'interno di un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af100-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="af100-126">Questo concetto è illustrato nella figura seguente:</span><span class="sxs-lookup"><span data-stu-id="af100-126">This concept is illustrated by the following figure:</span></span>

![Relazione tra package, autorità e percorso](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="af100-128">Pacchetti e parti sono analoghi ad applicazioni e file, dove un'applicazione (pacchetto) può includere uno o più file (parti), tra cui:</span><span class="sxs-lookup"><span data-stu-id="af100-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="af100-129">File di risorse compilati nell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="af100-130">File di risorse compilati in un assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="af100-131">File di risorse compilati in un assembly contenente un riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="af100-132">File di contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-132">Content files.</span></span>

- <span data-ttu-id="af100-133">File del sito di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-133">Site of origin files.</span></span>

<span data-ttu-id="af100-134">Per accedere a questi tipi di file [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , supporta due autorità: Application:///e siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="af100-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="af100-135">L'autorità application:/// identifica i file di dati dell'applicazione noti al momento della compilazione, inclusi file di risorse e di contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="af100-136">L'autorità siteoforigin:/// identifica i file del sito di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="af100-137">La figura seguente illustra l'ambito di ciascuna autorità.</span><span class="sxs-lookup"><span data-stu-id="af100-137">The scope of each authority is shown in the following figure.</span></span>

![Diagramma dell'URI di tipo pack](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="af100-139">Il componente Authority di un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] è un incorporato [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che punta a un pacchetto e deve essere conforme allo standard RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="af100-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="af100-140">Inoltre, il carattere "/" deve essere sostituito con il carattere "," e i caratteri riservati quali "%" e "?" devono essere preceduti da un carattere di escape.</span><span class="sxs-lookup"><span data-stu-id="af100-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="af100-141">Per informazioni dettagliate, vedere la specifica OPC.</span><span class="sxs-lookup"><span data-stu-id="af100-141">See the OPC for details.</span></span>

<span data-ttu-id="af100-142">Le sezioni seguenti illustrano come creare un [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetto usando queste due autorità insieme ai percorsi appropriati per identificare i file di risorse, di contenuto e del sito di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="af100-143">URI di tipo pack di file di risorse</span><span class="sxs-lookup"><span data-stu-id="af100-143">Resource File Pack URIs</span></span>

<span data-ttu-id="af100-144">I file di risorse sono configurati come elementi MSBuild `Resource` e vengono compilati in assembly.</span><span class="sxs-lookup"><span data-stu-id="af100-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="af100-145">WPF supporta la costruzione di URI di tipo pack che possono essere utilizzati per identificare i file di risorse compilati nell'assembly locale o compilati in un assembly a cui viene fatto riferimento dall'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="af100-146">File di risorse dell'assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-146">Local Assembly Resource File</span></span>

<span data-ttu-id="af100-147">Il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] per un file di risorse compilato nell'assembly locale usa l'autorità e il percorso seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="af100-148">**Autorità**: application:///.</span><span class="sxs-lookup"><span data-stu-id="af100-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="af100-149">**Percorso**: Nome del file di risorse, incluso il relativo percorso, relativo alla radice della cartella del progetto dell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="af100-150">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di risorse che si trova nella radice della cartella del progetto dell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="af100-151">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di risorse che si trova in una sottocartella della cartella del progetto dell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="af100-152">File di risorse dell'assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="af100-153">Il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] per un file di risorse compilato in un assembly a cui si fa riferimento usa l'autorità e il percorso seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="af100-154">**Autorità**: application:///.</span><span class="sxs-lookup"><span data-stu-id="af100-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="af100-155">**Percorso**: Nome di un file di risorse compilato in un assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="af100-156">Il percorso deve essere conforme al formato seguente:</span><span class="sxs-lookup"><span data-stu-id="af100-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="af100-157">*NomeBreveAssembly* { *; Versione*] { *; PublicKey*]; componente/*percorso*</span><span class="sxs-lookup"><span data-stu-id="af100-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="af100-158">**NomeBreveAssembly**: nome breve dell'assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="af100-159">**;Versione** [facoltativo]: versione dell'assembly a cui si fa riferimento che contiene il file di risorse.</span><span class="sxs-lookup"><span data-stu-id="af100-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="af100-160">Viene usato quando vengono caricati due o più assembly a cui si fa riferimento con lo stesso nome breve.</span><span class="sxs-lookup"><span data-stu-id="af100-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="af100-161">**;ChiavePubblica** [facoltativo]: chiave pubblica usata per firmare l'assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="af100-162">Viene usato quando vengono caricati due o più assembly a cui si fa riferimento con lo stesso nome breve.</span><span class="sxs-lookup"><span data-stu-id="af100-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="af100-163">**;component**: specifica che il riferimento all'assembly avviene dall'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="af100-164">**/Percorso**: nome del file di risorse, contenente il percorso relativo alla radice della cartella del progetto dell'assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="af100-165">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di risorse che si trova nella radice della cartella del progetto dell'assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="af100-166">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di risorse che si trova in una sottocartella della cartella del progetto dell'assembly a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="af100-167">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di risorse che si trova nella cartella radice di una cartella di progetto di un assembly specifico della versione a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="af100-168">Si noti che la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sintassi Pack per i file di risorse dell'assembly a cui si fa riferimento può essere usata solo con l'autorità Application:///.</span><span class="sxs-lookup"><span data-stu-id="af100-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="af100-169">Il codice seguente, ad esempio, non è [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]supportato in.</span><span class="sxs-lookup"><span data-stu-id="af100-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="af100-170">URI di tipo pack di file di contenuto</span><span class="sxs-lookup"><span data-stu-id="af100-170">Content File Pack URIs</span></span>

<span data-ttu-id="af100-171">Il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] per un file di contenuto usa l'autorità e il percorso seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="af100-172">**Autorità**: application:///.</span><span class="sxs-lookup"><span data-stu-id="af100-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="af100-173">**Percorso**: Nome del file di contenuto, incluso il percorso relativo alla posizione file system dell'assembly eseguibile principale dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="af100-174">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di contenuto che si trova nella stessa cartella dell'assembly eseguibile.</span><span class="sxs-lookup"><span data-stu-id="af100-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="af100-175">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file di contenuto, situato in una sottocartella relativa all'assembly eseguibile dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="af100-176">Non è possibile passare a file di contenuto HTML.</span><span class="sxs-lookup"><span data-stu-id="af100-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="af100-177">Lo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schema supporta solo la navigazione a file HTML che si trovano nel sito di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="af100-178">URI di tipo pack del sito di origine</span><span class="sxs-lookup"><span data-stu-id="af100-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="af100-179">Il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] per un file del sito di origine usa l'autorità e il percorso seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="af100-180">**Autorità**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="af100-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="af100-181">**Percorso**: Nome del file del sito di origine, incluso il percorso relativo alla posizione da cui è stato avviato l'assembly eseguibile.</span><span class="sxs-lookup"><span data-stu-id="af100-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="af100-182">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file del sito di origine, archiviato nella posizione da cui viene avviato l'assembly eseguibile.</span><span class="sxs-lookup"><span data-stu-id="af100-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="af100-183">Nell'esempio seguente viene illustrato l' [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oggetto Pack [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per un file del sito di origine, archiviato nella sottocartella relativa al percorso da cui viene avviato l'assembly eseguibile dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="af100-184">File di paging</span><span class="sxs-lookup"><span data-stu-id="af100-184">Page Files</span></span>

<span data-ttu-id="af100-185">I file XAML configurati come `Page` elementi MSBuild vengono compilati in assembly nello stesso modo dei file di risorse.</span><span class="sxs-lookup"><span data-stu-id="af100-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="af100-186">Di conseguenza, `Page` gli elementi MSBuild possono essere identificati usando URI di pacchetto per i file di risorse.</span><span class="sxs-lookup"><span data-stu-id="af100-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="af100-187">I tipi di [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file comunemente configurati come elementi`Page` MSBuild hanno uno dei seguenti elementi come elemento radice:</span><span class="sxs-lookup"><span data-stu-id="af100-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="af100-188">URI di tipo pack assoluti e relativi</span><span class="sxs-lookup"><span data-stu-id="af100-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="af100-189">Un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] completo include lo schema, l'autorità e il percorso ed è considerato un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]assoluto.</span><span class="sxs-lookup"><span data-stu-id="af100-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="af100-190">Per semplificare gli sviluppatori, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gli elementi consentono in genere di impostare attributi appropriati con un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]relativo, che include solo il percorso.</span><span class="sxs-lookup"><span data-stu-id="af100-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="af100-191">Si consideri, ad esempio, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] il pacchetto assoluto seguente per un file di risorse nell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="af100-192">Il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativo che fa riferimento a questo file di risorse è il seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="af100-193">Poiché i file del sito di origine non sono associati ad assembly, è possibile farvi riferimento solo con il [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]pacchetto Absolute.</span><span class="sxs-lookup"><span data-stu-id="af100-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="af100-194">Per impostazione predefinita, un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativo viene considerato relativo alla posizione del markup o del codice che contiene il riferimento.</span><span class="sxs-lookup"><span data-stu-id="af100-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="af100-195">Se viene utilizzata una barra rovesciata principale, tuttavia, il [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] riferimento di pacchetto relativo viene considerato relativo alla radice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="af100-196">Si consideri ad esempio la struttura di progetto seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="af100-197">Se Pagina1. XAML contiene un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che fa riferimento alla *radice*\SubFolder\Page2.XAML, il riferimento può usare il seguente [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pacchetto relativo.</span><span class="sxs-lookup"><span data-stu-id="af100-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="af100-198">Se Pagina1. XAML contiene un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che fa riferimento alla *radice*\Page2.XAML, il riferimento può usare il seguente [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pacchetto relativo.</span><span class="sxs-lookup"><span data-stu-id="af100-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="af100-199">Risoluzione degli URI di tipo pack</span><span class="sxs-lookup"><span data-stu-id="af100-199">Pack URI Resolution</span></span>

<span data-ttu-id="af100-200">Il formato di Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] consente a Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] per i diversi tipi di file di essere identici.</span><span class="sxs-lookup"><span data-stu-id="af100-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="af100-201">Si consideri, ad esempio, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]il pacchetto assoluto seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="af100-202">Questo pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] assoluto può fare riferimento a un file di risorse nell'assembly locale o in un file di contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="af100-203">Lo stesso vale per l'oggetto relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="af100-204">Per determinare il tipo di file a cui fa riferimento un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacchetto, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] risolve [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i file di risorse in assembly locali e file di contenuto usando l'euristica seguente:</span><span class="sxs-lookup"><span data-stu-id="af100-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="af100-205">Esegue il probe dei metadati <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> dell'assembly per un attributo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]che corrisponde al pacchetto.</span><span class="sxs-lookup"><span data-stu-id="af100-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="af100-206">Se l' <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attributo viene trovato, il percorso del pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fa riferimento a un file di contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="af100-207">Se l' <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attributo non viene trovato, verificare i file di risorse set compilati nell'assembly locale.</span><span class="sxs-lookup"><span data-stu-id="af100-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="af100-208">Se viene trovato un file di risorse che corrisponde al percorso [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] del pacchetto, il percorso del pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fa riferimento a un file di risorse.</span><span class="sxs-lookup"><span data-stu-id="af100-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="af100-209">Se la risorsa non viene trovata, l'oggetto creato <xref:System.Uri> internamente non è valido.</span><span class="sxs-lookup"><span data-stu-id="af100-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="af100-210">la risoluzione non si applica [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a che fanno riferimento agli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="af100-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="af100-211">File di contenuto in assembly a cui si fa riferimento: questi tipi di [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]file non sono supportati da.</span><span class="sxs-lookup"><span data-stu-id="af100-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="af100-212">File incorporati negli assembly a cui [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] si fa riferimento: che li identificano sono univoci perché includono sia il nome dell'assembly `;component` a cui si fa riferimento sia il suffisso.</span><span class="sxs-lookup"><span data-stu-id="af100-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="af100-213">File del sito di origine [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : che li identificano sono univoci perché sono gli unici file che possono essere identificati da Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] che contengono l'autorità siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="af100-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="af100-214">Una semplificazione consentita dalla risoluzione di Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] è che il codice sia indipendente dalle posizioni dei file di risorse e di contenuto.</span><span class="sxs-lookup"><span data-stu-id="af100-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="af100-215">Se, ad esempio, si dispone di un file di risorse nell'assembly locale riconfigurato come file di contenuto, il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] per la risorsa rimane invariato, così come il codice che utilizza il pacchetto. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af100-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="af100-216">Programmazione con URI di tipo pack</span><span class="sxs-lookup"><span data-stu-id="af100-216">Programming with Pack URIs</span></span>

<span data-ttu-id="af100-217">Molte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classi implementano proprietà che possono essere impostate con [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]Pack, tra cui:</span><span class="sxs-lookup"><span data-stu-id="af100-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="af100-218">Queste proprietà possono essere impostate da markup e codice.</span><span class="sxs-lookup"><span data-stu-id="af100-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="af100-219">Questa sezione illustra le costruzioni di base per entrambi e quindi riporta esempi di scenari comuni.</span><span class="sxs-lookup"><span data-stu-id="af100-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="af100-220">Uso di URI di tipo pack nel markup</span><span class="sxs-lookup"><span data-stu-id="af100-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="af100-221">Un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] viene specificato nel markup impostando l'elemento di un attributo con il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af100-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="af100-222">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="af100-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="af100-223">Nella tabella 1 sono illustrati i diversi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetti assoluti che è possibile specificare nel markup.</span><span class="sxs-lookup"><span data-stu-id="af100-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="af100-224">Tabella 1: URI di pacchetto assoluti nel markup</span><span class="sxs-lookup"><span data-stu-id="af100-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="af100-225">File</span><span class="sxs-lookup"><span data-stu-id="af100-225">File</span></span>|<span data-ttu-id="af100-226">Pack assoluto[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af100-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="af100-227">File di risorse - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="af100-228">File di risorse in una sottocartella - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="af100-229">File di risorse - assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="af100-230">File di risorse in una sottocartella dell'assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="af100-231">File di risorse in un assembly a cui si fa riferimento con versione</span><span class="sxs-lookup"><span data-stu-id="af100-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="af100-232">File di contenuto</span><span class="sxs-lookup"><span data-stu-id="af100-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="af100-233">File di contenuto in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="af100-234">File del sito di origine</span><span class="sxs-lookup"><span data-stu-id="af100-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="af100-235">File del sito di origine in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="af100-236">Nella tabella 2 sono illustrati i vari [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetti relativi che è possibile specificare nel markup.</span><span class="sxs-lookup"><span data-stu-id="af100-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="af100-237">Tabella 2: URI di pacchetto relativi nel markup</span><span class="sxs-lookup"><span data-stu-id="af100-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="af100-238">File</span><span class="sxs-lookup"><span data-stu-id="af100-238">File</span></span>|<span data-ttu-id="af100-239">Pacchetto relativo[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af100-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="af100-240">File di risorse nell'assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="af100-241">File di risorse in una sottocartella dell'assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="af100-242">File di risorse nell'assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="af100-243">File di risorse in una sottocartella dell'assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="af100-244">File di contenuto</span><span class="sxs-lookup"><span data-stu-id="af100-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="af100-245">File di contenuto in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="af100-246">Uso di URI di tipo pack nel codice</span><span class="sxs-lookup"><span data-stu-id="af100-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="af100-247">Per specificare un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] nel codice, creare un'istanza <xref:System.Uri> della classe e passare il [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacchetto come parametro al costruttore.</span><span class="sxs-lookup"><span data-stu-id="af100-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="af100-248">come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="af100-249">Per impostazione predefinita, <xref:System.Uri> la classe considera [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] il pacchetto come assoluto.</span><span class="sxs-lookup"><span data-stu-id="af100-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="af100-250">Di conseguenza, viene generata un'eccezione quando viene creata un' <xref:System.Uri> istanza della classe con un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]relativo.</span><span class="sxs-lookup"><span data-stu-id="af100-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="af100-251">Fortunatamente, l' <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload <xref:System.Uri> del costruttore della classe accetta un parametro di tipo <xref:System.UriKind> per consentire di specificare se un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] è assoluto o relativo.</span><span class="sxs-lookup"><span data-stu-id="af100-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="af100-252">È necessario specificare solo <xref:System.UriKind.Absolute> o <xref:System.UriKind.Relative> quando si è certi che il pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fornito sia uno o l'altro.</span><span class="sxs-lookup"><span data-stu-id="af100-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="af100-253">Se non si conosce il tipo di pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] usato, ad esempio quando un utente immette un pacchetto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in fase di esecuzione, usare <xref:System.UriKind.RelativeOrAbsolute> invece.</span><span class="sxs-lookup"><span data-stu-id="af100-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="af100-254">Nella tabella 3 vengono illustrati i vari [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetti relativi che è possibile specificare nel codice <xref:System.Uri?displayProperty=nameWithType>tramite.</span><span class="sxs-lookup"><span data-stu-id="af100-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="af100-255">Tabella 3: URI di pacchetto assoluti nel codice</span><span class="sxs-lookup"><span data-stu-id="af100-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="af100-256">File</span><span class="sxs-lookup"><span data-stu-id="af100-256">File</span></span>|<span data-ttu-id="af100-257">Pack assoluto[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af100-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="af100-258">File di risorse - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-259">File di risorse in una sottocartella - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-260">File di risorse - assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-261">File di risorse in una sottocartella dell'assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-262">File di risorse in un assembly a cui si fa riferimento con versione</span><span class="sxs-lookup"><span data-stu-id="af100-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-263">File di contenuto</span><span class="sxs-lookup"><span data-stu-id="af100-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-264">File di contenuto in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-265">File del sito di origine</span><span class="sxs-lookup"><span data-stu-id="af100-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="af100-266">File del sito di origine in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="af100-267">Nella tabella 4 sono illustrati i diversi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetti relativi che è possibile specificare nel <xref:System.Uri?displayProperty=nameWithType>codice utilizzando.</span><span class="sxs-lookup"><span data-stu-id="af100-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="af100-268">Tabella 4: URI di pacchetto relativi nel codice</span><span class="sxs-lookup"><span data-stu-id="af100-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="af100-269">File</span><span class="sxs-lookup"><span data-stu-id="af100-269">File</span></span>|<span data-ttu-id="af100-270">Pacchetto relativo[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af100-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="af100-271">File di risorse - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="af100-272">File di risorse in una sottocartella - assembly locale</span><span class="sxs-lookup"><span data-stu-id="af100-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="af100-273">File di risorse - assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="af100-274">File di risorse in una sottocartella - assembly a cui si fa riferimento</span><span class="sxs-lookup"><span data-stu-id="af100-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="af100-275">File di contenuto</span><span class="sxs-lookup"><span data-stu-id="af100-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="af100-276">File di contenuto in una sottocartella</span><span class="sxs-lookup"><span data-stu-id="af100-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="af100-277">Scenari comuni di URI Pack</span><span class="sxs-lookup"><span data-stu-id="af100-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="af100-278">Nelle sezioni precedenti è stato illustrato come creare un [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacchetto per identificare i file di risorse, contenuti e siti di origine.</span><span class="sxs-lookup"><span data-stu-id="af100-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="af100-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]queste costruzioni vengono usate in diversi modi e nelle sezioni seguenti vengono illustrati alcuni utilizzi comuni.</span><span class="sxs-lookup"><span data-stu-id="af100-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="af100-280">Specifica dell'interfaccia utente da visualizzare all'avvio di un'applicazione</span><span class="sxs-lookup"><span data-stu-id="af100-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="af100-281"><xref:System.Windows.Application.StartupUri%2A>Specifica il primo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] da visualizzare quando viene [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] avviata un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="af100-282">Per le applicazioni autonome [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , può essere una finestra, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="af100-283">Le applicazioni autonome e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] possono inoltre specificare una pagina come interfaccia utente iniziale, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="af100-284">Se l'applicazione è un'applicazione autonoma e viene specificata una pagina <xref:System.Windows.Application.StartupUri%2A>con [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , apre <xref:System.Windows.Navigation.NavigationWindow> per ospitare la pagina.</span><span class="sxs-lookup"><span data-stu-id="af100-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="af100-285">Per [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], la pagina viene visualizzata nel browser host.</span><span class="sxs-lookup"><span data-stu-id="af100-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="af100-286">Spostamento su una pagina</span><span class="sxs-lookup"><span data-stu-id="af100-286">Navigating to a Page</span></span>

<span data-ttu-id="af100-287">L'esempio seguente illustra come spostarsi su una pagina.</span><span class="sxs-lookup"><span data-stu-id="af100-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="af100-288">Per ulteriori informazioni sui vari modi per spostarsi in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vedere [Cenni preliminari sulla navigazione](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="af100-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="af100-289">Specifica dell'icona di una finestra</span><span class="sxs-lookup"><span data-stu-id="af100-289">Specifying a Window Icon</span></span>

<span data-ttu-id="af100-290">L'esempio seguente illustra come usare un URI per specificare l'icona di una finestra.</span><span class="sxs-lookup"><span data-stu-id="af100-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="af100-291">Per altre informazioni, vedere <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="af100-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="af100-292">Caricamento di file di immagine, audio e video</span><span class="sxs-lookup"><span data-stu-id="af100-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="af100-293">consente alle applicazioni di usare un'ampia gamma di tipi di supporti, che possono essere identificati e caricati con [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]il pacchetto, come illustrato negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="af100-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="af100-294">Per ulteriori informazioni sull'utilizzo del contenuto multimediale, vedere [grafica e multimedia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="af100-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="af100-295">Caricamento di un dizionario risorse dal sito di origine</span><span class="sxs-lookup"><span data-stu-id="af100-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="af100-296">È possibile usare<xref:System.Windows.ResourceDictionary>i dizionari risorse () per supportare i temi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="af100-297">Un modo per creare e gestire i temi consiste nel creare più temi come dizionari risorse che si trovano nel sito di origine di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="af100-298">In questo modo è possibile aggiungere e aggiornare i temi senza ricompilare e ridistribuire un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af100-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="af100-299">Questi dizionari risorse possono essere identificati e caricati usando [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]Pack, illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="af100-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="af100-300">Per una panoramica dei temi in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vedere applicazione di [stili e modelli](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="af100-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af100-301">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="af100-301">See also</span></span>

- [<span data-ttu-id="af100-302">File di dati e di risorse dell'applicazione WPF</span><span class="sxs-lookup"><span data-stu-id="af100-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
