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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20fd186c32857fe547c47d06874f635a5628b178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750773"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="96846-102">Metodo ICorProfilerCallback::RuntimeSuspendStarted</span><span class="sxs-lookup"><span data-stu-id="96846-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="96846-103">Notifica al profiler che il runtime sta per sospendere tutti i thread di runtime.</span><span class="sxs-lookup"><span data-stu-id="96846-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96846-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="96846-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96846-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="96846-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="96846-106">[in] Valore di [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumerazione che indica il motivo della sospensione.</span><span class="sxs-lookup"><span data-stu-id="96846-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96846-107">Note</span><span class="sxs-lookup"><span data-stu-id="96846-107">Remarks</span></span>  
 <span data-ttu-id="96846-108">Sono consentiti tutti i thread di runtime in codice non gestito per continuare l'esecuzione fino a quando non tentano di immettere nuovamente la fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="96846-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="96846-109">A questo punto si verranno inoltre sospese fino a quando il runtime riprende.</span><span class="sxs-lookup"><span data-stu-id="96846-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="96846-110">Questo vale anche per nuovi thread che accedono al runtime.</span><span class="sxs-lookup"><span data-stu-id="96846-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="96846-111">Tutti i thread nel runtime vengono che sospesi immediatamente se sono già nel codice che possono essere interrotte, o gli viene chiesto sospese quando raggiungono codice.</span><span class="sxs-lookup"><span data-stu-id="96846-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96846-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="96846-112">Requirements</span></span>  
 <span data-ttu-id="96846-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96846-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96846-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96846-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96846-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96846-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96846-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96846-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96846-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="96846-117">See also</span></span>

- [<span data-ttu-id="96846-118">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="96846-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="96846-119">Metodo RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="96846-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="96846-120">Metodo RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="96846-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
