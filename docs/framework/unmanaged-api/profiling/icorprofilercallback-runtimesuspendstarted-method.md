---
title: Metodo ICorProfilerCallback::RuntimeSuspendStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 1777fa1f2537b6d28d771661ca463564d74d8550
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433516"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="bbd0f-102">Metodo ICorProfilerCallback::RuntimeSuspendStarted</span><span class="sxs-lookup"><span data-stu-id="bbd0f-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="bbd0f-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd0f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bbd0f-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbd0f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bbd0f-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="bbd0f-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbd0f-107">Note</span><span class="sxs-lookup"><span data-stu-id="bbd0f-107">Remarks</span></span>  
 <span data-ttu-id="bbd0f-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="bbd0f-109">At that point they will also be suspended until the runtime resumes.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="bbd0f-110">This also applies to new threads that enter the runtime.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="bbd0f-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span><span class="sxs-lookup"><span data-stu-id="bbd0f-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd0f-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bbd0f-112">Requirements</span></span>  
 <span data-ttu-id="bbd0f-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd0f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd0f-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bbd0f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bbd0f-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbd0f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbd0f-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd0f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd0f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbd0f-117">See also</span></span>

- [<span data-ttu-id="bbd0f-118">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bbd0f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bbd0f-119">Metodo RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="bbd0f-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="bbd0f-120">Metodo RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="bbd0f-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
