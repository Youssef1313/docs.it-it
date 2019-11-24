---
title: Metodo ICorProfilerCallback4::SurvivingReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: 3178d099db96d52f0238cfcf7e055e761687ce30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430091"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>Metodo ICorProfilerCallback4::SurvivingReferences2
Indica il layout degli oggetti nell'heap in seguito a un'operazione di Garbage Collection senza compattazione. This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametri  
 `cSurvivingObjectIDRanges`  
 [in] Numero di blocchi di oggetti contigui rimasti in seguito alla mancata compattazione dell'operazione di Garbage Collection, ovvero il valore di `cSurvivingObjectIDRanges` è la dimensione delle matrici `objectIDRangeStart` e `cObjectIDRangeLength`, in cui vengono rispettivamente archiviati un `ObjectID` e una lunghezza per ogni blocco di oggetti.  
  
 I successivi due argomenti di `SurvivingReferences2` sono matrici parallele. In altre parole, `objectIDRangeStart` e `cObjectIDRangeLength` riguardano lo stesso blocco di oggetti contigui.  
  
 `objectIDRangeStart`  
 [in] Matrice di valori `ObjectID`, ognuno dei quali è l'indirizzo iniziale di un blocco di oggetti attivi contigui in memoria.  
  
 `cObjectIDRangeLength`  
 [in] Matrice di Integer, ognuno dei quali è la dimensione di un blocco escluso di oggetti contigui in memoria.  
  
 Viene specificata una dimensione per ogni blocco a cui si fa riferimento nella matrice `objectIDRangeStart`.  
  
## <a name="remarks"></a>Note  
 Gli elementi delle matrici `objectIDRangeStart` e `cObjectIDRangeLength` devono essere interpretati come indicato di seguito per determinare se un oggetto è stato escluso dall'operazione di Garbage Collection. Si supponga che un valore `ObjectID` (`ObjectID`) si trovi nell'intervallo seguente:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Per qualsiasi valore di `i` compreso nell'intervallo seguente, l'oggetto è stato escluso dall'operazione di Garbage Collection:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Una mancata compattazione dell'operazione di Garbage Collection recupera la memoria occupata dagli oggetti inutilizzati, ma non compatta lo spazio liberato. Di conseguenza, la memoria viene restituita all'heap, ma gli oggetti attivi non vengono spostati.  
  
 Common Language Runtime (CLR) chiama `SurvivingReferences2` per eseguire operazioni di Garbage Collection senza compattazione. For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead. Una stessa operazione di Garbage Collection può eseguire la compattazione per una generazione e non eseguirla per un'altra. For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.  
  
 Durante una particolare operazione di Garbage Collection possono essere ricevuti più callback `SurvivingReferences2`, a causa del buffer interno limitato, di callback multipli durante l'operazione di Garbage Collection per server e di altri motivi. Nel caso di più callback durante un'operazione di Garbage Collection, le informazioni sono cumulative. Tutti i riferimenti segnalati in qualsiasi callback `SurvivingReferences2` vengono esclusi dall'operazione di Garbage Collection.  
  
 If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully. I profiler possono restituire un valore HRESULT indicante un errore nel metodo `SurvivingReferences2` per evitare di chiamare il secondo metodo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interfaccia ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interfaccia ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
