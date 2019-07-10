---
title: Metodo ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ab4905c55a1395e9ae5cba8343e6b832622005d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737638"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="ad531-102">Metodo ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="ad531-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="ad531-103">Ottiene un oggetto gestito da un puntatore a COM Callable Wrapper (CCW)</span><span class="sxs-lookup"><span data-stu-id="ad531-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad531-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ad531-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad531-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ad531-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="ad531-106">[in] Puntatore a COM Callable Wrapper (CCW)</span><span class="sxs-lookup"><span data-stu-id="ad531-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="ad531-107">[out] Un puntatore all'indirizzo di un oggetto "ICorDebugValue" che rappresenta l'oggetto gestito che corrisponde al puntatore CCW specificato.</span><span class="sxs-lookup"><span data-stu-id="ad531-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad531-108">Note</span><span class="sxs-lookup"><span data-stu-id="ad531-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad531-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ad531-109">Requirements</span></span>  
 <span data-ttu-id="ad531-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad531-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad531-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad531-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad531-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad531-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad531-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad531-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad531-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad531-114">See also</span></span>

- [<span data-ttu-id="ad531-115">Interfaccia ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="ad531-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="ad531-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="ad531-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
