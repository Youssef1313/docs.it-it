---
title: Metodo ICorDebug::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77046745381d3ecc35c24d5af3f9181b9132e9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738157"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="3090c-102">Metodo ICorDebug::GetProcess</span><span class="sxs-lookup"><span data-stu-id="3090c-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="3090c-103">Ottiene un puntatore all'istanza di "ICorDebugProcess" per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="3090c-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3090c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3090c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3090c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3090c-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="3090c-106">[in] L'ID del processo.</span><span class="sxs-lookup"><span data-stu-id="3090c-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="3090c-107">[out] Un puntatore all'indirizzo di un `ICorDebugProcess` istanza per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="3090c-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3090c-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3090c-108">Requirements</span></span>  
 <span data-ttu-id="3090c-109">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3090c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3090c-110">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3090c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3090c-111">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3090c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3090c-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3090c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3090c-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3090c-113">See also</span></span>

- [<span data-ttu-id="3090c-114">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="3090c-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
