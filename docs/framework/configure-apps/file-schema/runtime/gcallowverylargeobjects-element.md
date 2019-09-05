---
title: <gcAllowVeryLargeObjects> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f638a880aaa21bc41d2575f3609dabae158c1a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252576"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="9895f-102">\<Elemento > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="9895f-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="9895f-103">Nelle piattaforme a 64 bit, abilita le matrici con dimensione totale maggiore di 2 gigabyte (GB).</span><span class="sxs-lookup"><span data-stu-id="9895f-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="9895f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9895f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9895f-105">&nbsp;&nbsp;[ **\<> di runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="9895f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9895f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects>**</span><span class="sxs-lookup"><span data-stu-id="9895f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9895f-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9895f-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9895f-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="9895f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9895f-109">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="9895f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9895f-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="9895f-110">Attributes</span></span>  
  
|<span data-ttu-id="9895f-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="9895f-111">Attribute</span></span>|<span data-ttu-id="9895f-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9895f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9895f-113">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="9895f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9895f-114">Specifica se le matrici con dimensione totale più grande di 2 GB sono abilitate nelle piattaforme a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="9895f-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9895f-115">Attributo enabled</span><span class="sxs-lookup"><span data-stu-id="9895f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9895f-116">Valore</span><span class="sxs-lookup"><span data-stu-id="9895f-116">Value</span></span>|<span data-ttu-id="9895f-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9895f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9895f-118">Le matrici con dimensione totale più grande di 2 GB non sono abilitate.</span><span class="sxs-lookup"><span data-stu-id="9895f-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="9895f-119">Questa è l'impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="9895f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9895f-120">Le matrici con dimensione totale più grande di 2 GB sono abilitate nelle piattaforme a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="9895f-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9895f-121">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="9895f-121">Child Elements</span></span>  
 <span data-ttu-id="9895f-122">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="9895f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9895f-123">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="9895f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9895f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9895f-124">Element</span></span>|<span data-ttu-id="9895f-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9895f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9895f-126">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9895f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9895f-127">Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9895f-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9895f-128">Note</span><span class="sxs-lookup"><span data-stu-id="9895f-128">Remarks</span></span>  
 <span data-ttu-id="9895f-129">L'utilizzo di questo elemento nel file di configurazione dell'applicazione abilita le matrici con dimensione maggiori di 2 GB, ma non consente di modificare gli altri limiti relativi alla dimensione dell'oggetto o della matrice:</span><span class="sxs-lookup"><span data-stu-id="9895f-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="9895f-130">Il numero massimo di elementi in una matrice è <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9895f-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="9895f-131">L'indice massimo in ogni singola dimensione è 2.147.483.591 (0x7FFFFFC7) per le matrici di byte e le matrici di strutture a byte singolo e 2.146.435.071 (0X7FEFFFFF) per gli altri tipi.</span><span class="sxs-lookup"><span data-stu-id="9895f-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="9895f-132">La dimensione massima consentita per le stringhe e altri oggetti diversi da matrici è invariata.</span><span class="sxs-lookup"><span data-stu-id="9895f-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9895f-133">Prima di abilitare questa funzionalità, assicurarsi che nell'applicazione non sia incluso codice di tipo unsafe in cui si presuppone che la dimensione di tutte le matrici sia inferiore a 2 GB.</span><span class="sxs-lookup"><span data-stu-id="9895f-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="9895f-134">Ad esempio, il codice di tipo unsafe in cui le matrici vengono utilizzate come buffer può essere soggetto a sovraccarichi del buffer se viene scritto partendo dal presupposto che le matrici non superino i 2 GB.</span><span class="sxs-lookup"><span data-stu-id="9895f-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9895f-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="9895f-135">Example</span></span>  
 <span data-ttu-id="9895f-136">Nell'esempio riportato di seguito viene illustrato come abilitare questa funzionalità per un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9895f-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="9895f-137">Supportato in</span><span class="sxs-lookup"><span data-stu-id="9895f-137">Supported in</span></span>

<span data-ttu-id="9895f-138">.NET Framework 4,5 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="9895f-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="9895f-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9895f-139">See also</span></span>

- [<span data-ttu-id="9895f-140">Schema delle impostazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="9895f-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9895f-141">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="9895f-141">Configuration File Schema</span></span>](../index.md)
