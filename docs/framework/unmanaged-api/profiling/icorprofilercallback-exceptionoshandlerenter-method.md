---
title: Metodo ICorProfilerCallback::ExceptionOSHandlerEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: b3088308e75fb7cbffcc439ab4440255ed0fb2b9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444907"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="6a5e8-102">Metodo ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="6a5e8-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="6a5e8-103">Non implementato.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-103">Not implemented.</span></span> <span data-ttu-id="6a5e8-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5e8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6a5e8-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6a5e8-106">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6a5e8-106">Requirements</span></span>  
 <span data-ttu-id="6a5e8-107">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5e8-108">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a5e8-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a5e8-109">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a5e8-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a5e8-110">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5e8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5e8-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6a5e8-111">See also</span></span>

- [<span data-ttu-id="6a5e8-112">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6a5e8-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
