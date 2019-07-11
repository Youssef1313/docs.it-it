---
title: Metodo ICorProfilerCallback8::DynamicMethodJITCompilationFinished
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba9f9d4ee5f95def3dcd2d757517e225c826cb9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757996"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="1bc3f-102">Metodo ICorProfilerCallback8::DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="1bc3f-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="1bc3f-103">[Supportato in .NET Framework 4.7 e versioni successive]</span><span class="sxs-lookup"><span data-stu-id="1bc3f-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="1bc3f-104">Notifica al profiler ogni volta che è stata completata la compilazione JIT di un metodo dinamico.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc3f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1bc3f-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bc3f-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="1bc3f-106">Parameters</span></span>  
<span data-ttu-id="1bc3f-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="1bc3f-107">[in] `functionId`</span></span>  
<span data-ttu-id="1bc3f-108">L'identificatore della funzione in memoria per la quale JIT viene avviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="1bc3f-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="1bc3f-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="1bc3f-110">Un valore che indica se la compilazione JIT è riuscita.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="1bc3f-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="1bc3f-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="1bc3f-112">`true` per indicare che il blocco può causare il runtime di attesa per il thread chiamante restituire da questo callback; `false` per indicare che il blocco non avrà effetto il funzionamento del runtime.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="1bc3f-113">Note</span><span class="sxs-lookup"><span data-stu-id="1bc3f-113">Remarks</span></span>  

<span data-ttu-id="1bc3f-114">Questo callback viene attivato ogni volta che ha terminato la compilazione JIT di un metodo dinamico.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="1bc3f-115">Sono inclusi vari stub a livello di integrità e i metodi LCG.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="1bc3f-116">L'obiettivo consiste nel fornire gli autori di profiler con le informazioni necessarie per identificare il metodo compilato per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="1bc3f-117">`functionId` valori non possono essere usati per risolvere i relativi token di metadati, perché i metadati non dispongono di metodi dinamici.</span><span class="sxs-lookup"><span data-stu-id="1bc3f-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="1bc3f-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1bc3f-118">Requirements</span></span>  
 <span data-ttu-id="1bc3f-119">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bc3f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc3f-120">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bc3f-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bc3f-121">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bc3f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bc3f-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc3f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc3f-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1bc3f-123">See also</span></span>

- [<span data-ttu-id="1bc3f-124">Metodo DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="1bc3f-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="1bc3f-125">Interfaccia ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="1bc3f-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
