---
title: Metodo IHostMAlloc::Free
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6de6d12322e29ddcc854f6b9aed0a4790af089e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780719"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="e041a-102">Metodo IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="e041a-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="e041a-103">Libera la memoria allocata tramite il [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) (funzione).</span><span class="sxs-lookup"><span data-stu-id="e041a-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e041a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e041a-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e041a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e041a-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="e041a-106">[in] Puntatore alla memoria da liberare.</span><span class="sxs-lookup"><span data-stu-id="e041a-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e041a-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e041a-107">Return Value</span></span>  
  
|<span data-ttu-id="e041a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e041a-108">HRESULT</span></span>|<span data-ttu-id="e041a-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e041a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e041a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e041a-110">S_OK</span></span>|<span data-ttu-id="e041a-111">`Free` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="e041a-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="e041a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e041a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e041a-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="e041a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e041a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e041a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e041a-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="e041a-115">The call timed out.</span></span>|  
|<span data-ttu-id="e041a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e041a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e041a-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="e041a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e041a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e041a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e041a-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="e041a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e041a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e041a-120">E_FAIL</span></span>|<span data-ttu-id="e041a-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="e041a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e041a-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="e041a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e041a-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e041a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e041a-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e041a-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e041a-125">È stato effettuato un tentativo per liberare la memoria non allocata tramite l'host.</span><span class="sxs-lookup"><span data-stu-id="e041a-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e041a-126">Note</span><span class="sxs-lookup"><span data-stu-id="e041a-126">Remarks</span></span>  
 <span data-ttu-id="e041a-127">Se il `pMem` parametro fa riferimento a un'area di memoria che non è stata allocata mediante una chiamata a `Alloc`, l'host deve restituire HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="e041a-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e041a-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e041a-128">Requirements</span></span>  
 <span data-ttu-id="e041a-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e041a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e041a-130">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e041a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e041a-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e041a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e041a-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e041a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e041a-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e041a-133">See also</span></span>

- [<span data-ttu-id="e041a-134">Interfaccia IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e041a-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="e041a-135">Interfaccia IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="e041a-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
