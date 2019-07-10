---
title: Metodo ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38ff08fa7e7db986006c4e0e09b1ac9cf1be801e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767144"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="62342-102">Metodo ICorDebugProcess5::EnableNGENPolicy</span><span class="sxs-lookup"><span data-stu-id="62342-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="62342-103">Imposta un valore che determina la modalità di caricamento delle immagini native durante l'esecuzione con un debugger gestito in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="62342-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62342-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="62342-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62342-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="62342-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="62342-106">[in] Oggetto [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) costante che determina la modalità di caricamento delle immagini native durante l'esecuzione con un debugger gestito in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="62342-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62342-107">Note</span><span class="sxs-lookup"><span data-stu-id="62342-107">Remarks</span></span>  
 <span data-ttu-id="62342-108">Se i criteri sono impostati correttamente, il metodo restituisce `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="62342-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="62342-109">Se `ePolicy` è compreso nell'intervallo dei valori enumerati definito da [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), il metodo restituisce `E_INVALIDARG` e la chiamata al metodo non ha alcun effetto.</span><span class="sxs-lookup"><span data-stu-id="62342-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="62342-110">Se non è possibile aggiornare i criteri del generatore di immagini Native (Ngen.exe), il metodo restituisce `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="62342-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="62342-111">Il `ICorDebugProcess5::EnableNGenPolicy` metodo può essere chiamato in qualsiasi momento durante il ciclo di vita del processo.</span><span class="sxs-lookup"><span data-stu-id="62342-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="62342-112">È in vigore per tutti i moduli caricati dopo che il criterio è impostato il criterio.</span><span class="sxs-lookup"><span data-stu-id="62342-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62342-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="62342-113">Requirements</span></span>  
 <span data-ttu-id="62342-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62342-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62342-115">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62342-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62342-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62342-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62342-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62342-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62342-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="62342-118">See also</span></span>

- [<span data-ttu-id="62342-119">Interfaccia ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="62342-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="62342-120">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="62342-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="62342-121">Debug</span><span class="sxs-lookup"><span data-stu-id="62342-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
