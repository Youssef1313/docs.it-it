---
title: Metodo ICorProfilerCallback::RuntimeThreadSuspended
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d03e760d2b08cd9ee8cdfd85e2e28223aeacd4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747229"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>Metodo ICorProfilerCallback::RuntimeThreadSuspended
Notifica al profiler che il thread specificato è stato sospeso o sta per essere sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametri  
 `threadId`  
 [in] L'ID del thread che è stata sospesa.  
  
## <a name="remarks"></a>Note  
 Il `RuntimeThreadSuspended` notifica può verificarsi in qualsiasi momento tra il [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) associate [RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) i callback. Le notifiche che si verificano tra [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e `RuntimeResumeStarted` sono per i thread che era in esecuzione nel codice non gestito e sono stati sospesi al momento dell'accesso al runtime.  
  
 In genere, questo callback si verifica solo dopo che un thread viene sospeso. Tuttavia, se il thread attualmente in esecuzione (il thread che ha chiamato tale callback) è quello che è stato sospeso, questo callback si verificherà prima che il thread viene sospeso.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Metodo RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
