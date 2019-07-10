---
title: Metodo ICLRRuntimeInfo::IsStarted
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b064f0b1cec07f29058300041711285bde66697
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748407"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="c9f65-102">Metodo ICLRRuntimeInfo::IsStarted</span><span class="sxs-lookup"><span data-stu-id="c9f65-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="c9f65-103">Indica se il runtime è stato avviato (vale a dire, se il [ICLRRuntimeHost::](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) è stato chiamato e ha avuto esito positivo).</span><span class="sxs-lookup"><span data-stu-id="c9f65-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f65-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9f65-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9f65-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="c9f65-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="c9f65-106">[out] `true` se questa istanza di runtime è avviato; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="c9f65-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="c9f65-107">[out] Restituisce i flag utilizzati per avviare il runtime.</span><span class="sxs-lookup"><span data-stu-id="c9f65-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9f65-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c9f65-108">Return Value</span></span>  
 <span data-ttu-id="c9f65-109">Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.</span><span class="sxs-lookup"><span data-stu-id="c9f65-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9f65-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9f65-110">HRESULT</span></span>|<span data-ttu-id="c9f65-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c9f65-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9f65-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9f65-112">S_OK</span></span>|<span data-ttu-id="c9f65-113">Metodo completato correttamente.</span><span class="sxs-lookup"><span data-stu-id="c9f65-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9f65-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c9f65-114">E_NOTIMPL</span></span>|<span data-ttu-id="c9f65-115">La versione di common language runtime (CLR) è precedente alla versione CLR in .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c9f65-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9f65-116">Note</span><span class="sxs-lookup"><span data-stu-id="c9f65-116">Remarks</span></span>  
 <span data-ttu-id="c9f65-117">Questo metodo non funziona con le versioni CLR precedenti alla versione di CLR in .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c9f65-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f65-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c9f65-118">Requirements</span></span>  
 <span data-ttu-id="c9f65-119">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f65-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f65-120">**Intestazione:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c9f65-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9f65-121">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c9f65-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9f65-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f65-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f65-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9f65-123">See also</span></span>

- [<span data-ttu-id="c9f65-124">Interfaccia ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="c9f65-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c9f65-125">Interfacce di hosting</span><span class="sxs-lookup"><span data-stu-id="c9f65-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c9f65-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="c9f65-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
