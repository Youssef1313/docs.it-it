---
title: Metodo ICorProfilerInfo3::GetThreadStaticAddress2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f3ec6c2e0e452d3410437a7ec7cd45eb38cd5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779846"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="0e3de-102">Metodo ICorProfilerInfo3::GetThreadStaticAddress2</span><span class="sxs-lookup"><span data-stu-id="0e3de-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="0e3de-103">Ottiene l'indirizzo del campo statico a livello di thread specificato che è nell'ambito del dominio dell'applicazione e del thread specificati.</span><span class="sxs-lookup"><span data-stu-id="0e3de-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3de-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0e3de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e3de-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0e3de-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0e3de-106">[in] L'ID della classe che contiene il campo statico thread richiesto.</span><span class="sxs-lookup"><span data-stu-id="0e3de-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="0e3de-107">[in] Il token di metadati per il campo statico thread richiesto.</span><span class="sxs-lookup"><span data-stu-id="0e3de-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="0e3de-108">[in] ID del dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="0e3de-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="0e3de-109">[in] L'ID del thread che è l'ambito per i campi statici richiesti.</span><span class="sxs-lookup"><span data-stu-id="0e3de-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="0e3de-110">[out] Un puntatore all'indirizzo del campo statico che si trova all'interno del thread specificato.</span><span class="sxs-lookup"><span data-stu-id="0e3de-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e3de-111">Note</span><span class="sxs-lookup"><span data-stu-id="0e3de-111">Remarks</span></span>  
 <span data-ttu-id="0e3de-112">Il `GetThreadStaticAddress2` metodo può restituire uno dei seguenti:</span><span class="sxs-lookup"><span data-stu-id="0e3de-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="0e3de-113">Un valore HRESULT CORPROF_E_DATAINCOMPLETE se il campo statico specificato non è stato assegnato un indirizzo nel contesto specificato.</span><span class="sxs-lookup"><span data-stu-id="0e3de-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="0e3de-114">Gli indirizzi di oggetti che possono trovarsi nell'heap di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0e3de-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="0e3de-115">Questi indirizzi potrebbero diventare non validi dopo l'operazione di garbage collection, in modo che dopo l'operazione di garbage collection, i profiler non devono presupporre che siano validi.</span><span class="sxs-lookup"><span data-stu-id="0e3de-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="0e3de-116">Prima del completamento, il costruttore di classe della classe `GetThreadStaticAddress2` restituirà CORPROF_E_DATAINCOMPLETE per tutti i relativi campi statici, anche se alcuni dei campi statici potrebbero essere già stato inizializzato e oggetti radice del garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0e3de-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="0e3de-117">Il [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) metodo è simile al `GetThreadStaticAddress2` (metodo), ma non accetta un argomento di dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="0e3de-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e3de-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0e3de-118">Requirements</span></span>  
 <span data-ttu-id="0e3de-119">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e3de-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3de-120">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e3de-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e3de-121">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e3de-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e3de-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3de-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3de-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e3de-123">See also</span></span>

- [<span data-ttu-id="0e3de-124">Interfaccia ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="0e3de-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0e3de-125">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="0e3de-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0e3de-126">Profilatura</span><span class="sxs-lookup"><span data-stu-id="0e3de-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
