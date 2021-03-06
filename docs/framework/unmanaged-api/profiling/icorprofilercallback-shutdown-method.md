---
title: Metodo ICorProfilerCallback::Shutdown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446939"
---
# <a name="icorprofilercallbackshutdown-method"></a>Metodo ICorProfilerCallback::Shutdown
Notifica al profiler che l'applicazione è in fase di chiusura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Note  
 Il codice del profiler non può chiamare in modo sicuro i metodi dell'interfaccia [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) dopo la chiamata del metodo `Shutdown`. Tutte le chiamate ai metodi `ICorProfilerInfo` hanno come risultato un comportamento non definito dopo la restituzione del metodo `Shutdown`. Alcuni eventi non modificabili possono ancora verificarsi dopo l'arresto. il profiler deve prestare attenzione a restituire immediatamente quando si verifica questo problema.  
  
 Il metodo `Shutdown` verrà chiamato solo se l'applicazione gestita sottomessa a profilatura è stata avviata come codice gestito, ovvero il frame iniziale nello stack del processo è gestito. Se l'applicazione è stata avviata come codice non gestito, ma in seguito viene passata al codice gestito, creando quindi un'istanza del Common Language Runtime (CLR), `Shutdown` non verrà chiamata. In questi casi, il profiler deve includere nella relativa libreria un `DllMain` routine che usa il valore DLL_PROCESS_DETACH per liberare le risorse ed eseguire l'elaborazione di pulitura dei dati, ad esempio lo scaricamento delle tracce sul disco e così via.  
  
 In generale, il profiler deve far fronte a arresti imprevisti. È ad esempio possibile che un processo venga interrotto da Win32 `TerminateProcess` metodo (dichiarato in winbase. h). In altri casi, CLR interromperà alcuni thread gestiti (thread in background) senza dover recapitano i messaggi di distruzione ordinata.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Metodo Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
