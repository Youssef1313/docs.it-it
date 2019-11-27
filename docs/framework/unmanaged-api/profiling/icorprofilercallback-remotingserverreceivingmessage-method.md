---
title: Metodo ICorProfilerCallback::RemotingServerReceivingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 2c2eb7d0dc04d813b1ce91fb1acf4b171f244592
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445753"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="2267a-102">Metodo ICorProfilerCallback::RemotingServerReceivingMessage</span><span class="sxs-lookup"><span data-stu-id="2267a-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="2267a-103">Notifica al profiler che il processo ha ricevuto una chiamata al metodo remoto o una richiesta di attivazione.</span><span class="sxs-lookup"><span data-stu-id="2267a-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2267a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2267a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2267a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="2267a-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="2267a-106">in Valore che corrisponderà al valore fornito in [ICorProfilerCallback:: RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) in queste condizioni:</span><span class="sxs-lookup"><span data-stu-id="2267a-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="2267a-107">I cookie GUID di comunicazione remota sono attivi.</span><span class="sxs-lookup"><span data-stu-id="2267a-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="2267a-108">Il canale riesce a trasmettere il messaggio.</span><span class="sxs-lookup"><span data-stu-id="2267a-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="2267a-109">I cookie GUID sono attivi sul processo sul lato client.</span><span class="sxs-lookup"><span data-stu-id="2267a-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="2267a-110">Questo consente di associare facilmente le chiamate remote e la creazione di uno stack di chiamate logico.</span><span class="sxs-lookup"><span data-stu-id="2267a-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="2267a-111">in Valore `true` se la chiamata è asincrona. in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="2267a-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2267a-112">Note</span><span class="sxs-lookup"><span data-stu-id="2267a-112">Remarks</span></span>  
 <span data-ttu-id="2267a-113">Se la richiesta di messaggio è asincrona, la richiesta può essere gestita da qualsiasi thread arbitrario.</span><span class="sxs-lookup"><span data-stu-id="2267a-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2267a-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2267a-114">Requirements</span></span>  
 <span data-ttu-id="2267a-115">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2267a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2267a-116">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2267a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2267a-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2267a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2267a-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2267a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2267a-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2267a-119">See also</span></span>

- [<span data-ttu-id="2267a-120">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2267a-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
