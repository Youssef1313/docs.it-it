---
title: Metodo ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356678afb537ab5e5e1653c4f71140ce704e55ef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779678"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="76f1d-102">Metodo ICLRGCManager2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="76f1d-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="76f1d-103">Imposta le dimensioni di un segmento di garbage collection e le dimensioni massime della generazione del sistema di garbage collection 0.</span><span class="sxs-lookup"><span data-stu-id="76f1d-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f1d-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="76f1d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f1d-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="76f1d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="76f1d-106">[in] La dimensione specificata per un segmento di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="76f1d-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="76f1d-107">Le dimensioni del segmento minimo sono 4 MB.</span><span class="sxs-lookup"><span data-stu-id="76f1d-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="76f1d-108">Segmenti possono essere un aumento con incrementi di 1 MB o maggiori.</span><span class="sxs-lookup"><span data-stu-id="76f1d-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="76f1d-109">[in] Le dimensioni massime specificata per la generazione 0.</span><span class="sxs-lookup"><span data-stu-id="76f1d-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="76f1d-110">La dimensione minima per la generazione 0 è 64 KB.</span><span class="sxs-lookup"><span data-stu-id="76f1d-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76f1d-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="76f1d-111">Return Value</span></span>  
  
|<span data-ttu-id="76f1d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76f1d-112">HRESULT</span></span>|<span data-ttu-id="76f1d-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="76f1d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76f1d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="76f1d-114">S_OK</span></span>|<span data-ttu-id="76f1d-115">`SetGCStartupLimitsEx` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="76f1d-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="76f1d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76f1d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76f1d-117">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="76f1d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76f1d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76f1d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76f1d-119">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="76f1d-119">The call timed out.</span></span>|  
|<span data-ttu-id="76f1d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76f1d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76f1d-121">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="76f1d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76f1d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76f1d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76f1d-123">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="76f1d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76f1d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76f1d-124">E_FAIL</span></span>|<span data-ttu-id="76f1d-125">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="76f1d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76f1d-126">Dopo che un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="76f1d-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76f1d-127">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76f1d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f1d-128">Note</span><span class="sxs-lookup"><span data-stu-id="76f1d-128">Remarks</span></span>  
 <span data-ttu-id="76f1d-129">I valori che `SetGCStartupLimitsEx` set possono essere specificati solo prima dell'avvio dell'host.</span><span class="sxs-lookup"><span data-stu-id="76f1d-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="76f1d-130">Le chiamate successive a `SetGCStartupLimitsEx` vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="76f1d-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="76f1d-131">Per impostare dei parametri senza influire su altro, specificare 0 (zero) per il parametro che non si vuole modificare.</span><span class="sxs-lookup"><span data-stu-id="76f1d-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f1d-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="76f1d-132">Requirements</span></span>  
 <span data-ttu-id="76f1d-133">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f1d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f1d-134">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76f1d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76f1d-135">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="76f1d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76f1d-136">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f1d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f1d-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="76f1d-137">See also</span></span>

- [<span data-ttu-id="76f1d-138">Gestione automatica della memoria</span><span class="sxs-lookup"><span data-stu-id="76f1d-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="76f1d-139">Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="76f1d-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="76f1d-140">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="76f1d-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="76f1d-141">Interfaccia ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="76f1d-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
