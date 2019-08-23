---
title: Metodo ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c88d389f80b4b3d811d95f65acd41f294d076b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969084"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="8ff80-102">Metodo ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="8ff80-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="8ff80-103">Ottiene le dimensioni del buffer di memoria, espresse in byte.</span><span class="sxs-lookup"><span data-stu-id="8ff80-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff80-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8ff80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff80-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="8ff80-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="8ff80-106">[out] Puntatore alle dimensioni del buffer di memoria.</span><span class="sxs-lookup"><span data-stu-id="8ff80-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ff80-107">Note</span><span class="sxs-lookup"><span data-stu-id="8ff80-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ff80-108">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ff80-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff80-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8ff80-109">Requirements</span></span>  
 <span data-ttu-id="8ff80-110">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff80-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff80-111">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ff80-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ff80-112">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ff80-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ff80-113">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff80-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff80-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8ff80-114">See also</span></span>

- [<span data-ttu-id="8ff80-115">Interfaccia ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="8ff80-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="8ff80-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="8ff80-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
