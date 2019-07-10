---
title: Metodo ICorProfilerInfo::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b8afe10563d61e3ddab93e8d1b57eee4b6765c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766837"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="5493d-102">Metodo ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="5493d-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="5493d-103">Ottiene l'identità del contesto attualmente associato al thread specificato.</span><span class="sxs-lookup"><span data-stu-id="5493d-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5493d-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5493d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5493d-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5493d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5493d-106">[in] L'ID del thread.</span><span class="sxs-lookup"><span data-stu-id="5493d-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="5493d-107">[out] Un puntatore all'ID di contesto attualmente associato al thread specificato.</span><span class="sxs-lookup"><span data-stu-id="5493d-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="5493d-108">Se il thread non è attualmente associato alcun contesto, questa funzione restituirà CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="5493d-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5493d-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5493d-109">Requirements</span></span>  
 <span data-ttu-id="5493d-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5493d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5493d-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5493d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5493d-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5493d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5493d-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5493d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5493d-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5493d-114">See also</span></span>

- [<span data-ttu-id="5493d-115">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5493d-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
