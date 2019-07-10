---
title: Metodo ICorDebugProcess5::GetTypeFields
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d413b17da0b6f241f9078bfeb3bd035d4d07a81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767624"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="3573e-102">Metodo ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="3573e-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="3573e-103">Vengono fornite informazioni sui campi che appartengono a un tipo.</span><span class="sxs-lookup"><span data-stu-id="3573e-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3573e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3573e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3573e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3573e-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="3573e-106">[in] L'identificatore del tipo le cui informazioni di campo viene recuperati.</span><span class="sxs-lookup"><span data-stu-id="3573e-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="3573e-107">[in] I numerosi [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) oggetti le cui informazioni di campo deve essere recuperato.</span><span class="sxs-lookup"><span data-stu-id="3573e-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="3573e-108">[out] Matrice di [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) gli oggetti che forniscono informazioni sui campi che appartengono al tipo.</span><span class="sxs-lookup"><span data-stu-id="3573e-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="3573e-109">[out] Un puntatore al numero di [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) oggetti inclusi nel `fields`.</span><span class="sxs-lookup"><span data-stu-id="3573e-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3573e-110">Note</span><span class="sxs-lookup"><span data-stu-id="3573e-110">Remarks</span></span>  
 <span data-ttu-id="3573e-111">Il `celt` parametro che specifica il numero di campi cui informazioni di campo, il metodo viene utilizzato per popolare `fields`, deve corrispondere al valore della `COR_TYPE_LAYOUT::numFields` campo.</span><span class="sxs-lookup"><span data-stu-id="3573e-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3573e-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3573e-112">Requirements</span></span>  
 <span data-ttu-id="3573e-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3573e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3573e-114">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3573e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3573e-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3573e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3573e-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3573e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3573e-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3573e-117">See also</span></span>

- [<span data-ttu-id="3573e-118">Interfaccia ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="3573e-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="3573e-119">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="3573e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
