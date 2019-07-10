---
title: Enumerazione COR_PRF_MISC
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dd3cf7e4badf8caa711f2a1b972d9fa14215204
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752137"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="3e419-102">Enumerazione COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="3e419-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="3e419-103">Contiene valori costanti che specificano identificatori speciali.</span><span class="sxs-lookup"><span data-stu-id="3e419-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e419-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3e419-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="3e419-105">Membri</span><span class="sxs-lookup"><span data-stu-id="3e419-105">Members</span></span>  
  
|<span data-ttu-id="3e419-106">Member</span><span class="sxs-lookup"><span data-stu-id="3e419-106">Member</span></span>|<span data-ttu-id="3e419-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3e419-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="3e419-108">L'identificatore predefinito utilizzato dai [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) per un modulo che non è ancora stato associato a un assembly.</span><span class="sxs-lookup"><span data-stu-id="3e419-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="3e419-109">L'identificatore di classe predefinito per le costanti globali che non appartengono a una classe.</span><span class="sxs-lookup"><span data-stu-id="3e419-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="3e419-110">L'identificatore del modulo predefinito per gli oggetti globali che non appartengono a un modulo.</span><span class="sxs-lookup"><span data-stu-id="3e419-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e419-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3e419-111">Requirements</span></span>  
 <span data-ttu-id="3e419-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e419-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e419-113">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e419-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e419-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e419-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e419-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e419-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e419-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3e419-116">See also</span></span>

- [<span data-ttu-id="3e419-117">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="3e419-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
