---
title: Metodo ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d831dd7a63c06327bb0f373b3be254401c6e2ee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780363"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="222a4-102">Metodo ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="222a4-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="222a4-103">Sostituisce il corpo Common Intermediate Language (CIL) del metodo.</span><span class="sxs-lookup"><span data-stu-id="222a4-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222a4-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="222a4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="222a4-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="222a4-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="222a4-106">[in] Dimensioni totali del nuovo codice CIL, incluse l'intestazione e tutte strutture successive al corpo.</span><span class="sxs-lookup"><span data-stu-id="222a4-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="222a4-107">[in] Puntatore alla nuova intestazione CIL.</span><span class="sxs-lookup"><span data-stu-id="222a4-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="222a4-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="222a4-108">Return Value</span></span>  
 <span data-ttu-id="222a4-109">Questo metodo restituisce gli HRESULT specifici seguenti.</span><span class="sxs-lookup"><span data-stu-id="222a4-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="222a4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="222a4-110">HRESULT</span></span>|<span data-ttu-id="222a4-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="222a4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="222a4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="222a4-112">S_OK</span></span>|<span data-ttu-id="222a4-113">Sostituzione completata correttamente.</span><span class="sxs-lookup"><span data-stu-id="222a4-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="222a4-114">Note</span><span class="sxs-lookup"><span data-stu-id="222a4-114">Remarks</span></span>  
 <span data-ttu-id="222a4-115">A differenza di [ICorProfilerInfo:: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metodo, il `SetILFunctionBody` metodo gestisce la memoria necessaria per il nuovo corpo CIL.</span><span class="sxs-lookup"><span data-stu-id="222a4-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="222a4-116">Ciò significa che il corpo CIL fornito dal profiler non deve essere allocato tramite il [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfaccia o allocata in un intervallo specifico.</span><span class="sxs-lookup"><span data-stu-id="222a4-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="222a4-117">ma può essere allocato in qualsiasi heap.</span><span class="sxs-lookup"><span data-stu-id="222a4-117">It can be allocated on any heap.</span></span> <span data-ttu-id="222a4-118">Il profiler può liberare la memoria usata per proprio corpo CIL dopo `SetILFunctionBody` restituisce.</span><span class="sxs-lookup"><span data-stu-id="222a4-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="222a4-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="222a4-119">Requirements</span></span>  
 <span data-ttu-id="222a4-120">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="222a4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="222a4-121">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="222a4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="222a4-122">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="222a4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="222a4-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="222a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222a4-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="222a4-124">See also</span></span>

- [<span data-ttu-id="222a4-125">Interfaccia ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="222a4-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
