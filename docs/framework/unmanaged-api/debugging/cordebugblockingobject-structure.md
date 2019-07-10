---
title: Struttura CorDebugBlockingObject
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83dac3b9b2ac396cdef19695fcce0f7e20485a50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740401"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="030dd-102">Struttura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="030dd-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="030dd-103">Definisce un oggetto che blocca un thread e il motivo specifico che il thread è bloccato.</span><span class="sxs-lookup"><span data-stu-id="030dd-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030dd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="030dd-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="030dd-105">Membri</span><span class="sxs-lookup"><span data-stu-id="030dd-105">Members</span></span>  
  
|<span data-ttu-id="030dd-106">Member</span><span class="sxs-lookup"><span data-stu-id="030dd-106">Member</span></span>|<span data-ttu-id="030dd-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="030dd-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="030dd-108">L'oggetto su cui sta bloccando il thread.</span><span class="sxs-lookup"><span data-stu-id="030dd-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="030dd-109">Questo oggetto è valido solo per la durata dello stato di sincronizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="030dd-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="030dd-110">Se due thread sono bloccati nello stesso oggetto nello stesso stato sincronizzato, si sarebbe potuto prevedere la [GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) per restituire lo stesso valore.</span><span class="sxs-lookup"><span data-stu-id="030dd-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="030dd-111">Tuttavia, le interfacce possono o potrebbero non essere puntatore equivalente.</span><span class="sxs-lookup"><span data-stu-id="030dd-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="030dd-112">Il numero di millisecondi prima che l'operazione di blocco sarà previsto un timeout o il valore infinito, a indicare che si verifica alcun timeout. Il valore di timeout specifica la lunghezza totale del tempo per l'operazione di blocco, non l'ora in cui resta ancora da fare.</span><span class="sxs-lookup"><span data-stu-id="030dd-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="030dd-113">Il motivo è che il thread è bloccato su questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="030dd-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="030dd-114">Note</span><span class="sxs-lookup"><span data-stu-id="030dd-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030dd-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="030dd-115">Requirements</span></span>  
 <span data-ttu-id="030dd-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="030dd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="030dd-117">**Intestazione:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="030dd-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="030dd-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="030dd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="030dd-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="030dd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030dd-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="030dd-120">See also</span></span>

- [<span data-ttu-id="030dd-121">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="030dd-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="030dd-122">Debug</span><span class="sxs-lookup"><span data-stu-id="030dd-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
