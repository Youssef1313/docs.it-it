---
title: Metodo ICorProfilerCallback::JITCachedFunctionSearchFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882d3b3c359724688c0fb8fe5e2b567f1d575e76
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782864"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="12338-102">Metodo ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="12338-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="12338-103">Notifica al profiler di completamento di una ricerca per una funzione che è stata compilata in precedenza usando il generatore di immagini Native (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="12338-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12338-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="12338-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12338-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="12338-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="12338-106">[in] L'ID della funzione per cui è stata eseguita la ricerca.</span><span class="sxs-lookup"><span data-stu-id="12338-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="12338-107">[in] Valore di [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumerazione che indica il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="12338-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12338-108">Note</span><span class="sxs-lookup"><span data-stu-id="12338-108">Remarks</span></span>  
 <span data-ttu-id="12338-109">In .NET Framework versione 2.0, il [JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` callback non verranno effettuati per tutte le funzioni nelle immagini NGen normali.</span><span class="sxs-lookup"><span data-stu-id="12338-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="12338-110">Solo le immagini NGen ottimizzate per un profiler genererà i callback per tutte le funzioni nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="12338-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="12338-111">Tuttavia, a causa del sovraccarico aggiuntivo, un profiler deve richiedere immagini NGen ottimizzata su profiler solo se intende usare questi callback per forzare una funzione di essere compilati just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="12338-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="12338-112">In caso contrario, il profiler deve usare una strategia lazy per raccogliere informazioni sulle funzioni.</span><span class="sxs-lookup"><span data-stu-id="12338-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12338-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="12338-113">Requirements</span></span>  
 <span data-ttu-id="12338-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12338-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12338-115">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12338-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12338-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12338-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12338-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12338-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12338-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12338-118">See also</span></span>

- [<span data-ttu-id="12338-119">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="12338-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
