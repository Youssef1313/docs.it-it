---
title: Struttura COR_GC_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 630c365c8710388ae3e913bedece0fb710da7cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768132"
---
# <a name="corgcstats-structure"></a><span data-ttu-id="a5743-102">Struttura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="a5743-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="a5743-103">Fornisce statistiche sul meccanismo di garbage collection di common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a5743-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5743-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a5743-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="a5743-105">Membri</span><span class="sxs-lookup"><span data-stu-id="a5743-105">Members</span></span>  
  
|<span data-ttu-id="a5743-106">Member</span><span class="sxs-lookup"><span data-stu-id="a5743-106">Member</span></span>|<span data-ttu-id="a5743-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a5743-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="a5743-108">Indica i valori dei campi devono essere calcolati e restituiti.</span><span class="sxs-lookup"><span data-stu-id="a5743-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="a5743-109">Indica il numero di operazioni di garbage collection che sono stati obbligati da una richiesta esterna.</span><span class="sxs-lookup"><span data-stu-id="a5743-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="a5743-110">Indica il numero di operazioni di garbage collection eseguite per ogni generazione.</span><span class="sxs-lookup"><span data-stu-id="a5743-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="a5743-111">Il numero totale di kilobyte eseguito il commit in tutti gli heap.</span><span class="sxs-lookup"><span data-stu-id="a5743-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="a5743-112">Il numero totale di kilobyte riservato in tutti gli heap.</span><span class="sxs-lookup"><span data-stu-id="a5743-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="a5743-113">Dimensione, espressa in kilobyte, dell'heap di generazione 0.</span><span class="sxs-lookup"><span data-stu-id="a5743-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="a5743-114">Dimensione, espressa in kilobyte, dell'heap di generazione 1.</span><span class="sxs-lookup"><span data-stu-id="a5743-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="a5743-115">Dimensione, espressa in kilobyte, dell'heap di generazione 2.</span><span class="sxs-lookup"><span data-stu-id="a5743-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="a5743-116">Dimensione, espressa in kilobyte, dell'heap oggetti grandi.</span><span class="sxs-lookup"><span data-stu-id="a5743-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="a5743-117">Dimensione, espressa in kilobyte, gli oggetti promossi dalla generazione 0 alla generazione 1.</span><span class="sxs-lookup"><span data-stu-id="a5743-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="a5743-118">Dimensione, espressa in kilobyte, gli oggetti promossi dalla generazione 1 alla generazione 2.</span><span class="sxs-lookup"><span data-stu-id="a5743-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5743-119">Note</span><span class="sxs-lookup"><span data-stu-id="a5743-119">Remarks</span></span>  
 <span data-ttu-id="a5743-120">Il [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metodo richiede il `Flags` campo il `COR_GC_STATS` struttura viene impostata su uno o più valori del [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumerazione per specificare quali le statistiche devono essere impostate.</span><span class="sxs-lookup"><span data-stu-id="a5743-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="a5743-121">Nella tabella seguente viene eseguito il mapping le statistiche fornite da questa struttura per i due [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valori di enumerazione `COR_GC_COUNTS` e `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="a5743-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="a5743-122">Specificato dal COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="a5743-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="a5743-123">Specificato dal COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="a5743-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="a5743-124">Un esempio dell'utilizzo è come segue:</span><span class="sxs-lookup"><span data-stu-id="a5743-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a5743-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a5743-125">Requirements</span></span>  
 <span data-ttu-id="a5743-126">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5743-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5743-127">**Intestazione:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="a5743-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="a5743-128">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a5743-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5743-129">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5743-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5743-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a5743-130">See also</span></span>

- [<span data-ttu-id="a5743-131">Strutture di hosting</span><span class="sxs-lookup"><span data-stu-id="a5743-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="a5743-132">Gestione automatica della memoria</span><span class="sxs-lookup"><span data-stu-id="a5743-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="a5743-133">Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="a5743-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
