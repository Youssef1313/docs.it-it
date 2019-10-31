---
title: Metodo IGCHost::GetThreadStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 36eeb7ed4f80979ef2edb930e65963a1db0c894f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134909"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="2c795-102">Metodo IGCHost::GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="2c795-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="2c795-103">Ottiene le statistiche per thread per Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="2c795-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c795-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2c795-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c795-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="2c795-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="2c795-106">in Puntatore a un cookie Fiber che specifica il thread per il quale recuperare le statistiche.</span><span class="sxs-lookup"><span data-stu-id="2c795-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="2c795-107">[in, out] Puntatore a una struttura [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) che contiene le statistiche Garbage Collection per il thread specificato.</span><span class="sxs-lookup"><span data-stu-id="2c795-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c795-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2c795-108">Requirements</span></span>  
 <span data-ttu-id="2c795-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c795-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c795-110">**Intestazione:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="2c795-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2c795-111">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c795-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c795-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c795-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c795-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2c795-113">See also</span></span>

- [<span data-ttu-id="2c795-114">Interfaccia IGCHost</span><span class="sxs-lookup"><span data-stu-id="2c795-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
