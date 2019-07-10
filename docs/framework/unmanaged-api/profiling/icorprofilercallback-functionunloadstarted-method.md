---
title: Metodo ICorProfilerCallback::FunctionUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6dd7792fe298aa1950b23053a7c5cd576b62e7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755888"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="61f61-102">Metodo ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="61f61-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="61f61-103">Notifica al profiler che il runtime ha iniziato a scaricare una funzione.</span><span class="sxs-lookup"><span data-stu-id="61f61-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61f61-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="61f61-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="61f61-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="61f61-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="61f61-106">[in] L'ID della funzione che sta per essere scaricata.</span><span class="sxs-lookup"><span data-stu-id="61f61-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61f61-107">Note</span><span class="sxs-lookup"><span data-stu-id="61f61-107">Remarks</span></span>  
 <span data-ttu-id="61f61-108">Il valore della `functionId` parametro non è più valido dopo che questo metodo viene restituito al chiamante.</span><span class="sxs-lookup"><span data-stu-id="61f61-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61f61-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="61f61-109">Requirements</span></span>  
 <span data-ttu-id="61f61-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61f61-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61f61-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61f61-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61f61-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61f61-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61f61-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61f61-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f61-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="61f61-114">See also</span></span>

- [<span data-ttu-id="61f61-115">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="61f61-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
