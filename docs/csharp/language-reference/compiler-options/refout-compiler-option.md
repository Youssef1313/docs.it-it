---
title: -refout (opzioni del compilatore C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602512"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="1f5d0-102">-refout (opzioni del compilatore C#)</span><span class="sxs-lookup"><span data-stu-id="1f5d0-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="1f5d0-103">L'opzione **-refout** specifica un percorso file in cui l'assembly di riferimento deve essere restituito come output.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="1f5d0-104">Ciò si converte in `metadataPeStream` nell'API Emit.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="1f5d0-105">Questa opzione corrisponde alla proprietà del progetto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) di MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f5d0-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1f5d0-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="1f5d0-107">Argomenti</span><span class="sxs-lookup"><span data-stu-id="1f5d0-107">Arguments</span></span>

 <span data-ttu-id="1f5d0-108">`filepath` Il percorso del file dell'assembly di riferimento.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="1f5d0-109">In genere corrisponde a quello dell'assembly primario.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="1f5d0-110">La convenzione consigliata (usata da MSBuild) consiste nell'inserire l'assembly di riferimento in una sottocartella "ref /" relativa all'assembly primario.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f5d0-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1f5d0-111">Remarks</span></span>

<span data-ttu-id="1f5d0-112">Per gli assembly di soli metadati i corpi di metodo vengono sostituiti con un singolo corpo `throw null`, ma sono inclusi tutti i membri, tranne i tipi anonimi.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="1f5d0-113">L'utilizzo di corpi `throw null`, a differenza di nessun corpo, è giustificato dal fatto che PEVerify può essere eseguito e avere esito positivo convalidando la completezza dei metadati.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="1f5d0-114">Gli assembly di riferimento includono un attributo `ReferenceAssembly` al livello assembly.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="1f5d0-115">Questo attributo può essere specificato nell'origine, quindi non è necessaria la sintesi da parte del compilatore.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="1f5d0-116">A causa di questo attributo, i runtime non caricheranno gli assembly di riferimento per l'esecuzione, che tuttavia possono essere caricati in modalità sola reflection.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="1f5d0-117">Gli strumenti che eseguono la reflection sugli assembly devono garantire che vengano caricati gli assembly di riferimento come sola reflection; in caso contrario il runtime visualizzerà un errore di caricamento del tipo.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="1f5d0-118">Gli assembly di riferimento rimuovono ulteriormente i metadati (membri privati) dagli assembly di soli metadati:</span><span class="sxs-lookup"><span data-stu-id="1f5d0-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="1f5d0-119">Un assembly di riferimento include solo i riferimenti per i requisiti nella superficie dell'API.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="1f5d0-120">L'assembly reale può includere riferimenti aggiuntivi relativi a implementazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="1f5d0-121">Ad esempio, l'assembly di riferimento per `class C { private void M() { dynamic d = 1; ... } }` non fa riferimento ai tipi necessari per `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="1f5d0-122">I membri-funzione privati (metodi, proprietà ed eventi) vengono rimossi quando la rimozione non impatta in maniera visibile sulla compilazione.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="1f5d0-123">Se non esistono attributi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, eseguire la stessa operazione per i membri-funzione interni.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="1f5d0-124">Negli assembly di riferimento vengono tuttavia mantenuti tutti i tipi, inclusi i tipi privati o nidificati.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="1f5d0-125">Vengono mantenuti tutti gli attributi, persino quelli interni.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="1f5d0-126">Vengono mantenuti tutti i metodi virtuali.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-126">All virtual methods are kept.</span></span> <span data-ttu-id="1f5d0-127">Vengono mantenute le implementazioni esplicite di interfacce.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="1f5d0-128">Vengono mantenuti gli eventi e le proprietà implementati in modo esplicito poiché le relative funzioni di accesso sono virtuali.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="1f5d0-129">Vengono mantenuti tutti i campi di uno struct.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-129">All fields of a struct are kept.</span></span> <span data-ttu-id="1f5d0-130">È un candidato per la rifinitura post-C#-7.1.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="1f5d0-131">Le opzioni `-refout` e [`-refonly`](refonly-compiler-option.md) si escludono reciprocamente.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f5d0-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f5d0-132">See also</span></span>

- [<span data-ttu-id="1f5d0-133">Opzioni del compilatore C#</span><span class="sxs-lookup"><span data-stu-id="1f5d0-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1f5d0-134">Gestione delle proprietà di progetti e soluzioni</span><span class="sxs-lookup"><span data-stu-id="1f5d0-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
