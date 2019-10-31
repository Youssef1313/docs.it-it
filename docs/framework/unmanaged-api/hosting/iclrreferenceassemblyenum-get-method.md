---
title: Metodo ICLRReferenceAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 8f479443e168c3fc7c627c3227e59f1e8b54f0e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120511"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="e07a5-102">Metodo ICLRReferenceAssemblyEnum::Get</span><span class="sxs-lookup"><span data-stu-id="e07a5-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="e07a5-103">Ottiene l'identità dell'assembly in corrispondenza dell'indice fornito.</span><span class="sxs-lookup"><span data-stu-id="e07a5-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07a5-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e07a5-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07a5-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e07a5-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="e07a5-106">in Indice in base zero dell'identità dell'assembly da restituire.</span><span class="sxs-lookup"><span data-stu-id="e07a5-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="e07a5-107">out Buffer contenente i dati di identità dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="e07a5-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="e07a5-108">[in, out] Dimensioni del buffer `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="e07a5-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e07a5-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e07a5-109">Return Value</span></span>  
  
|<span data-ttu-id="e07a5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e07a5-110">HRESULT</span></span>|<span data-ttu-id="e07a5-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e07a5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e07a5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e07a5-112">S_OK</span></span>|<span data-ttu-id="e07a5-113">`Get` ha restituito un esito positivo.</span><span class="sxs-lookup"><span data-stu-id="e07a5-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="e07a5-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e07a5-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e07a5-115">il `pwzBuffer` è troppo piccolo.</span><span class="sxs-lookup"><span data-stu-id="e07a5-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="e07a5-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="e07a5-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="e07a5-117">L'enumerazione non contiene altri elementi.</span><span class="sxs-lookup"><span data-stu-id="e07a5-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="e07a5-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e07a5-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e07a5-119">Il Common Language Runtime (CLR) non è stato caricato in un processo oppure CLR si trova in uno stato in cui non è possibile eseguire codice gestito o elaborare la chiamata correttamente.</span><span class="sxs-lookup"><span data-stu-id="e07a5-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e07a5-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e07a5-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e07a5-121">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="e07a5-121">The call timed out.</span></span>|  
|<span data-ttu-id="e07a5-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e07a5-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e07a5-123">Il chiamante non è il proprietario del blocco.</span><span class="sxs-lookup"><span data-stu-id="e07a5-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e07a5-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e07a5-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e07a5-125">Un evento è stato annullato mentre un thread bloccato o Fiber era in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="e07a5-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e07a5-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e07a5-126">E_FAIL</span></span>|<span data-ttu-id="e07a5-127">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="e07a5-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e07a5-128">Se un metodo restituisce E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="e07a5-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e07a5-129">Le chiamate successive ai metodi di hosting restituiscono HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e07a5-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e07a5-130">Note</span><span class="sxs-lookup"><span data-stu-id="e07a5-130">Remarks</span></span>  
 <span data-ttu-id="e07a5-131">`Get` viene in genere chiamato due volte.</span><span class="sxs-lookup"><span data-stu-id="e07a5-131">`Get` is typically called twice.</span></span> <span data-ttu-id="e07a5-132">La prima chiamata fornisce un valore null per `pwzBuffer`e imposta `pcchBufferSize` sulle dimensioni appropriate per `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="e07a5-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="e07a5-133">La seconda chiamata fornisce un `pwzBuffer`di dimensioni appropriate e contiene i dati di identità dell'assembly canonico al termine dell'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e07a5-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07a5-134">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e07a5-134">Requirements</span></span>  
 <span data-ttu-id="e07a5-135">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e07a5-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07a5-136">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e07a5-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e07a5-137">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e07a5-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e07a5-138">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07a5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07a5-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e07a5-139">See also</span></span>

- [<span data-ttu-id="e07a5-140">Interfaccia ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="e07a5-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e07a5-141">Interfaccia ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="e07a5-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
