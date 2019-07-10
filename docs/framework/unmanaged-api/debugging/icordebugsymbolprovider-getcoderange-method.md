---
title: Metodo ICorDebugSymbolProvider::GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6d1f2bd903124773eaa20581f013bb41cf9cf99
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771493"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="224e3-102">Metodo ICorDebugSymbolProvider::GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="224e3-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="224e3-103">Ottiene l'indirizzo iniziale del metodo e la dimensione sulla base di un indirizzo RVA (Relative Virtual Address) in un metodo.</span><span class="sxs-lookup"><span data-stu-id="224e3-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224e3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="224e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="224e3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="224e3-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="224e3-106">[in] Indirizzo RVA (Relative Virtual Address) in un metodo</span><span class="sxs-lookup"><span data-stu-id="224e3-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="224e3-107">[out] Puntatore all'indirizzo iniziale del metodo.</span><span class="sxs-lookup"><span data-stu-id="224e3-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="224e3-108">Puntatore alla dimensione del codice del metodo (numero di byte del codice del metodo).</span><span class="sxs-lookup"><span data-stu-id="224e3-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="224e3-109">Note</span><span class="sxs-lookup"><span data-stu-id="224e3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="224e3-110">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="224e3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="224e3-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="224e3-111">Requirements</span></span>  
 <span data-ttu-id="224e3-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="224e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="224e3-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="224e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="224e3-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="224e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="224e3-115">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="224e3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224e3-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="224e3-116">See also</span></span>

- [<span data-ttu-id="224e3-117">Interfaccia ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="224e3-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="224e3-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="224e3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
