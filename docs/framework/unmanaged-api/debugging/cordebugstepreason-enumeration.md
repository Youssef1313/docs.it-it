---
title: Enumerazione CorDebugStepReason
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d9dc94689083d79858319387747eb9dafe8b2f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739569"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="f266c-102">Enumerazione CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="f266c-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="f266c-103">Indica l'esito di una singola istruzione.</span><span class="sxs-lookup"><span data-stu-id="f266c-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f266c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f266c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="f266c-105">Membri</span><span class="sxs-lookup"><span data-stu-id="f266c-105">Members</span></span>  
  
|<span data-ttu-id="f266c-106">Member</span><span class="sxs-lookup"><span data-stu-id="f266c-106">Member</span></span>|<span data-ttu-id="f266c-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f266c-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="f266c-108">L'esecuzione di istruzioni completata in genere, entro la stessa funzione.</span><span class="sxs-lookup"><span data-stu-id="f266c-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="f266c-109">L'esecuzione di istruzioni continuato in genere, dopo la funzione ha restituito.</span><span class="sxs-lookup"><span data-stu-id="f266c-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="f266c-110">L'esecuzione di istruzioni continuato in genere, all'inizio di una nuova funzione chiamata.</span><span class="sxs-lookup"><span data-stu-id="f266c-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="f266c-111">È stata generata un'eccezione e il controllo è stato passato a un filtro eccezioni.</span><span class="sxs-lookup"><span data-stu-id="f266c-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="f266c-112">È stata generata un'eccezione e il controllo è stato passato a un gestore di eccezioni.</span><span class="sxs-lookup"><span data-stu-id="f266c-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="f266c-113">Il controllo è stato passato a un intercettore.</span><span class="sxs-lookup"><span data-stu-id="f266c-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="f266c-114">Il thread sia stato chiuso prima del completamento dell'istruzione.</span><span class="sxs-lookup"><span data-stu-id="f266c-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f266c-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f266c-115">Requirements</span></span>  
 <span data-ttu-id="f266c-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f266c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f266c-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f266c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f266c-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f266c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f266c-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f266c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f266c-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f266c-120">See also</span></span>

- [<span data-ttu-id="f266c-121">Metodo StepComplete</span><span class="sxs-lookup"><span data-stu-id="f266c-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="f266c-122">Enumerazioni di debug</span><span class="sxs-lookup"><span data-stu-id="f266c-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
