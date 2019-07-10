---
title: Metodo ICorDebugMDA::GetOSThreadId
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d676e0fad33ca994b2e5bcd7adf269e306cb55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761929"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="45832-102">Metodo ICorDebugMDA::GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="45832-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="45832-103">Ottiene l'identificatore del thread del sistema operativo (OS) su cui l'assistente al debug gestito (MDA) rappresentato da [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="45832-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45832-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="45832-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45832-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="45832-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="45832-106">[out] Un puntatore all'identificatore del thread del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="45832-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45832-107">Note</span><span class="sxs-lookup"><span data-stu-id="45832-107">Remarks</span></span>  
 <span data-ttu-id="45832-108">Il thread del sistema operativo verrà usato invece di un oggetto ICorDebugThread per consentire situazioni in cui un assistente al debug gestito viene attivato su un thread nativo o su un thread gestito che non ha ancora inserito codice gestito.</span><span class="sxs-lookup"><span data-stu-id="45832-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45832-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="45832-109">Requirements</span></span>  
 <span data-ttu-id="45832-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45832-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45832-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45832-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45832-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45832-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45832-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45832-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45832-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45832-114">See also</span></span>

- [<span data-ttu-id="45832-115">Interfaccia ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="45832-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="45832-116">Diagnostica degli errori tramite gli assistenti al debug gestito</span><span class="sxs-lookup"><span data-stu-id="45832-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
