---
title: Metodo ICLRHostProtectionManager::SetProtectedCategories
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f6dc1254261197583f2369587a61b5e179d760b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779647"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="f0e68-102">Metodo ICLRHostProtectionManager::SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="f0e68-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="f0e68-103">Specifica le categorie di tipi e membri gestiti devono essere impedite l'esecuzione di codice parzialmente attendibile.</span><span class="sxs-lookup"><span data-stu-id="f0e68-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e68-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f0e68-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0e68-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f0e68-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="f0e68-106">[in] Una combinazione di [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) valori, che indica quali categorie di tipi e membri gestiti devono essere impedite l'esecuzione di codice parzialmente attendibile.</span><span class="sxs-lookup"><span data-stu-id="f0e68-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0e68-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f0e68-107">Return Value</span></span>  
  
|<span data-ttu-id="f0e68-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0e68-108">HRESULT</span></span>|<span data-ttu-id="f0e68-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f0e68-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0e68-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0e68-110">S_OK</span></span>|<span data-ttu-id="f0e68-111">`SetProtectedCategories` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="f0e68-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="f0e68-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0e68-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0e68-113">Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="f0e68-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0e68-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0e68-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0e68-115">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="f0e68-115">The call timed out.</span></span>|  
|<span data-ttu-id="f0e68-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0e68-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0e68-117">Il chiamante non possiede il blocco.</span><span class="sxs-lookup"><span data-stu-id="f0e68-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0e68-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0e68-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0e68-119">Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="f0e68-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0e68-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0e68-120">E_FAIL</span></span>|<span data-ttu-id="f0e68-121">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="f0e68-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0e68-122">Dopo che un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="f0e68-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0e68-123">Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0e68-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e68-124">Note</span><span class="sxs-lookup"><span data-stu-id="f0e68-124">Remarks</span></span>  
 <span data-ttu-id="f0e68-125">Ogni `EApiCategories` valore si riferisce a un elenco di tipi e membri gestiti.</span><span class="sxs-lookup"><span data-stu-id="f0e68-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="f0e68-126">Il `EApiCategories` enumerazione e la `SetProtectedCategories` metodo sono direttamente correlati all'oggetto gestito <xref:System.Security.Permissions.HostProtectionAttribute> classe, che viene usato per contrassegnare tipi e membri che espongono funzionalità corrispondenti per le categorie descritte dal gestiti `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="f0e68-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="f0e68-127">Per altre informazioni, vedere <xref:System.Security.Permissions.HostProtectionAttribute> e il <xref:System.Security.Permissions.HostProtectionResource> enumerazione che corrisponde direttamente al `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="f0e68-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e68-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f0e68-128">Requirements</span></span>  
 <span data-ttu-id="f0e68-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e68-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e68-130">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0e68-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0e68-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f0e68-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0e68-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e68-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e68-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f0e68-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="f0e68-134">Enumerazione EApiCategories</span><span class="sxs-lookup"><span data-stu-id="f0e68-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="f0e68-135">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="f0e68-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f0e68-136">Interfaccia ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="f0e68-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
