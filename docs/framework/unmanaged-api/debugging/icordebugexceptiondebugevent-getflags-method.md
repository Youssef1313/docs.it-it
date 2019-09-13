---
title: Metodo ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb92deee21c63c935454ff7c7c4e70be6f770436
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895006"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="469ef-102">Metodo ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="469ef-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="469ef-103">Ottiene un flag che indica se è possibile intercettare l'eccezione.</span><span class="sxs-lookup"><span data-stu-id="469ef-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469ef-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="469ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="469ef-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="469ef-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="469ef-106">out Puntatore a un valore [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) che indica se l'eccezione può essere intercettata.</span><span class="sxs-lookup"><span data-stu-id="469ef-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="469ef-107">Note</span><span class="sxs-lookup"><span data-stu-id="469ef-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="469ef-108">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="469ef-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="469ef-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="469ef-109">Requirements</span></span>  
 <span data-ttu-id="469ef-110">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="469ef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="469ef-111">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="469ef-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="469ef-112">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="469ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="469ef-113">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="469ef-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469ef-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="469ef-114">See also</span></span>

- [<span data-ttu-id="469ef-115">Interfaccia ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="469ef-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="469ef-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="469ef-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
