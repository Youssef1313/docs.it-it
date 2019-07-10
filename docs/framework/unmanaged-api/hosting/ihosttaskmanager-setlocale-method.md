---
title: Metodo IHostTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f388a52c320c3f0d5f4ad7e073e1e8960d7947dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749361"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="3afcc-102">Metodo IHostTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="3afcc-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="3afcc-103">Notifica all'host che common language runtime (CLR) è stato modificato le impostazioni locali o impostazioni cultura, l'attività attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="3afcc-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3afcc-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3afcc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3afcc-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3afcc-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="3afcc-106">[in] Il valore dell'identificatore delle impostazioni locali che esegue il mapping alle nuove impostazioni e alla lingua.</span><span class="sxs-lookup"><span data-stu-id="3afcc-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3afcc-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3afcc-107">Return Value</span></span>  
  
|<span data-ttu-id="3afcc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3afcc-108">HRESULT</span></span>|<span data-ttu-id="3afcc-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3afcc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3afcc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3afcc-110">S_OK</span></span>|<span data-ttu-id="3afcc-111">`SetLocale` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="3afcc-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="3afcc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3afcc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3afcc-113">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="3afcc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3afcc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3afcc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3afcc-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="3afcc-115">The call timed out.</span></span>|  
|<span data-ttu-id="3afcc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3afcc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3afcc-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="3afcc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3afcc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3afcc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3afcc-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="3afcc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3afcc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3afcc-120">E_FAIL</span></span>|<span data-ttu-id="3afcc-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="3afcc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3afcc-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="3afcc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3afcc-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3afcc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3afcc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3afcc-124">E_NOTIMPL</span></span>|<span data-ttu-id="3afcc-125">L'host non supporta codice utente gestito modificare le impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="3afcc-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3afcc-126">Note</span><span class="sxs-lookup"><span data-stu-id="3afcc-126">Remarks</span></span>  
 <span data-ttu-id="3afcc-127">Il runtime chiama `SetLocale` quando il valore della <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> proprietà viene modificata dal codice gestito.</span><span class="sxs-lookup"><span data-stu-id="3afcc-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="3afcc-128">Questo metodo offre un'opportunità per l'host per l'esecuzione di eventuali meccanismi che disponibili per la sincronizzazione delle impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="3afcc-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="3afcc-129">Se un host non supporta le impostazioni locali essere modificato dal codice gestito o non implementa un meccanismo per sincronizzare le impostazioni locali, da questo metodo deve restituire E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3afcc-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3afcc-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3afcc-130">Requirements</span></span>  
 <span data-ttu-id="3afcc-131">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3afcc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3afcc-132">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3afcc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3afcc-133">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3afcc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3afcc-134">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3afcc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afcc-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3afcc-135">See also</span></span>

- [<span data-ttu-id="3afcc-136">Interfaccia ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3afcc-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3afcc-137">Interfaccia ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3afcc-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3afcc-138">Interfaccia IHostTask</span><span class="sxs-lookup"><span data-stu-id="3afcc-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3afcc-139">Interfaccia IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3afcc-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="3afcc-140">Metodo SetUILocale</span><span class="sxs-lookup"><span data-stu-id="3afcc-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
