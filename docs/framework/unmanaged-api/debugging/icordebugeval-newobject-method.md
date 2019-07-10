---
title: Metodo ICorDebugEval::NewObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 362c01e0b08145919793cec011a856f0090e5c47
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752998"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="5291f-102">Metodo ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="5291f-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="5291f-103">Consente di allocare una nuova istanza dell'oggetto e chiama il metodo costruttore specificato.</span><span class="sxs-lookup"><span data-stu-id="5291f-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="5291f-104">Questo metodo è obsoleto in .NET Framework versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="5291f-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5291f-105">Uso [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) invece.</span><span class="sxs-lookup"><span data-stu-id="5291f-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5291f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5291f-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5291f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5291f-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="5291f-108">[in] Il costruttore da chiamare.</span><span class="sxs-lookup"><span data-stu-id="5291f-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="5291f-109">[in] Dimensione della matrice `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="5291f-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="5291f-110">[in] Matrice di oggetti ICorDebugValue, ognuno dei quali rappresenta un argomento da passare al costruttore.</span><span class="sxs-lookup"><span data-stu-id="5291f-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5291f-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5291f-111">Requirements</span></span>  
 <span data-ttu-id="5291f-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5291f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5291f-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5291f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5291f-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5291f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5291f-115">**Versioni di .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="5291f-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5291f-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5291f-116">See also</span></span>

- [<span data-ttu-id="5291f-117">Metodo NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="5291f-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
