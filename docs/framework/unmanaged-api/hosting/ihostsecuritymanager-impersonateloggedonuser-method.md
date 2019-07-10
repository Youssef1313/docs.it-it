---
title: Metodo IHostSecurityManager::ImpersonateLoggedOnUser
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c276fc560474ff41afd0e93173d87a76a17a1323
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781001"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="cb597-102">Metodo IHostSecurityManager::ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="cb597-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="cb597-103">Le richieste che codice eseguito con le credenziali dell'identità dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="cb597-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb597-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cb597-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb597-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="cb597-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="cb597-106">[in] Un token che rappresenta le credenziali dell'utente da rappresentare.</span><span class="sxs-lookup"><span data-stu-id="cb597-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb597-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="cb597-107">Return Value</span></span>  
  
|<span data-ttu-id="cb597-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb597-108">HRESULT</span></span>|<span data-ttu-id="cb597-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cb597-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb597-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb597-110">S_OK</span></span>|<span data-ttu-id="cb597-111">`ImpersonateLoggedOnUser` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="cb597-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="cb597-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb597-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb597-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="cb597-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb597-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb597-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb597-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="cb597-115">The call timed out.</span></span>|  
|<span data-ttu-id="cb597-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb597-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb597-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="cb597-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb597-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb597-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb597-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="cb597-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb597-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb597-120">E_FAIL</span></span>|<span data-ttu-id="cb597-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="cb597-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb597-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="cb597-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb597-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb597-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb597-124">Note</span><span class="sxs-lookup"><span data-stu-id="cb597-124">Remarks</span></span>  
 <span data-ttu-id="cb597-125">Chiamare `LogonUser` o una funzione Win32 correlata per ottenere un handle per le credenziali dell'identità dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="cb597-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="cb597-126">Il `HANDLE` tipo non è compatibile con COM, vale a dire, la dimensione è specifica di un sistema operativo e richiede il marshalling personalizzato.</span><span class="sxs-lookup"><span data-stu-id="cb597-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="cb597-127">Di conseguenza, questo token è destinata solo all'interno del processo, tra CLR e l'host.</span><span class="sxs-lookup"><span data-stu-id="cb597-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb597-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cb597-128">Requirements</span></span>  
 <span data-ttu-id="cb597-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb597-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb597-130">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb597-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb597-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cb597-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb597-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb597-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb597-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cb597-133">See also</span></span>

- [<span data-ttu-id="cb597-134">Interfaccia IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="cb597-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="cb597-135">Interfaccia IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="cb597-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="cb597-136">Metodo RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="cb597-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
