---
title: Metodo ICorProfilerInfo2::GetThreadStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8c18935069e4162236f99c411312087ce73bdc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782210"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="30c5b-102">Metodo ICorProfilerInfo2::GetThreadStaticAddress</span><span class="sxs-lookup"><span data-stu-id="30c5b-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="30c5b-103">Ottiene l'indirizzo del campo statico di thread specificato che è nell'ambito del thread specificato.</span><span class="sxs-lookup"><span data-stu-id="30c5b-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c5b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="30c5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30c5b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="30c5b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="30c5b-106">[in] L'ID della classe che contiene il campo statico thread richiesto.</span><span class="sxs-lookup"><span data-stu-id="30c5b-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="30c5b-107">[in] Il token di metadati per il campo statico thread richiesto.</span><span class="sxs-lookup"><span data-stu-id="30c5b-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="30c5b-108">[in] L'ID del thread che è l'ambito per i campi statici richiesti.</span><span class="sxs-lookup"><span data-stu-id="30c5b-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="30c5b-109">[out] Un puntatore all'indirizzo del campo statico che si trova all'interno del thread specificato.</span><span class="sxs-lookup"><span data-stu-id="30c5b-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c5b-110">Note</span><span class="sxs-lookup"><span data-stu-id="30c5b-110">Remarks</span></span>  
 <span data-ttu-id="30c5b-111">Il `GetThreadStaticAddress` metodo può restituire uno dei seguenti:</span><span class="sxs-lookup"><span data-stu-id="30c5b-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="30c5b-112">Un valore HRESULT CORPROF_E_DATAINCOMPLETE se il campo statico specificato non è stato assegnato un indirizzo nel contesto specificato.</span><span class="sxs-lookup"><span data-stu-id="30c5b-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="30c5b-113">Gli indirizzi di oggetti che possono trovarsi nell'heap di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30c5b-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="30c5b-114">Questi indirizzi potrebbero diventare non validi dopo l'operazione di garbage collection, quindi dopo i profiler di garbage collection non devono presupporre che le sono valide.</span><span class="sxs-lookup"><span data-stu-id="30c5b-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="30c5b-115">Prima del completamento, il costruttore di classe della classe `GetThreadStaticAddress` restituirà CORPROF_E_DATAINCOMPLETE per tutti i relativi campi statici, anche se alcuni dei campi statici potrebbero essere già stato inizializzato e oggetti radice del garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30c5b-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c5b-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="30c5b-116">Requirements</span></span>  
 <span data-ttu-id="30c5b-117">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30c5b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30c5b-118">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30c5b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30c5b-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30c5b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30c5b-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c5b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c5b-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="30c5b-121">See also</span></span>

- [<span data-ttu-id="30c5b-122">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="30c5b-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="30c5b-123">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="30c5b-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
