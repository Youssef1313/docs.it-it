---
title: Metodo IHostControl::SetAppDomainManager
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94deb4eaeeec2400aebf397d391ce4b67c16989e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763891"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="095db-102">Metodo IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="095db-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="095db-103">Notifica all'host che è stato creato un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="095db-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095db-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="095db-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="095db-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="095db-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="095db-106">[in] L'identificatore numerico dell'oggetto selezionato <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="095db-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="095db-107">[in] Un puntatore per il <xref:System.AppDomainManager> oggetto che implementa l'host come `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="095db-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="095db-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="095db-108">Return Value</span></span>  
  
|<span data-ttu-id="095db-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="095db-109">HRESULT</span></span>|<span data-ttu-id="095db-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="095db-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="095db-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="095db-111">S_OK</span></span>|<span data-ttu-id="095db-112">`SetAppDomainManager` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="095db-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="095db-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="095db-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="095db-114">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="095db-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="095db-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="095db-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="095db-116">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="095db-116">The call timed out.</span></span>|  
|<span data-ttu-id="095db-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="095db-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="095db-118">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="095db-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="095db-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="095db-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="095db-120">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="095db-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="095db-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="095db-121">E_FAIL</span></span>|<span data-ttu-id="095db-122">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="095db-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="095db-123">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="095db-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="095db-124">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="095db-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="095db-125">Note</span><span class="sxs-lookup"><span data-stu-id="095db-125">Remarks</span></span>  
 <span data-ttu-id="095db-126">Il <xref:System.AppDomainManager> fornisce un meccanismo per eseguire il bootstrap in codice gestito e per controllare la creazione e configurazione di ciascun host <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="095db-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="095db-127">Il <xref:System.AppDomainManager> viene caricato in ognuno <xref:System.AppDomain> quando che <xref:System.AppDomain> viene creato.</span><span class="sxs-lookup"><span data-stu-id="095db-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="095db-128">Se sceglie, CLR notifica all'host che creato il dominio dell'applicazione impostando il valore della `pUnkAppDomainManager` parametro.</span><span class="sxs-lookup"><span data-stu-id="095db-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="095db-129">Nella sua implementazione del `SetAppDomainManager` metodo, l'host può impostare il nome dell'assembly e il tipo per il gestore del dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="095db-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095db-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="095db-130">Requirements</span></span>  
 <span data-ttu-id="095db-131">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095db-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095db-132">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="095db-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="095db-133">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="095db-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="095db-134">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095db-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095db-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="095db-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="095db-136">Interfaccia IHostControl</span><span class="sxs-lookup"><span data-stu-id="095db-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
