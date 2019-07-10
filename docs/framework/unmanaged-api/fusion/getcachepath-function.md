---
title: Funzione GetCachePath
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92366190c769344b41923cbb25ed4b04afceaae9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778665"
---
# <a name="getcachepath-function"></a><span data-ttu-id="d9ef7-102">Funzione GetCachePath</span><span class="sxs-lookup"><span data-stu-id="d9ef7-102">GetCachePath Function</span></span>
<span data-ttu-id="d9ef7-103">Ottiene il percorso all'assembly memorizzati nella cache, usando i flag specificati.</span><span class="sxs-lookup"><span data-stu-id="d9ef7-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ef7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d9ef7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ef7-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d9ef7-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="d9ef7-106">[in] Un' [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) valore che indica l'origine dell'assembly memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="d9ef7-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="d9ef7-107">[out] Il puntatore restituito al percorso.</span><span class="sxs-lookup"><span data-stu-id="d9ef7-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="d9ef7-108">[in, out] La lunghezza massima richiesta del `pwzCachePath`e dopo la restituzione, la lunghezza effettiva dei `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="d9ef7-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ef7-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d9ef7-109">Requirements</span></span>  
 <span data-ttu-id="d9ef7-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ef7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ef7-111">**Intestazione:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d9ef7-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d9ef7-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ef7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ef7-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d9ef7-113">See also</span></span>

- [<span data-ttu-id="d9ef7-114">Enumerazione ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d9ef7-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="d9ef7-115">Funzioni statiche globali Fusion</span><span class="sxs-lookup"><span data-stu-id="d9ef7-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
