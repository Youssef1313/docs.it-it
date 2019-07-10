---
title: Metodo ICorDebugObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a1c0f7deb2ef24893530797b4507e2dcc540ad2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757043"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="f4774-102">Metodo ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f4774-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="f4774-103">Ottiene gli indirizzi virtuali relativi (RVA) del numero specificato di oggetti dall'enumerazione, iniziando in corrispondenza della posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="f4774-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4774-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f4774-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4774-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f4774-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f4774-106">[in] Numero di oggetti da recuperare.</span><span class="sxs-lookup"><span data-stu-id="f4774-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f4774-107">[out] Una matrice di puntatori, ognuno dei quali punta a un oggetto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="f4774-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f4774-108">[out] Puntatore al numero di oggetti effettivamente restituiti.</span><span class="sxs-lookup"><span data-stu-id="f4774-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="f4774-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="f4774-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4774-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f4774-110">Requirements</span></span>  
 <span data-ttu-id="f4774-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4774-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4774-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4774-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4774-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4774-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4774-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4774-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4774-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f4774-115">See also</span></span>
