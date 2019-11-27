---
title: Metodo ICorProfilerFunctionControl::SetCodegenFlags
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 88c9f552b73af69ea4e1f64b75ed74ea762dcdfb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429935"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="985f7-102">Metodo ICorProfilerFunctionControl::SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="985f7-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="985f7-103">Imposta uno o più flag dall'enumerazione [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) per controllare la generazione di codice per una funzione JIT (just-in-Time) ricompilata.</span><span class="sxs-lookup"><span data-stu-id="985f7-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985f7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="985f7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="985f7-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="985f7-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="985f7-106">in Uno o più flag dall'enumerazione [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="985f7-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="985f7-107">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="985f7-107">Remarks</span></span>  
 <span data-ttu-id="985f7-108">Il profiler ottiene un'istanza di questa interfaccia tramite il callback [ICorProfilerCallback4:: GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="985f7-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="985f7-109">`SetCodegenFlags` consente al profiler di controllare la generazione del codice per la funzione ricompilata.</span><span class="sxs-lookup"><span data-stu-id="985f7-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="985f7-110">Come per tutti gli altri parametri di ricompilazione JIT, i flag di generazione del codice si applicano a tutte le istanze della funzione.</span><span class="sxs-lookup"><span data-stu-id="985f7-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="985f7-111">Il compilatore JIT considera questi flag di compilazione, insieme ad altri flag specificati da altre origini, durante la compilazione di una funzione.</span><span class="sxs-lookup"><span data-stu-id="985f7-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="985f7-112">Le altre origini includono il debugger, i flag globali impostati dal profiler all'avvio tramite il metodo [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) (con i valori `COR_PRF_DISABLE_INLINING` e `COR_PRF_DISABLE_OPTIMIZATIONS`) e il callback [ICorProfilerCallback:: JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) del profiler.</span><span class="sxs-lookup"><span data-stu-id="985f7-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="985f7-113">Il compilatore JIT fornisce la precedenza a un'origine che richiede la quantità minima di ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="985f7-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="985f7-114">Se, ad esempio, il profiler specifica `COR_PRF_DISABLE_INLINING` all'avvio, ma non specifica `COR_PRF_CODEGEN_DISABLE_INLINING` nel callback [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) , l'inlining è ancora disabilitato.</span><span class="sxs-lookup"><span data-stu-id="985f7-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="985f7-115">Analogamente, se il profiler non specifica `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, ma quindi Disabilita l'incorporamento tramite il callback [ICorProfilerCallback:: JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) , l'incorporamento è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="985f7-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="985f7-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="985f7-116">Requirements</span></span>  
 <span data-ttu-id="985f7-117">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="985f7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985f7-118">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="985f7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="985f7-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="985f7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="985f7-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985f7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985f7-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="985f7-121">See also</span></span>

- [<span data-ttu-id="985f7-122">Interfaccia ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="985f7-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
