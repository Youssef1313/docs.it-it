---
title: Metodo ICLRDebugManager::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30159748c1103cbc8efaf8929387052bbe5c3ec7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773132"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="ac72f-102">Metodo ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="ac72f-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="ac72f-103">Ottiene un valore che indica se un debugger è collegato al processo.</span><span class="sxs-lookup"><span data-stu-id="ac72f-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac72f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ac72f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac72f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ac72f-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="ac72f-106">[out] `true` se un debugger è collegato al processo; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="ac72f-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac72f-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ac72f-107">Return Value</span></span>  
  
|<span data-ttu-id="ac72f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac72f-108">HRESULT</span></span>|<span data-ttu-id="ac72f-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ac72f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac72f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac72f-110">S_OK</span></span>|<span data-ttu-id="ac72f-111">`IsDebuggerAttached` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="ac72f-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="ac72f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac72f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac72f-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="ac72f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac72f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac72f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac72f-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="ac72f-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac72f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac72f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac72f-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="ac72f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac72f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac72f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac72f-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="ac72f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac72f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac72f-120">E_FAIL</span></span>|<span data-ttu-id="ac72f-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="ac72f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac72f-122">Dopo che un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="ac72f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac72f-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac72f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac72f-124">Note</span><span class="sxs-lookup"><span data-stu-id="ac72f-124">Remarks</span></span>  
 <span data-ttu-id="ac72f-125">`IsDebuggerAttached` consente all'host di CLR per determinare se un debugger è collegato al processo di query.</span><span class="sxs-lookup"><span data-stu-id="ac72f-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac72f-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ac72f-126">Requirements</span></span>  
 <span data-ttu-id="ac72f-127">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac72f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac72f-128">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac72f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac72f-129">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ac72f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac72f-130">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac72f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac72f-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ac72f-131">See also</span></span>

- [<span data-ttu-id="ac72f-132">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="ac72f-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ac72f-133">Interfaccia ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="ac72f-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="ac72f-134">Interfaccia IHostControl</span><span class="sxs-lookup"><span data-stu-id="ac72f-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
