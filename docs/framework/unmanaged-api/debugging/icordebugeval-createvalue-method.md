---
title: Metodo ICorDebugEval::CreateValue
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ada3a06a2beb8f21c3e24665c0f1f8e7c48515f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752954"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="61605-102">Metodo ICorDebugEval::CreateValue</span><span class="sxs-lookup"><span data-stu-id="61605-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="61605-103">Crea un valore del tipo specificato, con un valore iniziale pari a zero o null.</span><span class="sxs-lookup"><span data-stu-id="61605-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="61605-104">Questo metodo è obsoleto in .NET Framework versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="61605-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="61605-105">Uso [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) invece.</span><span class="sxs-lookup"><span data-stu-id="61605-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61605-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="61605-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61605-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="61605-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="61605-108">[in] Valore di [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumerazione che specifica il tipo del valore.</span><span class="sxs-lookup"><span data-stu-id="61605-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="61605-109">[in] Puntatore a un [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) oggetto che specifica la classe del valore, se il tipo non è un tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="61605-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="61605-110">[out] Puntatore all'indirizzo di un oggetto "ICorDebugValue" che rappresenta il valore.</span><span class="sxs-lookup"><span data-stu-id="61605-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61605-111">Note</span><span class="sxs-lookup"><span data-stu-id="61605-111">Remarks</span></span>  
 <span data-ttu-id="61605-112">`CreateValue` Crea un `ICorDebugValue` oggetto del tipo specificato al solo scopo di utilizzo in una valutazione della funzione.</span><span class="sxs-lookup"><span data-stu-id="61605-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="61605-113">Questo oggetto di valore è utilizzabile per passare le costanti di utente come parametri.</span><span class="sxs-lookup"><span data-stu-id="61605-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="61605-114">Se il tipo del valore è un tipo primitivo, il valore iniziale è pari a zero o null.</span><span class="sxs-lookup"><span data-stu-id="61605-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="61605-115">Uso [ICorDebugGenericValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) per impostare il valore di un tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="61605-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="61605-116">Se il valore di `elementType` è ELEMENT_TYPE_CLASS, si ottiene un' "interfaccia ICorDebugReferenceValue" (restituite in `ppValue`) che rappresenta il riferimento all'oggetto null.</span><span class="sxs-lookup"><span data-stu-id="61605-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="61605-117">È possibile utilizzare questa oggetto passare null per una valutazione della funzione con parametri per riferimento oggetto.</span><span class="sxs-lookup"><span data-stu-id="61605-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="61605-118">Non è possibile impostare il `ICorDebugValue` ad alcun elemento; rimane sempre null.</span><span class="sxs-lookup"><span data-stu-id="61605-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61605-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="61605-119">Requirements</span></span>  
 <span data-ttu-id="61605-120">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61605-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61605-121">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61605-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61605-122">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61605-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61605-123">**Versioni di .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="61605-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61605-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="61605-124">See also</span></span>

- [<span data-ttu-id="61605-125">Metodo CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="61605-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="61605-126">ICorDebugEval (interfaccia)</span><span class="sxs-lookup"><span data-stu-id="61605-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
