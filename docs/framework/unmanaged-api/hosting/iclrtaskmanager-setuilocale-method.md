---
title: Metodo ICLRTaskManager::SetUILocale
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101bcac4ad25a0e1c0a5971aad639b0fb05378b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779963"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="d6a5b-102">Metodo ICLRTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="d6a5b-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="d6a5b-103">Invia una notifica di common language runtime (CLR) che l'host ha modificato le impostazioni locali dell'interfaccia utente o impostazioni cultura, l'attività attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a5b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d6a5b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6a5b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d6a5b-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="d6a5b-106">[in] Il valore dell'identificatore delle impostazioni locali che esegue il mapping per le nuove impostazioni e la lingua dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6a5b-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d6a5b-107">Return Value</span></span>  
  
|<span data-ttu-id="d6a5b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6a5b-108">HRESULT</span></span>|<span data-ttu-id="d6a5b-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d6a5b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6a5b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6a5b-110">S_OK</span></span>|<span data-ttu-id="d6a5b-111">`SetUILocale` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="d6a5b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6a5b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6a5b-113">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6a5b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6a5b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6a5b-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-115">The call timed out.</span></span>|  
|<span data-ttu-id="d6a5b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6a5b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6a5b-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6a5b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6a5b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6a5b-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6a5b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6a5b-120">E_FAIL</span></span>|<span data-ttu-id="d6a5b-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6a5b-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6a5b-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6a5b-124">Note</span><span class="sxs-lookup"><span data-stu-id="d6a5b-124">Remarks</span></span>  
 <span data-ttu-id="d6a5b-125">`SetUILocale` fornisce un'opportunità per l'host per l'esecuzione di eventuali meccanismi che disponibili per la sincronizzazione delle impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="d6a5b-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6a5b-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d6a5b-126">Requirements</span></span>  
 <span data-ttu-id="d6a5b-127">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6a5b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a5b-128">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6a5b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6a5b-129">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d6a5b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6a5b-130">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a5b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a5b-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d6a5b-131">See also</span></span>

- [<span data-ttu-id="d6a5b-132">Interfaccia ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d6a5b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d6a5b-133">Interfaccia ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d6a5b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d6a5b-134">Interfaccia IHostTask</span><span class="sxs-lookup"><span data-stu-id="d6a5b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d6a5b-135">Interfaccia IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d6a5b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
