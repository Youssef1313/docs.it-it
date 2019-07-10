---
title: Metodo ICLRTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe45322808a0a756b31f27f9f5c1549ece348e11
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770110"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="112a0-102">Metodo ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="112a0-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="112a0-103">Notifica common language runtime (CLR) che l'host ha modificato il valore dell'identificatore delle impostazioni locali (che esegue il mapping alle impostazioni cultura e alla lingua) per l'attività attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="112a0-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112a0-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="112a0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="112a0-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="112a0-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="112a0-106">[in] Il valore dell'identificatore delle impostazioni locali che esegue il mapping alle nuove impostazioni e alla lingua.</span><span class="sxs-lookup"><span data-stu-id="112a0-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="112a0-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="112a0-107">Return Value</span></span>  
  
|<span data-ttu-id="112a0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="112a0-108">HRESULT</span></span>|<span data-ttu-id="112a0-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="112a0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="112a0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="112a0-110">S_OK</span></span>|<span data-ttu-id="112a0-111">Il metodo è stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="112a0-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="112a0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="112a0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="112a0-113">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="112a0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="112a0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="112a0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="112a0-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="112a0-115">The call timed out.</span></span>|  
|<span data-ttu-id="112a0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="112a0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="112a0-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="112a0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="112a0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="112a0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="112a0-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="112a0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="112a0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="112a0-120">E_FAIL</span></span>|<span data-ttu-id="112a0-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="112a0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="112a0-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="112a0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="112a0-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="112a0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="112a0-124">Note</span><span class="sxs-lookup"><span data-stu-id="112a0-124">Remarks</span></span>  
 <span data-ttu-id="112a0-125">`SetLocale` consente all'host la possibilità di eseguire qualsiasi meccanismi che disponibili per la sincronizzazione delle impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="112a0-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="112a0-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="112a0-126">Requirements</span></span>  
 <span data-ttu-id="112a0-127">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="112a0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="112a0-128">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="112a0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="112a0-129">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="112a0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="112a0-130">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="112a0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112a0-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="112a0-131">See also</span></span>

- [<span data-ttu-id="112a0-132">Interfaccia ICLRTask</span><span class="sxs-lookup"><span data-stu-id="112a0-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="112a0-133">Interfaccia ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="112a0-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="112a0-134">Interfaccia IHostTask</span><span class="sxs-lookup"><span data-stu-id="112a0-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="112a0-135">Interfaccia IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="112a0-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
