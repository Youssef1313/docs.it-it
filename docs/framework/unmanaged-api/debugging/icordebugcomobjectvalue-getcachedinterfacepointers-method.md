---
title: Metodo ICorDebugComObjectValue::GetCachedInterfacePointers
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdbec0101de269b3d5b09e750d552c993a0198ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748477"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="d8b19-102">Metodo ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="d8b19-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="d8b19-103">Ottiene i puntatori a interfaccia raw memorizzato nella cache su corrente runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="d8b19-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b19-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d8b19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8b19-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d8b19-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="d8b19-106">[in] Un valore che indica se il metodo restituirà solo le interfacce di Windows Runtime (`IInspectable` interfacce) o tutte le interfacce COM presenti nella cache il runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="d8b19-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="d8b19-107">[in] Il numero di oggetti cui indirizzi devono essere recuperate.</span><span class="sxs-lookup"><span data-stu-id="d8b19-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d8b19-108">[out] Un puntatore al numero di `CORDB_ADDRESS` valori effettivamente restituiti nella `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="d8b19-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="d8b19-109">Un puntatore all'indirizzo iniziale di una matrice di `CORDB_ADDRESS` valori che contengono gli indirizzi di memorizzati nella cache gli oggetti dell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="d8b19-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8b19-110">Note</span><span class="sxs-lookup"><span data-stu-id="d8b19-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8b19-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d8b19-111">Requirements</span></span>  
 <span data-ttu-id="d8b19-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8b19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b19-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8b19-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8b19-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8b19-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8b19-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b19-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d8b19-116">See also</span></span>

- [<span data-ttu-id="d8b19-117">Interfaccia ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="d8b19-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d8b19-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="d8b19-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
