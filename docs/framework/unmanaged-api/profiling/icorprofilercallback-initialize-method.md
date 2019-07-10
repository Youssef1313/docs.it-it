---
title: Metodo ICorProfilerCallback::Initialize
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e50421dc15dd30f1811dbe5ebef2ff2f7a0a9483
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755832"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="e7b5b-102">Metodo ICorProfilerCallback::Initialize</span><span class="sxs-lookup"><span data-stu-id="e7b5b-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="e7b5b-103">Chiamato per inizializzare il profiler del codice ogni volta che viene avviata una nuova applicazione di common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e7b5b-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b5b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e7b5b-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7b5b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e7b5b-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="e7b5b-106">[nelle](/cpp/atl/iunknown) interfaccia che il profiler deve eseguire una query per un [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) puntatore a interfaccia.</span><span class="sxs-lookup"><span data-stu-id="e7b5b-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7b5b-107">Note</span><span class="sxs-lookup"><span data-stu-id="e7b5b-107">Remarks</span></span>  
 <span data-ttu-id="e7b5b-108">Il `Initialize` chiamata è l'unico modo per abilitare (o disabilitare) richiamate che non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="e7b5b-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="e7b5b-109">Dopo aver abilitato un callback per il `Initialize` chiamare, non può essere disabilitato in un secondo momento utilizzando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="e7b5b-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="e7b5b-110">Il valore COR_PRF_MONITOR_IMMUTABLE del [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumerazione indica gli eventi che non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="e7b5b-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b5b-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e7b5b-111">Requirements</span></span>  
 <span data-ttu-id="e7b5b-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7b5b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b5b-113">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7b5b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7b5b-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b5b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b5b-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b5b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7b5b-116">See also</span></span>

- [<span data-ttu-id="e7b5b-117">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e7b5b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e7b5b-118">Metodo Shutdown</span><span class="sxs-lookup"><span data-stu-id="e7b5b-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
