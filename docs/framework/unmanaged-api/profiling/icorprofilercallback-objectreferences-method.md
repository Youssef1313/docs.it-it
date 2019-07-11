---
title: Metodo ICorProfilerCallback::ObjectReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4141c79502dae89ec228e4e39da121615f292786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782967"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>Metodo ICorProfilerCallback::ObjectReferences
Notifica al profiler sugli oggetti in memoria a cui fa riferimento l'oggetto specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametri  
 `objectId`  
 [in] L'ID dell'oggetto a cui fa riferimento a oggetti.  
  
 `classId`  
 [in] L'ID della classe che l'oggetto specificato è un'istanza di.  
  
 `cObjectRefs`  
 [in] Il numero di oggetti a cui fa riferimento l'oggetto specificato (ovvero, il numero di elementi nel `objectRefIds` matrice).  
  
 `objectRefIds`  
 [in] Matrice di ID di oggetti a cui fa riferimento `objectId`.  
  
## <a name="remarks"></a>Note  
 Il `ObjectReferences` viene chiamato per ogni oggetto rimane nell'heap dopo un'operazione di garbage collection è stata completata. Se il profiler restituisce un errore da questo callback, i servizi di profilatura non richiameranno questo callback finché la successiva garbage collection.  
  
 Il `ObjectReferences` callback può essere usato in combinazione con il [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback per creare un grafico di riferimento di oggetto completo per il runtime. Common language runtime (CLR) garantisce che ogni riferimento all'oggetto viene segnalato una sola volta per il `ObjectReferences` (metodo).  
  
 L'ID di oggetto restituito da `ObjectReferences` nejsou platné durante il callback vero e proprio, perché l'operazione di garbage collection stia ancora spostando gli oggetti. Pertanto, profiler non deve tentare di controllare gli oggetti durante una `ObjectReferences` chiamare. Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) viene chiamato, l'operazione di garbage collection è stata completata e ispezione può essere eseguita in modo sicuro.  
  
 Un valore null `ClassId` indica che `objectId` dispone di un tipo che lo scaricamento.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
