---
title: Metodo ICorProfilerCallback::Shutdown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d63dd911a5f674a3ce0b02ec78de443c7aebf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747166"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="dec6f-102">Metodo ICorProfilerCallback::Shutdown</span><span class="sxs-lookup"><span data-stu-id="dec6f-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="dec6f-103">Notifica al profiler che l'applicazione è in corso l'arresto.</span><span class="sxs-lookup"><span data-stu-id="dec6f-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec6f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dec6f-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dec6f-105">Note</span><span class="sxs-lookup"><span data-stu-id="dec6f-105">Remarks</span></span>  
 <span data-ttu-id="dec6f-106">Il codice del profiler non è possibile chiamare i metodi del [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) dell'interfaccia dopo la `Shutdown` viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="dec6f-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="dec6f-107">Tutte le chiamate a `ICorProfilerInfo` metodi di causare un comportamento indefinito dopo il `Shutdown` restituzione del metodo.</span><span class="sxs-lookup"><span data-stu-id="dec6f-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="dec6f-108">Possono comunque si verificano determinati eventi non modificabile dopo l'arresto; il profiler deve prestare attenzione a restituire immediatamente quando ciò si verifica.</span><span class="sxs-lookup"><span data-stu-id="dec6f-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="dec6f-109">Il `Shutdown` metodo verrà chiamato solo se l'applicazione gestita che si sta profilando avviata come codice gestito (vale a dire, viene gestito il fotogramma iniziale sullo stack del processo).</span><span class="sxs-lookup"><span data-stu-id="dec6f-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="dec6f-110">Se l'applicazione avviata come codice non gestito, ma in un secondo momento un salto nel codice gestito, in modo da creare un'istanza di common language runtime (CLR), quindi `Shutdown` non verranno chiamati.</span><span class="sxs-lookup"><span data-stu-id="dec6f-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="dec6f-111">In questi casi, il profiler deve essere inclusa nella relativa libreria un `DllMain` routine che utilizzi il DLL_PROCESS_DETACH value per liberare le risorse ed eseguire l'elaborazione di pulizia dei dati, ad esempio lo svuotamento tracce su disco e così via.</span><span class="sxs-lookup"><span data-stu-id="dec6f-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="dec6f-112">In generale, il profiler deve far fronte ad arresti imprevisti.</span><span class="sxs-lookup"><span data-stu-id="dec6f-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="dec6f-113">Ad esempio, un processo venga arrestato di Win32 `TerminateProcess` metodo (dichiarato in winbase. h).</span><span class="sxs-lookup"><span data-stu-id="dec6f-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="dec6f-114">In altri casi, CLR si arresta in determinati thread gestiti (thread in background) senza il recapito dei messaggi di eliminazione per loro.</span><span class="sxs-lookup"><span data-stu-id="dec6f-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dec6f-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dec6f-115">Requirements</span></span>  
 <span data-ttu-id="dec6f-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dec6f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec6f-117">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dec6f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dec6f-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dec6f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dec6f-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dec6f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec6f-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dec6f-120">See also</span></span>

- [<span data-ttu-id="dec6f-121">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="dec6f-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="dec6f-122">Metodo Initialize</span><span class="sxs-lookup"><span data-stu-id="dec6f-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
