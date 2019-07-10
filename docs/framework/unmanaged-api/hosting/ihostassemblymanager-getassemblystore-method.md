---
title: Metodo IHostAssemblyManager::GetAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 194b40b0873cee848124a5afc9a47740d59969c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779461"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="6af1f-102">Metodo IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="6af1f-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="6af1f-103">Ottiene un puntatore a interfaccia a un [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) che rappresenta l'elenco di assembly caricati dall'host.</span><span class="sxs-lookup"><span data-stu-id="6af1f-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af1f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6af1f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af1f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="6af1f-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="6af1f-106">[out] Un puntatore a funzione a un `IHostAssemblyStore` dell'istanza o null se l'host non implementa `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="6af1f-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6af1f-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6af1f-107">Return Value</span></span>  
  
|<span data-ttu-id="6af1f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6af1f-108">HRESULT</span></span>|<span data-ttu-id="6af1f-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6af1f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6af1f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6af1f-110">S_OK</span></span>|<span data-ttu-id="6af1f-111">`GetAssemblyStore` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="6af1f-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="6af1f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6af1f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6af1f-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="6af1f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6af1f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6af1f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6af1f-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="6af1f-115">The call timed out.</span></span>|  
|<span data-ttu-id="6af1f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6af1f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6af1f-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="6af1f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6af1f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6af1f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6af1f-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="6af1f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6af1f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6af1f-120">E_FAIL</span></span>|<span data-ttu-id="6af1f-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="6af1f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6af1f-122">Quando un metodo di E_FAIL viene restituito, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="6af1f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6af1f-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6af1f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6af1f-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="6af1f-124">E_NOINTERFACE</span></span>|<span data-ttu-id="6af1f-125">L'host non fornisce un'implementazione di `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="6af1f-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6af1f-126">Note</span><span class="sxs-lookup"><span data-stu-id="6af1f-126">Remarks</span></span>  
 <span data-ttu-id="6af1f-127">`IHostAssemblyStore` fornisce metodi che consentono a un host da associare agli assembly e moduli indipendentemente da CLR.</span><span class="sxs-lookup"><span data-stu-id="6af1f-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="6af1f-128">Gli host forniscono in genere gli archivi di assembly per consentire il caricamento da formati diversi da file system di assembly.</span><span class="sxs-lookup"><span data-stu-id="6af1f-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6af1f-129">Se l'host non implementa `IHostAssemblyStore`, `GetAssemblyStore` deve restituire un valore HRESULT di tipo E_NOINTERFACE e devono impostare `ppAssemblyStore` su null.</span><span class="sxs-lookup"><span data-stu-id="6af1f-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af1f-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6af1f-130">Requirements</span></span>  
 <span data-ttu-id="6af1f-131">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af1f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af1f-132">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6af1f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6af1f-133">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6af1f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6af1f-134">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af1f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af1f-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6af1f-135">See also</span></span>

- [<span data-ttu-id="6af1f-136">Interfaccia IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="6af1f-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="6af1f-137">Interfaccia IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="6af1f-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
