---
title: Metodo ICorDebugEval::NewObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e4a09db3cedce7b0ae6049c7e550c0c3e21cc8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753179"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="f1283-102">Metodo ICorDebugEval::NewObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="f1283-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="f1283-103">Consente di allocare una nuova istanza dell'oggetto del tipo specificato, senza effettuare alcun tentativo di chiamare un metodo del costruttore.</span><span class="sxs-lookup"><span data-stu-id="f1283-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="f1283-104">Questo metodo è obsoleto in .NET Framework versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="f1283-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f1283-105">Uso [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) invece.</span><span class="sxs-lookup"><span data-stu-id="f1283-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1283-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f1283-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1283-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="f1283-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f1283-108">[in] Puntatore a un oggetto ICorDebugClass che rappresenta il tipo di oggetto da cui creare istanze.</span><span class="sxs-lookup"><span data-stu-id="f1283-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1283-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f1283-109">Requirements</span></span>  
 <span data-ttu-id="f1283-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1283-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1283-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1283-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1283-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1283-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1283-113">**Versioni di .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f1283-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1283-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1283-114">See also</span></span>

- [<span data-ttu-id="f1283-115">Metodo NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="f1283-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
