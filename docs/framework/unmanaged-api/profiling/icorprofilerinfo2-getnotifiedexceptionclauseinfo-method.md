---
title: Metodo ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a659e139040174a66043283ed4633d9c9d223ce8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774042"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="af0d2-102">Metodo ICorProfilerInfo2::GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="af0d2-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="af0d2-103">Ottiene le informazioni di indirizzo e frame native per la clausola di eccezione (`catch`/`finally`/`filter`) che sta per essere eseguiti o che è stata appena eseguita.</span><span class="sxs-lookup"><span data-stu-id="af0d2-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0d2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="af0d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af0d2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="af0d2-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="af0d2-106">[out] Un puntatore a un [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) struttura che descrive l'istanza corrente di una clausola eccezione e il relativo frame associato.</span><span class="sxs-lookup"><span data-stu-id="af0d2-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af0d2-107">Note</span><span class="sxs-lookup"><span data-stu-id="af0d2-107">Remarks</span></span>  
 <span data-ttu-id="af0d2-108">Quando viene ricevuta una notifica di eccezione, `GetNotifiedExceptionClauseInfo` può essere utilizzato per ottenere le informazioni di indirizzo e frame native per la clausola di eccezione (`catch`/`finally`/`filter`) che sta per essere eseguito ([ ICorProfilerCallback:: ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), o [ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)callback viene ricevuto dal profiler) o semplicemente è stato eseguito ([ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), o [ ICorProfilerCallback:: ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback viene ricevuto dal profiler).</span><span class="sxs-lookup"><span data-stu-id="af0d2-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="af0d2-109">Questa chiamata può essere effettuata in qualsiasi momento dopo uno dei callback invio precedente finché non viene ricevuto il callback lascia corrispondenza o viene generata un'eccezione annidata nella clausola corrente, nel qual caso non vi è alcuna notifica di congedo per tale clausola.</span><span class="sxs-lookup"><span data-stu-id="af0d2-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="af0d2-110">Si noti che non è possibile che un'eccezione generata eseguire l'escape un `filter` clausola di eccezione, così esiste sempre una notifica di lasciare in questo caso.</span><span class="sxs-lookup"><span data-stu-id="af0d2-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af0d2-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="af0d2-111">Requirements</span></span>  
 <span data-ttu-id="af0d2-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af0d2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0d2-113">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af0d2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af0d2-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af0d2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af0d2-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0d2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0d2-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="af0d2-116">See also</span></span>

- [<span data-ttu-id="af0d2-117">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="af0d2-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="af0d2-118">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="af0d2-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
