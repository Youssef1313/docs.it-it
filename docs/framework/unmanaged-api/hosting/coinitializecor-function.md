---
title: Funzione CoInitializeCor
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e8d65e739504e01a7d11b37d1b34d7313b13a5e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138341"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="a291e-102">Funzione CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="a291e-102">CoInitializeCor Function</span></span>
<span data-ttu-id="a291e-103">`CoInitializeCor` è obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a291e-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a291e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a291e-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a291e-105">Note</span><span class="sxs-lookup"><span data-stu-id="a291e-105">Remarks</span></span>  
 <span data-ttu-id="a291e-106">Per inizializzare la Common Language Runtime, utilizzare [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) o [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="a291e-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a291e-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a291e-107">Requirements</span></span>  
 <span data-ttu-id="a291e-108">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a291e-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a291e-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a291e-109">See also</span></span>

- [<span data-ttu-id="a291e-110">Funzioni statiche globali dei metadati</span><span class="sxs-lookup"><span data-stu-id="a291e-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
