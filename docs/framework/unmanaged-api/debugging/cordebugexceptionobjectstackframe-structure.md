---
title: Struttura CorDebugExceptionObjectStackFrame
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd2add7e96a8edaff8509563ae1846e80132001
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740093"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="dba35-102">Struttura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="dba35-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="dba35-103">Rappresenta le informazioni sullo stack frame da un oggetto di eccezione.</span><span class="sxs-lookup"><span data-stu-id="dba35-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba35-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dba35-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="dba35-105">Membri</span><span class="sxs-lookup"><span data-stu-id="dba35-105">Members</span></span>  
  
|<span data-ttu-id="dba35-106">Member</span><span class="sxs-lookup"><span data-stu-id="dba35-106">Member</span></span>|<span data-ttu-id="dba35-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dba35-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="dba35-108">Un puntatore all'oggetto ICorDebugModule per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="dba35-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="dba35-109">Il valore del puntatore all'istruzione (EIP/RIP) per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="dba35-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="dba35-110">Il token del metodo per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="dba35-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="dba35-111">Un valore che indica se il frame è ultimo frame di un'eccezione esterna.</span><span class="sxs-lookup"><span data-stu-id="dba35-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba35-112">Note</span><span class="sxs-lookup"><span data-stu-id="dba35-112">Remarks</span></span>  
 <span data-ttu-id="dba35-113">Il chiamante deve rilasciare il puntatore all'oggetto ICorDebugModule una volta non è più in uso.</span><span class="sxs-lookup"><span data-stu-id="dba35-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba35-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dba35-114">Requirements</span></span>  
 <span data-ttu-id="dba35-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba35-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba35-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba35-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba35-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba35-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba35-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba35-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dba35-119">See also</span></span>

- [<span data-ttu-id="dba35-120">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="dba35-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="dba35-121">Debug</span><span class="sxs-lookup"><span data-stu-id="dba35-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
