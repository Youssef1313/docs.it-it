---
title: Struttura COR_GC_THREAD_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f56ceca5269ebffb29908c63e698ce794027d8a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768054"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="4dcf0-102">Struttura COR_GC_THREAD_STATS</span><span class="sxs-lookup"><span data-stu-id="4dcf0-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="4dcf0-103">Contiene le statistiche per ogni thread relative alla garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcf0-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4dcf0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="4dcf0-105">Membri</span><span class="sxs-lookup"><span data-stu-id="4dcf0-105">Members</span></span>  
  
|<span data-ttu-id="4dcf0-106">Member</span><span class="sxs-lookup"><span data-stu-id="4dcf0-106">Member</span></span>|<span data-ttu-id="4dcf0-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4dcf0-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="4dcf0-108">Il numero di byte di memoria allocata nel thread in cui è associato all'oggetto corrente `COR_GC_THREAD_STATS` istanza.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="4dcf0-109">Questo numero viene impostato su zero ogni volta che si verifica una da zero la generazione di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="4dcf0-110">Il numero di byte promossi a una generazione superiore le più recenti di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dcf0-111">Note</span><span class="sxs-lookup"><span data-stu-id="4dcf0-111">Remarks</span></span>  
 <span data-ttu-id="4dcf0-112">[ICLRTask:: GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) accetta un parametro di output di tipo `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcf0-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4dcf0-113">Requirements</span></span>  
 <span data-ttu-id="4dcf0-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dcf0-115">**Intestazione:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="4dcf0-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="4dcf0-116">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4dcf0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dcf0-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dcf0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcf0-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4dcf0-118">See also</span></span>

- [<span data-ttu-id="4dcf0-119">Strutture di hosting</span><span class="sxs-lookup"><span data-stu-id="4dcf0-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="4dcf0-120">Interfaccia IHostTask</span><span class="sxs-lookup"><span data-stu-id="4dcf0-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
