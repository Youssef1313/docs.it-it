---
title: Interfaccia ICorProfilerCallback2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: a7867c63f76db38a16784c03fadd9fc917ecc4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439693"
---
# <a name="icorprofilercallback2-interface"></a>Interfaccia ICorProfilerCallback2
Fornisce i metodi utilizzati dal Common Language Runtime (CLR) per notificare a un Code Profiler quando si verificano gli eventi sottoscritti dal profiler. L'interfaccia `ICorProfilerCallback2` è un'estensione dell'interfaccia [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) . Ovvero fornisce nuovi callback introdotti nella versione .NET Framework 2,0.  
  
> [!NOTE]
> Ogni implementazione del metodo deve restituire un valore HRESULT con un valore di S_OK in caso di esito positivo o E_FAIL in caso di errore. Attualmente CLR ignora il valore HRESULT restituito da ogni callback eccetto [ICorProfilerCallback:: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Notifica all'Code Profiler che un oggetto con un finalizzatore è stato accodato al thread del finalizzatore per l'esecuzione del relativo metodo di `Finalize`.|  
|[Metodo GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Notifica al profiler che un Garbage Collection è stato completato e che sono stati rilasciati tutti i callback di Garbage Collection.|  
|[Metodo GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Notifica all'Code Profiler l'avvio di un Garbage Collection.|  
|[Metodo HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Notifica all'Code Profiler che è stato creato un handle di Garbage Collection.|  
|[Metodo HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Notifica all'Code Profiler che un handle di Garbage Collection è stato eliminato definitivamente.|  
|[Metodo RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Notifica al profiler i riferimenti radice dopo che si è verificato un Garbage Collection. Questo metodo è un'estensione del metodo [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .|  
|[Metodo SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Notifica al profiler i riferimenti a oggetti che sono sopravvissuti a una Garbage Collection.|  
|[Metodo ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Notifica all'Code Profiler che il nome di un thread è stato modificato.|  
  
## <a name="remarks"></a>Osservazioni  
 CLR chiama un metodo nell'interfaccia `ICorProfilerCallback` (o `ICorProfilerCallback2`) per notificare al profiler quando si verifica un evento in cui è stato sottoscritto il profiler. Si tratta dell'interfaccia di callback primaria tramite la quale CLR comunica con il Code Profiler.  
  
 Un Code Profiler deve implementare i metodi dell'interfaccia `ICorProfilerCallback`. Per la .NET Framework 2,0 e versioni successive, il profiler deve implementare anche i metodi di `ICorProfilerCallback2`. Ogni implementazione del metodo deve restituire un valore HRESULT con un valore di S_OK in caso di esito positivo o E_FAIL in caso di errore. Attualmente CLR ignora il valore HRESULT restituito da ogni callback eccetto [ICorProfilerCallback:: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 È necessario che un Code Profiler registri nel registro di sistema di Microsoft Windows, ovvero l'oggetto COM che implementa le interfacce `ICorProfilerCallback` e `ICorProfilerCallback2`. Un Code Profiler sottoscrive gli eventi per i quali vuole ricevere una notifica chiamando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Questa operazione viene in genere eseguita nell'implementazione del profiler di [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Il profiler può quindi ricevere una notifica dal runtime quando un evento sta per verificarsi o si è appena verificato in un processo di runtime in esecuzione.  
  
> [!NOTE]
> Il profiler registra un singolo oggetto COM. Se il profiler è destinato .NET Framework versione 1,0 o 1,1, tale oggetto COM deve implementare solo i metodi di `ICorProfilerCallback`. Se la destinazione è .NET Framework versione 2,0 e successive, anche l'oggetto COM deve implementare i metodi di `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di profilatura](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interfaccia ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [Interfaccia ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
