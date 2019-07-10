---
title: Metodo IHostMemoryManager::RegisterMemoryNotificationCallback
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48580f5ac71b906c302ee7ce1b98e7d4334f2482
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767730"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="0c081-102">Metodo IHostMemoryManager::RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="0c081-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="0c081-103">Registra un puntatore a una funzione di callback richiamata per ricevere una notifica di common language runtime (CLR) dall'host il carico di memoria corrente nel computer.</span><span class="sxs-lookup"><span data-stu-id="0c081-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c081-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0c081-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c081-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0c081-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="0c081-106">[in] Puntatore a interfaccia a un [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) istanza che viene implementato da CLR.</span><span class="sxs-lookup"><span data-stu-id="0c081-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c081-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0c081-107">Return Value</span></span>  
  
|<span data-ttu-id="0c081-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c081-108">HRESULT</span></span>|<span data-ttu-id="0c081-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0c081-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c081-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c081-110">S_OK</span></span>|<span data-ttu-id="0c081-111">`RegisterMemoryNotificationCallback` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="0c081-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="0c081-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c081-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c081-113">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="0c081-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c081-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c081-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c081-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="0c081-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c081-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c081-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c081-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="0c081-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c081-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c081-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c081-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="0c081-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c081-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c081-120">E_FAIL</span></span>|<span data-ttu-id="0c081-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="0c081-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c081-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="0c081-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c081-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c081-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c081-124">Note</span><span class="sxs-lookup"><span data-stu-id="0c081-124">Remarks</span></span>  
 <span data-ttu-id="0c081-125">Poiché il `ICLRMemoryNotificationCallback` interfaccia definisce un solo metodo ([ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) e poiché `pCallback` è un puntatore a un `ICLRMemoryNotificationCallback` istanza fornita da CLR, il la registrazione è efficace per la funzione di callback se stesso.</span><span class="sxs-lookup"><span data-stu-id="0c081-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="0c081-126">L'host richiama `OnMemoryNotification` per segnalare le condizioni di pressione della memoria, anziché utilizzare Win32 standard `CreateMemoryResourceNotification` (funzione).</span><span class="sxs-lookup"><span data-stu-id="0c081-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="0c081-127">Per altre informazioni, vedere la documentazione della piattaforma Windows.</span><span class="sxs-lookup"><span data-stu-id="0c081-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c081-128">Le chiamate a `OnMemoryNotification` si blocca mai.</span><span class="sxs-lookup"><span data-stu-id="0c081-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="0c081-129">Restituiscono sempre immediatamente.</span><span class="sxs-lookup"><span data-stu-id="0c081-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c081-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0c081-130">Requirements</span></span>  
 <span data-ttu-id="0c081-131">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c081-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c081-132">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c081-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c081-133">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0c081-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c081-134">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c081-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c081-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0c081-135">See also</span></span>

- [<span data-ttu-id="0c081-136">Interfaccia ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="0c081-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="0c081-137">Interfaccia IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="0c081-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
