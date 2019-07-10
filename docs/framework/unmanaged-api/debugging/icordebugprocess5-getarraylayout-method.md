---
title: Metodo ICorDebugProcess5::GetArrayLayout
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1afb87e063a18bd05bedf856f8b7ebdf0e47e91
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767427"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="9f2d7-102">Metodo ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="9f2d7-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="9f2d7-103">Fornisce informazioni sul layout dei tipi di matrice.</span><span class="sxs-lookup"><span data-stu-id="9f2d7-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f2d7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9f2d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f2d7-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="9f2d7-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="9f2d7-106">[in] Oggetto [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token che specifica la matrice il cui layout desiderato.</span><span class="sxs-lookup"><span data-stu-id="9f2d7-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="9f2d7-107">[out] Un puntatore a un [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) struttura che contiene informazioni sul layout della matrice in memoria.</span><span class="sxs-lookup"><span data-stu-id="9f2d7-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f2d7-108">Note</span><span class="sxs-lookup"><span data-stu-id="9f2d7-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f2d7-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9f2d7-109">Requirements</span></span>  
 <span data-ttu-id="9f2d7-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f2d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f2d7-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f2d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f2d7-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f2d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f2d7-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f2d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2d7-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f2d7-114">See also</span></span>

- [<span data-ttu-id="9f2d7-115">Interfaccia ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="9f2d7-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="9f2d7-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="9f2d7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
