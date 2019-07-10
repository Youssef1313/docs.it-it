---
title: Metodo ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31766fed66368c044b188b5a58452a5e264a25cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782204"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="887a0-102">Metodo ICorProfilerInfo2::SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="887a0-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="887a0-103">Specifica funzioni implementate dal profiler verrà chiamato sulle versioni aggiornate del "Immettere", "Continua" e "tailcall" hook di funzioni gestite.</span><span class="sxs-lookup"><span data-stu-id="887a0-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887a0-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="887a0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="887a0-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="887a0-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="887a0-106">[in] Un puntatore all'implementazione da usare come le [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span><span class="sxs-lookup"><span data-stu-id="887a0-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="887a0-107">[in] Un puntatore all'implementazione da usare come le [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span><span class="sxs-lookup"><span data-stu-id="887a0-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="887a0-108">[in] Un puntatore all'implementazione da usare come le [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span><span class="sxs-lookup"><span data-stu-id="887a0-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="887a0-109">Note</span><span class="sxs-lookup"><span data-stu-id="887a0-109">Remarks</span></span>  
 <span data-ttu-id="887a0-110">Il `SetEnterLeaveFunctionHooks2` metodo è simile al [SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="887a0-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="887a0-111">Utilizzare la precedente per specificare le funzioni da utilizzare come le versioni più recenti di callback invio/leave/tailcall e quest'ultimo per specificare le funzioni da utilizzare come le versioni precedenti dei callback di invio/leave/tailcall.</span><span class="sxs-lookup"><span data-stu-id="887a0-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="887a0-112">Un solo set di callback può essere attivo contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="887a0-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="887a0-113">Di conseguenza, se un profiler chiama entrambe `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` viene usato.</span><span class="sxs-lookup"><span data-stu-id="887a0-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="887a0-114">Il `SetEnterLeaveFunctionHooks2` metodo può essere chiamato solo da del profiler [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="887a0-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887a0-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="887a0-115">Requirements</span></span>  
 <span data-ttu-id="887a0-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="887a0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887a0-117">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="887a0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="887a0-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="887a0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="887a0-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887a0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887a0-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="887a0-120">See also</span></span>

- [<span data-ttu-id="887a0-121">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="887a0-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="887a0-122">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="887a0-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
