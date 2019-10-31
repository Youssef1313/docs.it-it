---
title: Metodo ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122639"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="6ed2e-102">Metodo ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="6ed2e-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="6ed2e-103">Ottiene le dimensioni, in byte, del modulo caricato.</span><span class="sxs-lookup"><span data-stu-id="6ed2e-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed2e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6ed2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed2e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="6ed2e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="6ed2e-106">[out] Puntatore al numero di byte nel modulo caricato.</span><span class="sxs-lookup"><span data-stu-id="6ed2e-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed2e-107">Note</span><span class="sxs-lookup"><span data-stu-id="6ed2e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ed2e-108">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6ed2e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed2e-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6ed2e-109">Requirements</span></span>  
 <span data-ttu-id="6ed2e-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed2e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed2e-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ed2e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed2e-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ed2e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed2e-113">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed2e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed2e-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6ed2e-114">See also</span></span>

- [<span data-ttu-id="6ed2e-115">Interfaccia ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="6ed2e-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="6ed2e-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="6ed2e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
