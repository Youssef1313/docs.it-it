---
title: Metodo ICorDebugManagedCallback::EvalComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: d52c19f8663a776215241ddb16f3aa9ba00c0d36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137346"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="9c4ea-102">Metodo ICorDebugManagedCallback::EvalComplete</span><span class="sxs-lookup"><span data-stu-id="9c4ea-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="9c4ea-103">Notifica al debugger che la valutazione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="9c4ea-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4ea-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9c4ea-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c4ea-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="9c4ea-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9c4ea-106">in Puntatore a un oggetto ICorDebugAppDomain che rappresenta il dominio applicazione in cui è stata eseguita la valutazione.</span><span class="sxs-lookup"><span data-stu-id="9c4ea-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9c4ea-107">in Puntatore a un oggetto ICorDebugThread che rappresenta il thread in cui è stata eseguita la valutazione.</span><span class="sxs-lookup"><span data-stu-id="9c4ea-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="9c4ea-108">in Puntatore a un oggetto ICorDebugEval che rappresenta il codice che ha eseguito la valutazione.</span><span class="sxs-lookup"><span data-stu-id="9c4ea-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4ea-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9c4ea-109">Requirements</span></span>  
 <span data-ttu-id="9c4ea-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c4ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c4ea-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c4ea-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c4ea-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c4ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c4ea-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c4ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4ea-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c4ea-114">See also</span></span>

- [<span data-ttu-id="9c4ea-115">Interfaccia ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="9c4ea-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
