---
title: Metodo ICorDebugManagedCallback2::MDANotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011932af6f4b058906c19566e4c1abe96b409db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762091"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="a2634-102">Metodo ICorDebugManagedCallback2::MDANotification</span><span class="sxs-lookup"><span data-stu-id="a2634-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="a2634-103">Fornisce la notifica che l'esecuzione di codice ha rilevato un assistente al debug gestito (MDA) nell'applicazione in fase di debug.</span><span class="sxs-lookup"><span data-stu-id="a2634-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2634-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a2634-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2634-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a2634-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="a2634-106">[in] Puntatore a un'interfaccia ICorDebugController che espone il processo o un dominio dell'applicazione in cui si è verificato l'assistente al debug gestito.</span><span class="sxs-lookup"><span data-stu-id="a2634-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="a2634-107">Un debugger non deve fare supposizioni sul fatto che il controller è un processo o un dominio applicazione, anche se sempre possibile eseguire una query l'interfaccia per effettuare una determinazione.</span><span class="sxs-lookup"><span data-stu-id="a2634-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a2634-108">[in] Un puntatore a un'interfaccia ICorDebugThread che espone il thread gestito in cui si è verificato l'evento di debug.</span><span class="sxs-lookup"><span data-stu-id="a2634-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="a2634-109">Se si è verificato l'assistente al debug gestito in una funzione non gestita del thread, il valore di `pThread` sarà null.</span><span class="sxs-lookup"><span data-stu-id="a2634-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="a2634-110">È necessario ottenere l'ID del thread del sistema operativo (OS) direttamente l'oggetto Assistente al debug gestito.</span><span class="sxs-lookup"><span data-stu-id="a2634-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="a2634-111">[in] Un puntatore a un [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interfaccia che espone le informazioni di assistente al debug gestito.</span><span class="sxs-lookup"><span data-stu-id="a2634-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2634-112">Note</span><span class="sxs-lookup"><span data-stu-id="a2634-112">Remarks</span></span>  
 <span data-ttu-id="a2634-113">Un assistente al debug gestito è un avviso euristico e non richiede alcuna azione esplicita del debugger, ad eccezione di chiamata [ICorDebugController](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) per riprendere l'esecuzione dell'applicazione che viene eseguito il debug.</span><span class="sxs-lookup"><span data-stu-id="a2634-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="a2634-114">Common language runtime (CLR) può determinare quali assistenti al debug gestito vengono attivati e quali dati si trovano in qualsiasi dato assistente al debug gestito in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="a2634-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="a2634-115">Di conseguenza, i debugger non devono compilare tutte le funzionalità che richiedono i modelli di assistente al debug gestito specifici.</span><span class="sxs-lookup"><span data-stu-id="a2634-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="a2634-116">Assistenti al debug gestito può essere accodate e generati subito dopo l'assistente al debug gestito viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="a2634-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="a2634-117">Questo problema può verificarsi se il runtime deve rimanere in attesa fino a raggiungere un punto sicuro per l'attivazione l'assistente al debug gestito, anziché attivato l'assistente al debug gestito quando lo rileva.</span><span class="sxs-lookup"><span data-stu-id="a2634-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="a2634-118">Significa anche che il runtime può attivare un numero di assistenti al debug gestito in un unico set di callback in coda (simile a un'operazione di evento "Collega").</span><span class="sxs-lookup"><span data-stu-id="a2634-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="a2634-119">Un debugger deve rilasciare il riferimento a un `ICorDebugMDA` immediatamente dopo la restituzione dall'istanza il `MDANotification` callback per consentire a CLR riciclare la memoria utilizzata da un assistente al debug gestito.</span><span class="sxs-lookup"><span data-stu-id="a2634-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="a2634-120">Rilasciare l'istanza può migliorare le prestazioni se si stanno attivando molti assistenti al debug gestito.</span><span class="sxs-lookup"><span data-stu-id="a2634-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2634-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a2634-121">Requirements</span></span>  
 <span data-ttu-id="a2634-122">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2634-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2634-123">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2634-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2634-124">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2634-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2634-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2634-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2634-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a2634-126">See also</span></span>

- [<span data-ttu-id="a2634-127">Diagnostica degli errori tramite gli assistenti al debug gestito</span><span class="sxs-lookup"><span data-stu-id="a2634-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a2634-128">Interfaccia ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="a2634-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a2634-129">Interfaccia ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a2634-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
