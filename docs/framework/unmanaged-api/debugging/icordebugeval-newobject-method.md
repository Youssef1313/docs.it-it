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
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137614"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="7fa33-102">Metodo ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="7fa33-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="7fa33-103">Alloca una nuova istanza dell'oggetto e chiama il metodo del costruttore specificato.</span><span class="sxs-lookup"><span data-stu-id="7fa33-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="7fa33-104">Questo metodo è obsoleto nella versione .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7fa33-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7fa33-105">Usare invece [ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7fa33-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa33-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7fa33-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fa33-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="7fa33-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="7fa33-108">in Costruttore da chiamare.</span><span class="sxs-lookup"><span data-stu-id="7fa33-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="7fa33-109">[in] Dimensione della matrice `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="7fa33-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="7fa33-110">in Matrice di oggetti ICorDebugValue, ognuno dei quali rappresenta un argomento da passare al costruttore.</span><span class="sxs-lookup"><span data-stu-id="7fa33-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fa33-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7fa33-111">Requirements</span></span>  
 <span data-ttu-id="7fa33-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa33-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa33-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fa33-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fa33-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fa33-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fa33-115">**Versioni .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="7fa33-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa33-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7fa33-116">See also</span></span>

- [<span data-ttu-id="7fa33-117">Metodo NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="7fa33-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
