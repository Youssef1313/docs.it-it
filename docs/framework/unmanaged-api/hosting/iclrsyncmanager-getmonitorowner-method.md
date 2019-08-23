---
title: Metodo ICLRSyncManager::GetMonitorOwner
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e08af840d1c4a654fa9b9ff8b2064f5265afaf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943248"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="c9902-102">Metodo ICLRSyncManager::GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="c9902-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="c9902-103">Ottiene l'istanza di [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) a cui appartiene il monitoraggio identificato dal cookie specificato.</span><span class="sxs-lookup"><span data-stu-id="c9902-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9902-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9902-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9902-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="c9902-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="c9902-106">in Cookie associato al monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="c9902-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="c9902-107">out Puntatore all'oggetto `IHostTask` che attualmente possiede il monitoraggio oppure null se nessuna attività ha la proprietà.</span><span class="sxs-lookup"><span data-stu-id="c9902-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9902-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c9902-108">Return Value</span></span>  
  
|<span data-ttu-id="c9902-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9902-109">HRESULT</span></span>|<span data-ttu-id="c9902-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c9902-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9902-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9902-111">S_OK</span></span>|<span data-ttu-id="c9902-112">`GetMonitorOwner`la restituzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="c9902-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="c9902-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9902-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9902-114">CLR non è stato caricato in un processo oppure CLR si trova in uno stato in cui non è possibile eseguire codice gestito o elaborare la chiamata correttamente.</span><span class="sxs-lookup"><span data-stu-id="c9902-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9902-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9902-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9902-116">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="c9902-116">The call timed out.</span></span>|  
|<span data-ttu-id="c9902-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9902-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9902-118">Il chiamante non è il proprietario del blocco.</span><span class="sxs-lookup"><span data-stu-id="c9902-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9902-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9902-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9902-120">Un evento è stato annullato mentre un thread bloccato o Fiber era in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="c9902-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9902-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9902-121">E_FAIL</span></span>|<span data-ttu-id="c9902-122">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="c9902-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9902-123">Quando un metodo restituisce E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="c9902-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9902-124">Le chiamate successive ai metodi di hosting restituiscono HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9902-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9902-125">Note</span><span class="sxs-lookup"><span data-stu-id="c9902-125">Remarks</span></span>  
 <span data-ttu-id="c9902-126">L'host chiama `GetMonitorOwner` in genere come parte di un meccanismo di rilevamento di deadlock.</span><span class="sxs-lookup"><span data-stu-id="c9902-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="c9902-127">Il cookie è associato a un monitoraggio quando viene creato tramite una chiamata a [IHostSyncManager:: CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9902-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9902-128">Una chiamata per rilasciare l'evento sottostante al monitoraggio potrebbe bloccarsi, ma non deadlock, se una chiamata a questo metodo è attualmente attiva sul cookie associato a tale monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="c9902-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="c9902-129">Anche altre attività potrebbero bloccarsi se tentano di acquisire questo monitoraggio.</span><span class="sxs-lookup"><span data-stu-id="c9902-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="c9902-130">`GetMonitorOwner`viene sempre restituito immediatamente e può essere chiamato in qualsiasi momento dopo una `CreateMonitorEvent`chiamata a.</span><span class="sxs-lookup"><span data-stu-id="c9902-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="c9902-131">L'host non deve attendere finché un'attività non è in attesa dell'evento.</span><span class="sxs-lookup"><span data-stu-id="c9902-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9902-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c9902-132">Requirements</span></span>  
 <span data-ttu-id="c9902-133">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9902-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9902-134">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9902-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9902-135">**Libreria** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9902-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9902-136">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9902-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9902-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9902-137">See also</span></span>

- [<span data-ttu-id="c9902-138">Interfaccia ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c9902-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c9902-139">Interfaccia IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c9902-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
