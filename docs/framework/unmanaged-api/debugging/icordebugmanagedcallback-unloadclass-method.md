---
title: Metodo ICorDebugManagedCallback::UnloadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 629a4850d47940633c8c69a7e464cfae315b3c56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761251"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="e396b-102">Metodo ICorDebugManagedCallback::UnloadClass</span><span class="sxs-lookup"><span data-stu-id="e396b-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="e396b-103">Notifica al debugger che è in corso lo scaricamento di una classe.</span><span class="sxs-lookup"><span data-stu-id="e396b-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e396b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e396b-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e396b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e396b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e396b-106">[in] Un puntatore a un oggetto ICorDebugAppDomain che rappresenta il dominio applicazione contenente la classe.</span><span class="sxs-lookup"><span data-stu-id="e396b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="e396b-107">[in] Un puntatore a un oggetto ICorDebugClass che rappresenta la classe.</span><span class="sxs-lookup"><span data-stu-id="e396b-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e396b-108">Note</span><span class="sxs-lookup"><span data-stu-id="e396b-108">Remarks</span></span>  
 <span data-ttu-id="e396b-109">La classe non dovrebbe essere specificata dopo questa chiamata.</span><span class="sxs-lookup"><span data-stu-id="e396b-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e396b-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e396b-110">Requirements</span></span>  
 <span data-ttu-id="e396b-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e396b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e396b-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e396b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e396b-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e396b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e396b-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e396b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e396b-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e396b-115">See also</span></span>

- [<span data-ttu-id="e396b-116">Metodo LoadClass</span><span class="sxs-lookup"><span data-stu-id="e396b-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="e396b-117">Interfaccia ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e396b-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
