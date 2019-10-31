---
title: Interfaccia ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138673"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="2b2e6-102">Interfaccia ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="2b2e6-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="2b2e6-103">Funge da estensione logica per l'interfaccia ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b2e6-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="2b2e6-104">Methods</span></span>  
  
|<span data-ttu-id="2b2e6-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="2b2e6-105">Method</span></span>|<span data-ttu-id="2b2e6-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2b2e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b2e6-107">Metodo GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="2b2e6-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="2b2e6-108">Ottiene una matrice di istanze di COR_ACTIVE_FUNCTION che contengono dati sulle funzioni attive nei frame di un thread.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="2b2e6-109">Metodo GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="2b2e6-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="2b2e6-110">Ottiene un identificatore di connessione per questo `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="2b2e6-111">Metodo GetTaskID</span><span class="sxs-lookup"><span data-stu-id="2b2e6-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="2b2e6-112">Ottiene un identificatore di attività per questo `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="2b2e6-113">Metodo GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="2b2e6-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="2b2e6-114">Ottiene l'identificatore del thread del sistema operativo per questo `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="2b2e6-115">Metodo InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="2b2e6-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="2b2e6-116">Consente a un debugger di intercettare l'eccezione corrente su un thread.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b2e6-117">Note</span><span class="sxs-lookup"><span data-stu-id="2b2e6-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b2e6-118">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="2b2e6-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b2e6-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2b2e6-119">Requirements</span></span>  
 <span data-ttu-id="2b2e6-120">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2e6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2e6-121">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b2e6-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b2e6-122">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b2e6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b2e6-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2e6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2e6-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2b2e6-124">See also</span></span>

- [<span data-ttu-id="2b2e6-125">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="2b2e6-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
