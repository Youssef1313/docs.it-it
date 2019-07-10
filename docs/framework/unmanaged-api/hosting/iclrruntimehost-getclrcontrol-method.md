---
title: Metodo ICLRRuntimeHost::GetCLRControl
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b697e2cf7688767ac58c6bd2a3f18d781ab439b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768750"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="2f892-102">Metodo ICLRRuntimeHost::GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="2f892-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="2f892-103">Ottiene un puntatore a interfaccia typu [interfaccia ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) che gli host possono usare per personalizzare gli aspetti di common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2f892-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f892-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2f892-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f892-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="2f892-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="2f892-106">[out] Un puntatore a interfaccia typu [interfaccia ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) che consente agli host di configurare altri aspetti di CLR.</span><span class="sxs-lookup"><span data-stu-id="2f892-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f892-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2f892-107">Return Value</span></span>  
  
|<span data-ttu-id="2f892-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f892-108">HRESULT</span></span>|<span data-ttu-id="2f892-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2f892-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f892-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f892-110">S_OK</span></span>|<span data-ttu-id="2f892-111">`GetCLRControl` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="2f892-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="2f892-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f892-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f892-113">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="2f892-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f892-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f892-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f892-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="2f892-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f892-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f892-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f892-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="2f892-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f892-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f892-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f892-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="2f892-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f892-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f892-120">E_FAIL</span></span>|<span data-ttu-id="2f892-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="2f892-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f892-122">Se un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="2f892-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f892-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f892-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f892-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2f892-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2f892-125">CLR è già avviata.</span><span class="sxs-lookup"><span data-stu-id="2f892-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f892-126">Note</span><span class="sxs-lookup"><span data-stu-id="2f892-126">Remarks</span></span>  
 <span data-ttu-id="2f892-127">`ICLRControl` fornisce il [metodo GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodo, che consente all'host ottenere un puntatore a interfaccia per uno dei tipi di gestione.</span><span class="sxs-lookup"><span data-stu-id="2f892-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f892-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2f892-128">Requirements</span></span>  
 <span data-ttu-id="2f892-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f892-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f892-130">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f892-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f892-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2f892-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f892-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f892-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f892-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f892-133">See also</span></span>

- [<span data-ttu-id="2f892-134">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="2f892-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2f892-135">Interfaccia ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2f892-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
