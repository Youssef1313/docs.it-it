---
title: 'Metodo metodo icordebugsymbolprovider:: GetCodeRange'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 84bf545fedf3a6c7915d94fd0c2630268585b6eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138926"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="fd5a7-102">Metodo metodo icordebugsymbolprovider:: GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="fd5a7-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="fd5a7-103">Ottiene l'indirizzo iniziale del metodo e la dimensione sulla base di un indirizzo RVA (Relative Virtual Address) in un metodo.</span><span class="sxs-lookup"><span data-stu-id="fd5a7-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5a7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fd5a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd5a7-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="fd5a7-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="fd5a7-106">[in] Indirizzo RVA (Relative Virtual Address) in un metodo</span><span class="sxs-lookup"><span data-stu-id="fd5a7-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="fd5a7-107">[out] Puntatore all'indirizzo iniziale del metodo.</span><span class="sxs-lookup"><span data-stu-id="fd5a7-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="fd5a7-108">Puntatore alla dimensione del codice del metodo (numero di byte del codice del metodo).</span><span class="sxs-lookup"><span data-stu-id="fd5a7-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5a7-109">Note</span><span class="sxs-lookup"><span data-stu-id="fd5a7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd5a7-110">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd5a7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd5a7-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fd5a7-111">Requirements</span></span>  
 <span data-ttu-id="fd5a7-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd5a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd5a7-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd5a7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd5a7-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd5a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd5a7-115">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd5a7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5a7-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fd5a7-116">See also</span></span>

- [<span data-ttu-id="fd5a7-117">Interfaccia ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="fd5a7-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="fd5a7-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="fd5a7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
