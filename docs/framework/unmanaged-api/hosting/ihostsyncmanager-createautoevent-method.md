---
title: Metodo IHostSyncManager::CreateAutoEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad704ff1e38d59df9e26d34b6dc62c40522aa728
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753464"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="66e4b-102">Metodo IHostSyncManager::CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="66e4b-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="66e4b-103">Crea un oggetto evento auto-reset.</span><span class="sxs-lookup"><span data-stu-id="66e4b-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e4b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="66e4b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e4b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="66e4b-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="66e4b-106">[out] Un puntatore all'indirizzo di un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) istanza implementata dall'host, o null se non è stato possibile creare l'oggetto evento.</span><span class="sxs-lookup"><span data-stu-id="66e4b-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e4b-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="66e4b-107">Return Value</span></span>  
  
|<span data-ttu-id="66e4b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66e4b-108">HRESULT</span></span>|<span data-ttu-id="66e4b-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="66e4b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66e4b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="66e4b-110">S_OK</span></span>|<span data-ttu-id="66e4b-111">`CreateAutoEvent` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="66e4b-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="66e4b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66e4b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66e4b-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="66e4b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66e4b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66e4b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66e4b-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="66e4b-115">The call timed out.</span></span>|  
|<span data-ttu-id="66e4b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66e4b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66e4b-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="66e4b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66e4b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66e4b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66e4b-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="66e4b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66e4b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66e4b-120">E_FAIL</span></span>|<span data-ttu-id="66e4b-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="66e4b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66e4b-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="66e4b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66e4b-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66e4b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="66e4b-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="66e4b-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="66e4b-125">Memoria insufficiente era disponibile per creare l'oggetto evento richiesto.</span><span class="sxs-lookup"><span data-stu-id="66e4b-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e4b-126">Note</span><span class="sxs-lookup"><span data-stu-id="66e4b-126">Remarks</span></span>  
 <span data-ttu-id="66e4b-127">`CreateAutoEvent` Crea un oggetto di auto-evento il cui stato viene automaticamente impostato su non segnalato dopo che il thread in attesa è stato rilasciato.</span><span class="sxs-lookup"><span data-stu-id="66e4b-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="66e4b-128">Questo metodo esegue il mirroring Win32 `CreateEvent` funzione con un valore di `false` specificato per il `bManualReset` parametro</span><span class="sxs-lookup"><span data-stu-id="66e4b-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e4b-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="66e4b-129">Requirements</span></span>  
 <span data-ttu-id="66e4b-130">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e4b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e4b-131">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66e4b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66e4b-132">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="66e4b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66e4b-133">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e4b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e4b-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66e4b-134">See also</span></span>

- [<span data-ttu-id="66e4b-135">Interfaccia ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="66e4b-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="66e4b-136">Interfaccia IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="66e4b-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="66e4b-137">Interfaccia IHostControl</span><span class="sxs-lookup"><span data-stu-id="66e4b-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="66e4b-138">Interfaccia IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="66e4b-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
