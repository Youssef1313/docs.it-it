---
title: Metodo ICorProfilerCallback::ExceptionSearchFunctionLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: 6cd6b7981c9b6b7f2efd30b045e8e179a22a3b87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445362"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="e6d65-102">Metodo ICorProfilerCallback::ExceptionSearchFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="e6d65-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="e6d65-103">Notifica al profiler che la fase di ricerca della gestione delle eccezioni ha terminato la ricerca di una funzione.</span><span class="sxs-lookup"><span data-stu-id="e6d65-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d65-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e6d65-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e6d65-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e6d65-105">Requirements</span></span>  
 <span data-ttu-id="e6d65-106">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d65-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d65-107">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6d65-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6d65-108">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6d65-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6d65-109">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d65-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d65-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e6d65-110">See also</span></span>

- [<span data-ttu-id="e6d65-111">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e6d65-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e6d65-112">Metodo ExceptionSearchFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="e6d65-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
