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
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="ae111-102">Metodo ICorProfilerCallback5::ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="ae111-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="ae111-103">Identifica la chiusura transitiva di oggetti a cui le radici fanno riferimento tramite i riferimenti di campo di membri diretti e tramite le dipendenze `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="ae111-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae111-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ae111-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="ae111-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ae111-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="ae111-106">[in] Numero di elementi nelle matrici `keyRefIds`, `valueRefIds` e `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="ae111-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="ae111-107">[in] Matrice di ID oggetto, ognuno dei quali include il valore `ObjectID` per l'elemento primario nella coppia di handle dipendente.</span><span class="sxs-lookup"><span data-stu-id="ae111-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="ae111-108">[in] Matrice di ID oggetto, ognuno dei quali include il valore `ObjectID` per l'elemento secondario nella coppia di handle dipendente.</span><span class="sxs-lookup"><span data-stu-id="ae111-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="ae111-109">`keyRefIds[i]` mantiene `valueRefIds[i]` attivo.</span><span class="sxs-lookup"><span data-stu-id="ae111-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="ae111-110">[in] Matrice di valori `GCHandleID` che fanno riferimento a un valore Integer contenente informazioni aggiuntive sulla radice di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="ae111-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="ae111-111">Nessuno dei valori `ObjectID` restituito dal metodo `ConditionalWeakTableElementReferences` è valido durante il callback stesso, poiché è possibile che il Garbage Collector stia spostando oggetti da posizioni precedenti a nuove posizioni.</span><span class="sxs-lookup"><span data-stu-id="ae111-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="ae111-112">I profiler non devono quindi tentare di verificare gli oggetti durante una chiamata a `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="ae111-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="ae111-113">In corrispondenza di `GarbageCollectionFinished`, tutti gli oggetti saranno stati spostati nelle nuove posizioni e sarà possibile verificarli.</span><span class="sxs-lookup"><span data-stu-id="ae111-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="ae111-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="ae111-114">Example</span></span>

<span data-ttu-id="ae111-115">Nell'esempio di codice riportato di seguito viene illustrato come implementare [ICorProfilerCallback5](icorprofilercallback5-interface.md) e utilizzare questo metodo.</span><span class="sxs-lookup"><span data-stu-id="ae111-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="ae111-116">Note</span><span class="sxs-lookup"><span data-stu-id="ae111-116">Remarks</span></span>

<span data-ttu-id="ae111-117">Un profiler per la .NET Framework 4,5 o versioni successive implementa l'interfaccia [ICorProfilerCallback5](icorprofilercallback5-interface.md) e registra le dipendenze specificate dal metodo `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="ae111-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="ae111-118">`ICorProfilerCallback5` fornisce il set completo di dipendenze tra gli oggetti attivi rappresentati dalle voci `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="ae111-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="ae111-119">Queste dipendenze e i riferimenti ai campi membro specificati dal metodo [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) consentono a un profiler gestito di generare l'oggetto grafico completo di oggetti attivi.</span><span class="sxs-lookup"><span data-stu-id="ae111-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae111-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ae111-120">Requirements</span></span>

<span data-ttu-id="ae111-121">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae111-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ae111-122">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae111-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ae111-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae111-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ae111-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ae111-124">See also</span></span>

- [<span data-ttu-id="ae111-125">Interfaccia ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="ae111-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
