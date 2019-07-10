---
title: Metodo IGCHost::SetVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c43c2259d5b899f05e42437aa121dde57ce4b0c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766491"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="dc06c-102">Metodo IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="dc06c-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="dc06c-103">Imposta la dimensione massima di memoria virtuale del runtime.</span><span class="sxs-lookup"><span data-stu-id="dc06c-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc06c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dc06c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc06c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="dc06c-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="dc06c-106">[in] Le dimensioni massime, in megabyte, della memoria virtuale del runtime.</span><span class="sxs-lookup"><span data-stu-id="dc06c-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc06c-107">Note</span><span class="sxs-lookup"><span data-stu-id="dc06c-107">Remarks</span></span>  
 <span data-ttu-id="dc06c-108">La dimensione massima di memoria virtuale del runtime può essere modificata in modo dinamico.</span><span class="sxs-lookup"><span data-stu-id="dc06c-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc06c-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dc06c-109">Requirements</span></span>  
 <span data-ttu-id="dc06c-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc06c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc06c-111">**Intestazione:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="dc06c-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dc06c-112">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dc06c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc06c-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc06c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc06c-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dc06c-114">See also</span></span>

- [<span data-ttu-id="dc06c-115">Interfaccia IGCHost</span><span class="sxs-lookup"><span data-stu-id="dc06c-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
