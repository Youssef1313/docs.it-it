---
title: Metodo ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 39882a554f9d47040bef00ff320d15b56abea533
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445718"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="48cd8-102">Metodo ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="48cd8-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="48cd8-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span><span class="sxs-lookup"><span data-stu-id="48cd8-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cd8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="48cd8-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="48cd8-105">Note</span><span class="sxs-lookup"><span data-stu-id="48cd8-105">Remarks</span></span>  
 <span data-ttu-id="48cd8-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span><span class="sxs-lookup"><span data-stu-id="48cd8-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="48cd8-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span><span class="sxs-lookup"><span data-stu-id="48cd8-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="48cd8-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span><span class="sxs-lookup"><span data-stu-id="48cd8-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48cd8-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span><span class="sxs-lookup"><span data-stu-id="48cd8-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="48cd8-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span><span class="sxs-lookup"><span data-stu-id="48cd8-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48cd8-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="48cd8-111">Requirements</span></span>  
 <span data-ttu-id="48cd8-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48cd8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48cd8-113">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48cd8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48cd8-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48cd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48cd8-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48cd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48cd8-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48cd8-116">See also</span></span>

- [<span data-ttu-id="48cd8-117">Interfaccia ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="48cd8-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="48cd8-118">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="48cd8-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="48cd8-119">Profilatura</span><span class="sxs-lookup"><span data-stu-id="48cd8-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
