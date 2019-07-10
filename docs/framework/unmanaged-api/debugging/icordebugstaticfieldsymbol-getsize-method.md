---
title: Metodo ICorDebugStaticFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a30778a287b4115df552444549a92c006288005
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760758"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="977e6-102">Metodo ICorDebugStaticFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="977e6-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="977e6-103">Ottiene le dimensioni in byte del campo statico</span><span class="sxs-lookup"><span data-stu-id="977e6-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977e6-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="977e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="977e6-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="977e6-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="977e6-106">[out] Puntatore alla lunghezza del campo.</span><span class="sxs-lookup"><span data-stu-id="977e6-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="977e6-107">Note</span><span class="sxs-lookup"><span data-stu-id="977e6-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="977e6-108">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="977e6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977e6-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="977e6-109">Requirements</span></span>  
 <span data-ttu-id="977e6-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="977e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977e6-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="977e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="977e6-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="977e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="977e6-113">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="977e6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977e6-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="977e6-114">See also</span></span>

- [<span data-ttu-id="977e6-115">Interfaccia ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="977e6-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="977e6-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="977e6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
