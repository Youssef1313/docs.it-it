---
title: Metodo ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abcbfaf803e930baaaf798986a585a7da5f9134d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780805"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="b540b-102">Metodo ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="b540b-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="b540b-103">Inizializza il thread corrente prima di profiler successive chiamate API sullo stesso thread, in modo tale deadlock può essere evitato.</span><span class="sxs-lookup"><span data-stu-id="b540b-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b540b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b540b-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b540b-105">Note</span><span class="sxs-lookup"><span data-stu-id="b540b-105">Remarks</span></span>  
 <span data-ttu-id="b540b-106">Si consiglia di chiamare `InitializeCurrentThread` in qualsiasi thread che chiama un profiler API mentre vi sono sospese thread.</span><span class="sxs-lookup"><span data-stu-id="b540b-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="b540b-107">Questo metodo viene utilizzato generalmente per i profiler di campionamento che creano i propri thread per chiamare il [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodo per eseguire stack descrive mentre il thread di destinazione è sospesa.</span><span class="sxs-lookup"><span data-stu-id="b540b-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="b540b-108">Chiamando `InitializeCurrentThread` una volta quando il profiler crea innanzitutto il thread di campionamento, i profiler possono assicurarsi che l'inizializzazione differita per ogni thread che CLR altrimenti verrebbero eseguite durante la prima chiamata a `DoStackSnapshot` può ora avvenire in modo sicuro quando nessun altro thread è sospeso.</span><span class="sxs-lookup"><span data-stu-id="b540b-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b540b-109">`InitializeCurrentThread` esegue l'inizializzazione in anticipo per completare le attività accettano blocchi e possono causare un deadlock.</span><span class="sxs-lookup"><span data-stu-id="b540b-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="b540b-110">Chiamare `InitializeCurrentThread` solo quando nessun thread sospesi.</span><span class="sxs-lookup"><span data-stu-id="b540b-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b540b-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b540b-111">Requirements</span></span>  
 <span data-ttu-id="b540b-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b540b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b540b-113">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b540b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b540b-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b540b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b540b-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b540b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b540b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b540b-116">See also</span></span>

- [<span data-ttu-id="b540b-117">Interfaccia ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b540b-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b540b-118">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="b540b-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b540b-119">Profilatura</span><span class="sxs-lookup"><span data-stu-id="b540b-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
