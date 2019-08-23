---
title: Metodo ICorDebugSymbolProvider::GetAssemblyImageMetadata
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964651"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="16569-102">Metodo ICorDebugSymbolProvider::GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="16569-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="16569-103">Restituisce i metadati da un assembly sottoposto a merge.</span><span class="sxs-lookup"><span data-stu-id="16569-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16569-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="16569-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16569-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="16569-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="16569-106">out Puntatore all'indirizzo di un oggetto [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) che contiene informazioni sulle dimensioni e sull'indirizzo dei metadati dell'assembly sottoposto a merge.</span><span class="sxs-lookup"><span data-stu-id="16569-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16569-107">Note</span><span class="sxs-lookup"><span data-stu-id="16569-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16569-108">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16569-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16569-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="16569-109">Requirements</span></span>  
 <span data-ttu-id="16569-110">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16569-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16569-111">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16569-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16569-112">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16569-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16569-113">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16569-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16569-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="16569-114">See also</span></span>

- [<span data-ttu-id="16569-115">Interfaccia ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="16569-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="16569-116">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="16569-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
