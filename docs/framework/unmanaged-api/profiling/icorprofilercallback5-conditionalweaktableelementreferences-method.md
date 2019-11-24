---
title: Metodo ICorProfilerCallback5::ConditionalWeakTableElementReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: ad721d28f6a7dc6ae0370ce10178990cb02fb9f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430060"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Metodo ICorProfilerCallback5::ConditionalWeakTableElementReferences

Identifica la chiusura transitiva di oggetti a cui le radici fanno riferimento tramite i riferimenti di campo di membri diretti e tramite le dipendenze `ConditionalWeakTable`.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Parametri

`cRootRefs`\
[in] Numero di elementi nelle matrici `keyRefIds`, `valueRefIds` e `rootIds`.

`keyRefIds`\
[in] Matrice di ID oggetto, ognuno dei quali include il valore `ObjectID` per l'elemento primario nella coppia di handle dipendente.

`valueRefIds`\
[in] Matrice di ID oggetto, ognuno dei quali include il valore `ObjectID` per l'elemento secondario nella coppia di handle dipendente. (`keyRefIds[i]` keeps `valueRefIds[i]` alive.)

`rootIds`\
[in] Matrice di valori `GCHandleID` che fanno riferimento a un valore Integer contenente informazioni aggiuntive sulla radice di Garbage Collection.

Nessuno dei valori `ObjectID` restituito dal metodo `ConditionalWeakTableElementReferences` è valido durante il callback stesso, poiché è possibile che il Garbage Collector stia spostando oggetti da posizioni precedenti a nuove posizioni. I profiler non devono quindi tentare di verificare gli oggetti durante una chiamata a `ConditionalWeakTableElementReferences`. In corrispondenza di `GarbageCollectionFinished`, tutti gli oggetti saranno stati spostati nelle nuove posizioni e sarà possibile verificarli.

## <a name="example"></a>Esempio

The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a>Note

A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method. `ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries. These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.

## <a name="requirements"></a>Requisiti

**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).

**Intestazione:** CorProf.idl, CorProf.h

**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback5](icorprofilercallback5-interface.md)
