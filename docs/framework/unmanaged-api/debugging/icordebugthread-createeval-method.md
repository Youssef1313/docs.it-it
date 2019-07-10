---
title: Metodo ICorDebugThread::CreateEval
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41bd4c0bb4e84b6d6f267e24808baafa57f71882
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771114"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="1a4cd-102">Metodo ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="1a4cd-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="1a4cd-103">Crea un oggetto ICorDebugEval che raccoglie ed espone la funzionalità di ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1a4cd-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a4cd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1a4cd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a4cd-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="1a4cd-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="1a4cd-106">[out] Un puntatore all'indirizzo di un `ICorDebugEval` oggetto raccoglie ed espone la funzionalità di questo thread.</span><span class="sxs-lookup"><span data-stu-id="1a4cd-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a4cd-107">Note</span><span class="sxs-lookup"><span data-stu-id="1a4cd-107">Remarks</span></span>  
 <span data-ttu-id="1a4cd-108">L'oggetto valutazione effettuerà il push una catena di nuovo nel thread prima di eseguire il calcolo.</span><span class="sxs-lookup"><span data-stu-id="1a4cd-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="1a4cd-109">In questo modo si interromperà il calcolo viene eseguito sul thread fino al completamento della versione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="1a4cd-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a4cd-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1a4cd-110">Requirements</span></span>  
 <span data-ttu-id="1a4cd-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a4cd-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a4cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a4cd-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a4cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a4cd-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
