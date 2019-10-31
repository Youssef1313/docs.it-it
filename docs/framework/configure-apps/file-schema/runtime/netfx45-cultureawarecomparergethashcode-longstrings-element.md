---
title: Elemento <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 193f9a15768e4060d977063117c07558bbb1d766
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116135"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="9c715-102">\<elemento > NetFx45_CultureAwareComparerGetHashCode_LongStrings</span><span class="sxs-lookup"><span data-stu-id="9c715-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="9c715-103">Specifica se il runtime utilizza una quantità di memoria fissa per calcolare i codici hash per il metodo <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9c715-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9c715-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c715-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c715-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="9c715-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9c715-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**</span><span class="sxs-lookup"><span data-stu-id="9c715-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="9c715-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9c715-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c715-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9c715-108">Attributes and Elements</span></span>

<span data-ttu-id="9c715-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="9c715-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c715-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="9c715-110">Attributes</span></span>

|<span data-ttu-id="9c715-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="9c715-111">Attribute</span></span>|<span data-ttu-id="9c715-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9c715-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9c715-113">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="9c715-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9c715-114">Specifica se tramite Common Language Runtime viene allocata una quantità di memoria fissa durante il calcolo dei codici hash.</span><span class="sxs-lookup"><span data-stu-id="9c715-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="9c715-115">Attributo enabled</span><span class="sxs-lookup"><span data-stu-id="9c715-115">enabled Attribute</span></span>

|<span data-ttu-id="9c715-116">Value</span><span class="sxs-lookup"><span data-stu-id="9c715-116">Value</span></span>|<span data-ttu-id="9c715-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9c715-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="9c715-118">0</span><span class="sxs-lookup"><span data-stu-id="9c715-118">0</span></span>|<span data-ttu-id="9c715-119">Specifica se tramite Common Language Runtime viene allocata una quantità di memoria variabile al metodo <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> per il calcolo dei codici hash.</span><span class="sxs-lookup"><span data-stu-id="9c715-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="9c715-120">Questa è l'impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="9c715-120">This is the default.</span></span>|
|<span data-ttu-id="9c715-121">1</span><span class="sxs-lookup"><span data-stu-id="9c715-121">1</span></span>|<span data-ttu-id="9c715-122">Specifica se tramite Common Language Runtime viene allocata una quantità di memoria fissa al metodo <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> per il calcolo dei codici hash.</span><span class="sxs-lookup"><span data-stu-id="9c715-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9c715-123">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9c715-123">Child Elements</span></span>

<span data-ttu-id="9c715-124">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="9c715-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c715-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9c715-125">Parent Elements</span></span>

|<span data-ttu-id="9c715-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c715-126">Element</span></span>|<span data-ttu-id="9c715-127">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9c715-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9c715-128">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c715-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9c715-129">Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9c715-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c715-130">Note</span><span class="sxs-lookup"><span data-stu-id="9c715-130">Remarks</span></span>

<span data-ttu-id="9c715-131">Per impostazione predefinita, tramite Common Language Runtime viene allocata una quantità di memoria variabile per il metodo <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> e <xref:System.ArgumentException> può essere generata quando il metodo tenta di calcolare il codice hash di stringhe di dimensioni considerevoli (oltre diversi milioni di caratteri).</span><span class="sxs-lookup"><span data-stu-id="9c715-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="9c715-132">Aggiungendo questo elemento a un file di configurazione dell'applicazione e impostando il relativo attributo `enabled` su "1", è possibile specificare che il metodo <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> utilizza un algoritmo alternativo che alloca una quantità di memoria fissa per il calcolo di codici hash.</span><span class="sxs-lookup"><span data-stu-id="9c715-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c715-133">L'elemento di `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` non viene utilizzato in [!INCLUDE[win8](../../../../../includes/win8-md.md)] e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="9c715-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c715-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c715-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9c715-135">Schema delle impostazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="9c715-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9c715-136">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="9c715-136">Configuration File Schema</span></span>](../index.md)
