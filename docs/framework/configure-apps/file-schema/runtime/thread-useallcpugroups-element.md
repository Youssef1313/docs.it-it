---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115403"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="59c5d-102">\<elemento > Thread_UseAllCpuGroups</span><span class="sxs-lookup"><span data-stu-id="59c5d-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="59c5d-103">Specifica se il runtime distribuisce i thread gestiti tra tutti i gruppi di CPU.</span><span class="sxs-lookup"><span data-stu-id="59c5d-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="59c5d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59c5d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="59c5d-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="59c5d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="59c5d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="59c5d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="59c5d-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="59c5d-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59c5d-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="59c5d-108">Attributes and Elements</span></span>

<span data-ttu-id="59c5d-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="59c5d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="59c5d-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="59c5d-110">Attributes</span></span>

|<span data-ttu-id="59c5d-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="59c5d-111">Attribute</span></span>|<span data-ttu-id="59c5d-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="59c5d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="59c5d-113">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="59c5d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="59c5d-114">Specifica se il runtime distribuisce i thread gestiti tra tutti i gruppi di CPU.</span><span class="sxs-lookup"><span data-stu-id="59c5d-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="59c5d-115">Attributo enabled</span><span class="sxs-lookup"><span data-stu-id="59c5d-115">enabled Attribute</span></span>

|<span data-ttu-id="59c5d-116">Value</span><span class="sxs-lookup"><span data-stu-id="59c5d-116">Value</span></span>|<span data-ttu-id="59c5d-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="59c5d-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="59c5d-118">Il runtime non distribuisce i thread gestiti tra più gruppi di CPU.</span><span class="sxs-lookup"><span data-stu-id="59c5d-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="59c5d-119">Questa è l'impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="59c5d-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="59c5d-120">Il runtime distribuisce i thread gestiti tra più gruppi di CPU, se il computer dispone di più gruppi di CPU e l'elemento [\<> GCCpuGroup](gccpugroup-element.md) è abilitato.</span><span class="sxs-lookup"><span data-stu-id="59c5d-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="59c5d-121">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="59c5d-121">Child Elements</span></span>

<span data-ttu-id="59c5d-122">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="59c5d-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59c5d-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="59c5d-123">Parent Elements</span></span>

|<span data-ttu-id="59c5d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="59c5d-124">Element</span></span>|<span data-ttu-id="59c5d-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="59c5d-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="59c5d-126">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59c5d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="59c5d-127">Contiene informazioni sull'associazione degli assembly e sull'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="59c5d-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59c5d-128">Note</span><span class="sxs-lookup"><span data-stu-id="59c5d-128">Remarks</span></span>

<span data-ttu-id="59c5d-129">Quando un computer dispone di più gruppi di CPU, l'abilitazione di questo elemento fa sì che il runtime distribuisca i thread gestiti in tutti i gruppi di CPU.</span><span class="sxs-lookup"><span data-stu-id="59c5d-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="59c5d-130">Per usare questa funzionalità, è necessario abilitare anche l'elemento [\<> GCCpuGroup](gccpugroup-element.md) , che estende Garbage Collection a tutti i gruppi di CPU e prende in considerazione tutti i core quando crea e bilancia gli heap.</span><span class="sxs-lookup"><span data-stu-id="59c5d-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="59c5d-131">Per abilitare l'elemento [\<GCCpuGroup >](gccpugroup-element.md) è necessario abilitare l'elemento [\<gcServer >](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="59c5d-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="59c5d-132">Se questi elementi non sono abilitati, l'abilitazione dell'elemento `<Thread_UseAllCpuGroups>` non ha alcun effetto.</span><span class="sxs-lookup"><span data-stu-id="59c5d-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="59c5d-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="59c5d-133">Example</span></span>

<span data-ttu-id="59c5d-134">Nell'esempio seguente viene illustrato come abilitare il supporto per più gruppi di CPU.</span><span class="sxs-lookup"><span data-stu-id="59c5d-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="59c5d-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="59c5d-135">See also</span></span>

- [<span data-ttu-id="59c5d-136">Schema delle impostazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="59c5d-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="59c5d-137">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="59c5d-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="59c5d-138">\<elemento > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="59c5d-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
