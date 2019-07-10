---
title: Enumerazione CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740380"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="6b011-102">Enumerazione CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="6b011-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="6b011-103">Specifica i motivi che possono causare il blocco di un thread su un oggetto specifico.</span><span class="sxs-lookup"><span data-stu-id="6b011-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b011-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6b011-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="6b011-105">Membri</span><span class="sxs-lookup"><span data-stu-id="6b011-105">Members</span></span>  
  
|<span data-ttu-id="6b011-106">Member</span><span class="sxs-lookup"><span data-stu-id="6b011-106">Member</span></span>|<span data-ttu-id="6b011-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6b011-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="6b011-108">Solo per uso interno.</span><span class="sxs-lookup"><span data-stu-id="6b011-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="6b011-109">Un thread sta tentando di acquisire la sezione critica che è associata il blocco del monitoraggio in un oggetto.</span><span class="sxs-lookup"><span data-stu-id="6b011-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="6b011-110">In genere, ciò si verifica quando si chiama uno dei <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> o <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metodi.</span><span class="sxs-lookup"><span data-stu-id="6b011-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="6b011-111">Un thread è in attesa dell'evento associato a un blocco di monitoraggio per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="6b011-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="6b011-112">In genere, ciò si verifica quando si chiama uno dei <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metodi.</span><span class="sxs-lookup"><span data-stu-id="6b011-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b011-113">Note</span><span class="sxs-lookup"><span data-stu-id="6b011-113">Remarks</span></span>  
 <span data-ttu-id="6b011-114">Quando la `BLOCKING_MONITOR_CRITICAL_SECTION` oppure `BLOCKING_MONITOR_EVENT` membro viene utilizzato un [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struttura, il `pBlockingObject` membro della struttura punta a un'interfaccia "ICorDebugValue" che rappresenta l'oggetto che viene viene immesso .</span><span class="sxs-lookup"><span data-stu-id="6b011-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="6b011-115">È inoltre garantito per implementare il [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="6b011-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b011-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6b011-116">Requirements</span></span>  
 <span data-ttu-id="6b011-117">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b011-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b011-118">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b011-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b011-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b011-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b011-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b011-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b011-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6b011-121">See also</span></span>

- [<span data-ttu-id="6b011-122">Enumerazioni di debug</span><span class="sxs-lookup"><span data-stu-id="6b011-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="6b011-123">Debug</span><span class="sxs-lookup"><span data-stu-id="6b011-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
