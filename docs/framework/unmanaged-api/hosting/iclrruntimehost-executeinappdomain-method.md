---
title: Metodo ICLRRuntimeHost::ExecuteInAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314ffb143e99f9490bcd4a6489f2afed314b7c2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768768"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="04db9-102">Metodo ICLRRuntimeHost::ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="04db9-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="04db9-103">Specifica il <xref:System.AppDomain> in cui eseguire il codice gestito specificato.</span><span class="sxs-lookup"><span data-stu-id="04db9-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04db9-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="04db9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04db9-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="04db9-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="04db9-106">[in] L'ID numerico del <xref:System.AppDomain> in cui eseguire il metodo specificato.</span><span class="sxs-lookup"><span data-stu-id="04db9-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="04db9-107">[in] Un puntatore alla funzione da eseguire all'interno specificato <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="04db9-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="04db9-108">[in] Puntatore alla memoria allocata dal chiamante opaco.</span><span class="sxs-lookup"><span data-stu-id="04db9-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="04db9-109">Questo parametro viene passato da common language runtime (CLR) per il callback di dominio.</span><span class="sxs-lookup"><span data-stu-id="04db9-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="04db9-110">Non è la memoria dell'heap di runtime gestito. sia l'allocazione e la durata della memoria vengono controllate dal chiamante.</span><span class="sxs-lookup"><span data-stu-id="04db9-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04db9-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="04db9-111">Return Value</span></span>  
  
|<span data-ttu-id="04db9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04db9-112">HRESULT</span></span>|<span data-ttu-id="04db9-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="04db9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04db9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="04db9-114">S_OK</span></span>|<span data-ttu-id="04db9-115">`ExecuteInAppDomain` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="04db9-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="04db9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04db9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04db9-117">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="04db9-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04db9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04db9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04db9-119">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="04db9-119">The call timed out.</span></span>|  
|<span data-ttu-id="04db9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04db9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04db9-121">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="04db9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04db9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04db9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04db9-123">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="04db9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04db9-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04db9-124">E_FAIL</span></span>|<span data-ttu-id="04db9-125">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="04db9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04db9-126">Se un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="04db9-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04db9-127">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04db9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04db9-128">Note</span><span class="sxs-lookup"><span data-stu-id="04db9-128">Remarks</span></span>  
 <span data-ttu-id="04db9-129">`ExecuteInAppDomain` consente all'host di esercitare il controllo su cui gestiti <xref:System.AppDomain> il metodo gestito specificato deve essere eseguito nel.</span><span class="sxs-lookup"><span data-stu-id="04db9-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="04db9-130">È possibile ottenere il valore dell'identificatore di un dominio dell'applicazione, che corrisponde al valore della <xref:System.AppDomain.Id%2A> proprietà, chiamando [metodo GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="04db9-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04db9-131">Requisiti</span><span class="sxs-lookup"><span data-stu-id="04db9-131">Requirements</span></span>  
 <span data-ttu-id="04db9-132">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04db9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04db9-133">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04db9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04db9-134">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="04db9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04db9-135">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04db9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04db9-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="04db9-136">See also</span></span>

- [<span data-ttu-id="04db9-137">Interfaccia ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="04db9-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
