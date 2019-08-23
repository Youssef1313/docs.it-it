---
title: Enumerazione COR_PRF_JIT_CACHE
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30500e8ea55f8298b9a980e34dc611b58a51bdcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916391"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="5aef9-102">Enumerazione COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="5aef9-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="5aef9-103">Indica il risultato della ricerca di una funzione memorizzata nella cache.</span><span class="sxs-lookup"><span data-stu-id="5aef9-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aef9-104">`COR_PRF_CACHED_FUNCTION_FOUND`ha un valore pari a zero, `COR_PRF_JIT_CACHE` quindi non può essere usato come surrogato booleano.</span><span class="sxs-lookup"><span data-stu-id="5aef9-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aef9-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5aef9-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="5aef9-106">Members</span><span class="sxs-lookup"><span data-stu-id="5aef9-106">Members</span></span>  
  
|<span data-ttu-id="5aef9-107">Member</span><span class="sxs-lookup"><span data-stu-id="5aef9-107">Member</span></span>|<span data-ttu-id="5aef9-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5aef9-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="5aef9-109">La ricerca ha rilevato la funzione.</span><span class="sxs-lookup"><span data-stu-id="5aef9-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="5aef9-110">La ricerca non ha trovato la funzione.</span><span class="sxs-lookup"><span data-stu-id="5aef9-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5aef9-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5aef9-111">Requirements</span></span>  
 <span data-ttu-id="5aef9-112">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aef9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aef9-113">**Intestazione:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5aef9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5aef9-114">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aef9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aef9-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aef9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aef9-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5aef9-116">See also</span></span>

- [<span data-ttu-id="5aef9-117">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="5aef9-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
