---
title: Struttura COR_DEBUG_STEP_RANGE
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bda8079cff8f5e8fafade03a02c3dfe8798c5ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740779"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="65ac4-102">Struttura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="65ac4-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="65ac4-103">Contene le informazioni sugli offset per un intervallo di codice.</span><span class="sxs-lookup"><span data-stu-id="65ac4-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="65ac4-104">Questa struttura viene utilizzata per la [StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="65ac4-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ac4-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="65ac4-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="65ac4-106">Membri</span><span class="sxs-lookup"><span data-stu-id="65ac4-106">Members</span></span>  
  
|<span data-ttu-id="65ac4-107">Member</span><span class="sxs-lookup"><span data-stu-id="65ac4-107">Member</span></span>|<span data-ttu-id="65ac4-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="65ac4-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="65ac4-109">L'offset dell'inizio dell'intervallo.</span><span class="sxs-lookup"><span data-stu-id="65ac4-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="65ac4-110">L'offset della fine dell'intervallo.</span><span class="sxs-lookup"><span data-stu-id="65ac4-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65ac4-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="65ac4-111">Requirements</span></span>  
 <span data-ttu-id="65ac4-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ac4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ac4-113">**Intestazione:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="65ac4-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="65ac4-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65ac4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65ac4-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ac4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ac4-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="65ac4-116">See also</span></span>

- [<span data-ttu-id="65ac4-117">Metodo StepRange</span><span class="sxs-lookup"><span data-stu-id="65ac4-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="65ac4-118">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="65ac4-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="65ac4-119">Debug</span><span class="sxs-lookup"><span data-stu-id="65ac4-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
