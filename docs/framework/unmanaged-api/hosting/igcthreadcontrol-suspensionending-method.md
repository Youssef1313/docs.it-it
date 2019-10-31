---
title: Metodo IGCThreadControl::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134789"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="9ad25-102">Metodo IGCThreadControl::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="9ad25-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="9ad25-103">Notifica all'host che il Runtime sta riprendendo i thread dopo una Garbage Collection o un'altra sospensione.</span><span class="sxs-lookup"><span data-stu-id="9ad25-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad25-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9ad25-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ad25-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="9ad25-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="9ad25-106">in Generazione in cui è stata eseguita una Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="9ad25-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ad25-107">Note</span><span class="sxs-lookup"><span data-stu-id="9ad25-107">Remarks</span></span>  
 <span data-ttu-id="9ad25-108">Non ripianificare alcun thread durante il callback `SuspensionEnding`.</span><span class="sxs-lookup"><span data-stu-id="9ad25-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad25-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9ad25-109">Requirements</span></span>  
 <span data-ttu-id="9ad25-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad25-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad25-111">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9ad25-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ad25-112">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ad25-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ad25-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad25-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad25-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9ad25-114">See also</span></span>

- [<span data-ttu-id="9ad25-115">Interfaccia IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="9ad25-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
