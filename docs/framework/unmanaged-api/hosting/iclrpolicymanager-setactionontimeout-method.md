---
title: Metodo ICLRPolicyManager::SetActionOnTimeout
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0f7989765dcec4c405d168d5fa3d082bc30512f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779843"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="4a6df-102">Metodo ICLRPolicyManager::SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="4a6df-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="4a6df-103">Specifica l'azione di criteri che Common language runtime (CLR) deve intraprendere quando scade l'operazione specificata.</span><span class="sxs-lookup"><span data-stu-id="4a6df-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a6df-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4a6df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a6df-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4a6df-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="4a6df-106">[in] Uno dei [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valori, che indica l'operazione per cui si desidera specificare l'azione di timeout.</span><span class="sxs-lookup"><span data-stu-id="4a6df-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="4a6df-107">Sono supportati i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="4a6df-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="4a6df-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4a6df-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="4a6df-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4a6df-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="4a6df-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a6df-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="4a6df-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a6df-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="4a6df-112">[in] Uno dei [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valori, che indica l'azione di criteri da eseguire quando si verifica il timeout dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="4a6df-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a6df-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4a6df-113">Return Value</span></span>  
  
|<span data-ttu-id="4a6df-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a6df-114">HRESULT</span></span>|<span data-ttu-id="4a6df-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4a6df-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a6df-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a6df-116">S_OK</span></span>|<span data-ttu-id="4a6df-117">`SetActionOnTimeout` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="4a6df-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="4a6df-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a6df-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a6df-119">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="4a6df-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a6df-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a6df-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a6df-121">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="4a6df-121">The call timed out.</span></span>|  
|<span data-ttu-id="4a6df-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a6df-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a6df-123">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="4a6df-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a6df-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a6df-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a6df-125">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="4a6df-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a6df-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a6df-126">E_FAIL</span></span>|<span data-ttu-id="4a6df-127">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="4a6df-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a6df-128">Dopo che un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="4a6df-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a6df-129">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a6df-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a6df-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4a6df-130">E_INVALIDARG</span></span>|<span data-ttu-id="4a6df-131">Non è possibile impostare un timeout per l'oggetto specificato `operation`, o è stato specificato un valore non valido per `operation`.</span><span class="sxs-lookup"><span data-stu-id="4a6df-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a6df-132">Note</span><span class="sxs-lookup"><span data-stu-id="4a6df-132">Remarks</span></span>  
 <span data-ttu-id="4a6df-133">Il valore di timeout può essere il timeout predefinito impostato dal Common Language Runtime, o un valore specificato dall'host in una chiamata ai [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="4a6df-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="4a6df-134">Non tutti i valori di azione dei criteri possono essere specificati come il comportamento di timeout per le operazioni CLR.</span><span class="sxs-lookup"><span data-stu-id="4a6df-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="4a6df-135">`SetActionOnTimeout` in genere viene utilizzato solo per l'escalation di comportamento.</span><span class="sxs-lookup"><span data-stu-id="4a6df-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="4a6df-136">Ad esempio, un host può specificare che le interruzioni di thread deve essere trasformata in modo irregolare interruzioni di thread, ma non è possibile specificare l'opposto.</span><span class="sxs-lookup"><span data-stu-id="4a6df-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="4a6df-137">La tabella seguente descrive validi `action` i valori per valido `operation` valori.</span><span class="sxs-lookup"><span data-stu-id="4a6df-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="4a6df-138">Valore per `operation`</span><span class="sxs-lookup"><span data-stu-id="4a6df-138">Value for `operation`</span></span>|<span data-ttu-id="4a6df-139">Valori validi per `action`</span><span class="sxs-lookup"><span data-stu-id="4a6df-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="4a6df-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a6df-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="4a6df-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="4a6df-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="4a6df-142">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="4a6df-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="4a6df-143">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a6df-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4a6df-144">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a6df-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4a6df-145">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-145">-   eExitProcess</span></span><br /><span data-ttu-id="4a6df-146">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a6df-147">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a6df-148">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a6df-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4a6df-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="4a6df-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="4a6df-150">-   eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a6df-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="4a6df-151">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a6df-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="4a6df-152">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-152">-   eExitProcess</span></span><br /><span data-ttu-id="4a6df-153">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a6df-154">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a6df-155">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a6df-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="4a6df-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="4a6df-156">OPR_ProcessExit</span></span>|<span data-ttu-id="4a6df-157">-   eExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-157">-   eExitProcess</span></span><br /><span data-ttu-id="4a6df-158">-   eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="4a6df-159">-   eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="4a6df-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="4a6df-160">-   eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="4a6df-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a6df-161">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4a6df-161">Requirements</span></span>  
 <span data-ttu-id="4a6df-162">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a6df-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a6df-163">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a6df-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a6df-164">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4a6df-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a6df-165">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a6df-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6df-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a6df-166">See also</span></span>

- [<span data-ttu-id="4a6df-167">Enumerazione EClrOperation</span><span class="sxs-lookup"><span data-stu-id="4a6df-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="4a6df-168">Enumerazione EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="4a6df-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="4a6df-169">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="4a6df-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4a6df-170">Interfaccia ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="4a6df-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
