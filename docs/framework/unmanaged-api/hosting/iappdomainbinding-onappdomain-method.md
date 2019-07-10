---
title: Metodo IAppDomainBinding::OnAppDomain
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 523f90966501e06994fb0e11b3c77aa62c378eef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770469"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="368dc-102">Metodo IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="368dc-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="368dc-103">Chiamato da common language runtime (CLR) per notificare all'host che è stato creato un dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="368dc-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368dc-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="368dc-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="368dc-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="368dc-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="368dc-106">[in] Un puntatore a un [IUnknown](/cpp/atl/iunknown) oggetto di interfaccia che rappresenta il nuovo dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="368dc-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="368dc-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="368dc-107">Requirements</span></span>  
 <span data-ttu-id="368dc-108">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="368dc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="368dc-109">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="368dc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="368dc-110">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="368dc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="368dc-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="368dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368dc-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="368dc-112">See also</span></span>

- [<span data-ttu-id="368dc-113">Interfaccia IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="368dc-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
