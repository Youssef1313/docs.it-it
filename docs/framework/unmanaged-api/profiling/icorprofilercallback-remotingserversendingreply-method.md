---
title: Metodo ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: 1aa5a0d20ee87fe4362016ed0d7fa29ef786460e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430712"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="5f08c-102">Metodo ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="5f08c-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="5f08c-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span><span class="sxs-lookup"><span data-stu-id="5f08c-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f08c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5f08c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f08c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5f08c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="5f08c-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span><span class="sxs-lookup"><span data-stu-id="5f08c-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="5f08c-107">Remoting GUID cookies are active.</span><span class="sxs-lookup"><span data-stu-id="5f08c-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="5f08c-108">The channel succeeds in transmitting the message.</span><span class="sxs-lookup"><span data-stu-id="5f08c-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="5f08c-109">GUID cookies are active on the client-side process.</span><span class="sxs-lookup"><span data-stu-id="5f08c-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="5f08c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span><span class="sxs-lookup"><span data-stu-id="5f08c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="5f08c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="5f08c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f08c-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5f08c-112">Requirements</span></span>  
 <span data-ttu-id="5f08c-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f08c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f08c-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f08c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f08c-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f08c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f08c-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f08c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f08c-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5f08c-117">See also</span></span>

- [<span data-ttu-id="5f08c-118">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5f08c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
