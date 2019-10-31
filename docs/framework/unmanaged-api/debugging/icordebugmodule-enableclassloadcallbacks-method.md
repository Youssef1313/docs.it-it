---
title: Metodo ICorDebugModule::EnableClassLoadCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139224"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="b9603-102">Metodo ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="b9603-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="b9603-103">Controlla se i callback [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) vengono chiamati per questo modulo.</span><span class="sxs-lookup"><span data-stu-id="b9603-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9603-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b9603-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9603-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b9603-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="b9603-106">in Impostare questo valore su `true` per consentire al Common Language Runtime (CLR) di chiamare i metodi di `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` quando si verificano gli eventi associati.</span><span class="sxs-lookup"><span data-stu-id="b9603-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="b9603-107">Il valore predefinito è `false` per i moduli non dinamici.</span><span class="sxs-lookup"><span data-stu-id="b9603-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="b9603-108">Il valore è sempre `true` per i moduli dinamici e non può essere modificato.</span><span class="sxs-lookup"><span data-stu-id="b9603-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9603-109">Note</span><span class="sxs-lookup"><span data-stu-id="b9603-109">Remarks</span></span>  
 <span data-ttu-id="b9603-110">I callback `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` sono sempre abilitati per i moduli dinamici e non possono essere disabilitati.</span><span class="sxs-lookup"><span data-stu-id="b9603-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9603-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b9603-111">Requirements</span></span>  
 <span data-ttu-id="b9603-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9603-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9603-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9603-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9603-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9603-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9603-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9603-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9603-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9603-116">See also</span></span>
