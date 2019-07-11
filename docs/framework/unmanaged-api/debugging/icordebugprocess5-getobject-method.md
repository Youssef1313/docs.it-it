---
title: Metodo ICorDebugProcess5::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ec3dc37984228565b4a3fcc560d3857a1c1e46d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767335"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="5fb62-102">Metodo ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="5fb62-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="5fb62-103">Converte un indirizzo dell'oggetto a un oggetto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="5fb62-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb62-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5fb62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fb62-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5fb62-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="5fb62-106">[in] L'indirizzo dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5fb62-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="5fb62-107">[out] Un puntatore all'indirizzo di un oggetto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="5fb62-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fb62-108">Note</span><span class="sxs-lookup"><span data-stu-id="5fb62-108">Remarks</span></span>  
 <span data-ttu-id="5fb62-109">Se `addr` non punta a un oggetto gestito valido, il `GetObject` restituzione del metodo `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="5fb62-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb62-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5fb62-110">Requirements</span></span>  
 <span data-ttu-id="5fb62-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb62-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb62-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb62-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb62-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb62-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fb62-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb62-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb62-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5fb62-115">See also</span></span>

- [<span data-ttu-id="5fb62-116">Interfaccia ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="5fb62-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="5fb62-117">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="5fb62-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
