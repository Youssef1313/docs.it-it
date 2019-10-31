---
title: Metodo ICorDebugController::IsRunning
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: f24c07a654dc2345cb65226463573576a6fb3658
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125346"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="ace6a-102">Metodo ICorDebugController::IsRunning</span><span class="sxs-lookup"><span data-stu-id="ace6a-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="ace6a-103">Ottiene un valore che indica se i thread del processo sono attualmente in esecuzione liberamente.</span><span class="sxs-lookup"><span data-stu-id="ace6a-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace6a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ace6a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ace6a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ace6a-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="ace6a-106">out Puntatore a un valore `true` se i thread del processo vengono eseguiti liberamente; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="ace6a-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace6a-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ace6a-107">Requirements</span></span>  
 <span data-ttu-id="ace6a-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ace6a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace6a-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ace6a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ace6a-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ace6a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace6a-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace6a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace6a-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ace6a-112">See also</span></span>
