---
title: Metodo ICLRErrorReportingManager::EndCustomDump
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 2acbe72377e4c5b291ab062fcb5faa6503bd7937
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129282"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="5d128-102">Metodo ICLRErrorReportingManager::EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="5d128-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="5d128-103">Rimuove la configurazione del dump dello stack personalizzato specificata in una chiamata precedente al metodo [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5d128-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d128-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5d128-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5d128-105">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5d128-105">Return Value</span></span>  
  
|<span data-ttu-id="5d128-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d128-106">HRESULT</span></span>|<span data-ttu-id="5d128-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5d128-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d128-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d128-108">S_OK</span></span>|<span data-ttu-id="5d128-109">`EndCustomDump` ha restituito un esito positivo.</span><span class="sxs-lookup"><span data-stu-id="5d128-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="5d128-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d128-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d128-111">Il Common Language Runtime (CLR) non è stato caricato in un processo oppure CLR si trova in uno stato in cui non è possibile eseguire codice gestito o elaborare la chiamata correttamente.</span><span class="sxs-lookup"><span data-stu-id="5d128-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d128-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d128-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d128-113">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="5d128-113">The call timed out.</span></span>|  
|<span data-ttu-id="5d128-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d128-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d128-115">Il chiamante non è il proprietario del blocco.</span><span class="sxs-lookup"><span data-stu-id="5d128-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d128-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d128-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d128-117">Un evento è stato annullato mentre un thread bloccato o Fiber era in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="5d128-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d128-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d128-118">E_FAIL</span></span>|<span data-ttu-id="5d128-119">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="5d128-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d128-120">Dopo che un metodo restituisce E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="5d128-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d128-121">Le chiamate successive ai metodi di hosting restituiscono HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5d128-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d128-122">Note</span><span class="sxs-lookup"><span data-stu-id="5d128-122">Remarks</span></span>  
 <span data-ttu-id="5d128-123">Il metodo `EndCustomDump` Cancella la configurazione del dump dello stack personalizzato impostata da una chiamata precedente al metodo `BeginCustomDump` e libera qualsiasi stato associato.</span><span class="sxs-lookup"><span data-stu-id="5d128-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="5d128-124">Deve essere chiamato dopo il completamento del dump dello stack personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5d128-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d128-125">La mancata chiamata di `EndCustomDump` causa la perdita della memoria.</span><span class="sxs-lookup"><span data-stu-id="5d128-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d128-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5d128-126">Requirements</span></span>  
 <span data-ttu-id="5d128-127">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d128-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d128-128">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d128-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d128-129">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d128-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d128-130">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d128-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d128-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5d128-131">See also</span></span>

- [<span data-ttu-id="5d128-132">Struttura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="5d128-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="5d128-133">Enumerazione ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="5d128-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="5d128-134">Interfaccia ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="5d128-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
