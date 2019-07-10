---
title: Metodo IHostThreadPoolManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a727a5287f6eaad600fc37befc32790fc4cf26
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749304"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="0347b-102">Metodo IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="0347b-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="0347b-103">Ottiene il numero di thread nel pool di thread che non stanno elaborando gli elementi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="0347b-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0347b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0347b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0347b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0347b-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="0347b-106">[out] Puntatore al numero di thread nel pool di thread che non stanno elaborando gli elementi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="0347b-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0347b-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0347b-107">Return Value</span></span>  
  
|<span data-ttu-id="0347b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0347b-108">HRESULT</span></span>|<span data-ttu-id="0347b-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0347b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0347b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0347b-110">S_OK</span></span>|<span data-ttu-id="0347b-111">`GetAvailableThreads` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="0347b-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0347b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0347b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0347b-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="0347b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0347b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0347b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0347b-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="0347b-115">The call timed out.</span></span>|  
|<span data-ttu-id="0347b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0347b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0347b-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="0347b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0347b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0347b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0347b-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="0347b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0347b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0347b-120">E_FAIL</span></span>|<span data-ttu-id="0347b-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="0347b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0347b-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="0347b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0347b-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0347b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0347b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0347b-124">E_NOTIMPL</span></span>|<span data-ttu-id="0347b-125">L'host non fornisce un'implementazione di `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="0347b-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0347b-126">Note</span><span class="sxs-lookup"><span data-stu-id="0347b-126">Remarks</span></span>  
 <span data-ttu-id="0347b-127">Se l'host non fornisce un'implementazione di `GetAvailableThreads`, deve restituire un valore HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="0347b-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0347b-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0347b-128">Requirements</span></span>  
 <span data-ttu-id="0347b-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0347b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0347b-130">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0347b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0347b-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0347b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0347b-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0347b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0347b-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0347b-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="0347b-134">Interfaccia IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="0347b-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
