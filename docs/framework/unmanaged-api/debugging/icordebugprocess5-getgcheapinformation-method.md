---
title: Metodo ICorDebugProcess5::GetGCHeapInformation
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e94034fcdcd8d86f34c61af30a7729a80c913fac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767344"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="bc9be-102">Metodo ICorDebugProcess5::GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="bc9be-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="bc9be-103">Fornisce informazioni generali sull'heap di garbage collection, ad esempio se è attualmente enumerabile.</span><span class="sxs-lookup"><span data-stu-id="bc9be-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9be-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bc9be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9be-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bc9be-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="bc9be-106">[out] Un puntatore a un [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valore che fornisce informazioni generali sull'heap di garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bc9be-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc9be-107">Note</span><span class="sxs-lookup"><span data-stu-id="bc9be-107">Remarks</span></span>  
 <span data-ttu-id="bc9be-108">Il `ICorDebugProcess5::GetGCHeapInformation` metodo deve essere chiamato prima dell'enumerazione dell'heap o heap singole aree per garantire che le strutture di garbage collection nel processo sono attualmente valide.</span><span class="sxs-lookup"><span data-stu-id="bc9be-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="bc9be-109">Non è possibile scorrere l'heap di garbage collection mentre è in corso una raccolta.</span><span class="sxs-lookup"><span data-stu-id="bc9be-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="bc9be-110">In caso contrario, l'enumerazione può acquisire le strutture di garbage collection che non sono validi.</span><span class="sxs-lookup"><span data-stu-id="bc9be-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9be-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bc9be-111">Requirements</span></span>  
 <span data-ttu-id="bc9be-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9be-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc9be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc9be-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc9be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc9be-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9be-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bc9be-116">See also</span></span>

- [<span data-ttu-id="bc9be-117">Interfaccia ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="bc9be-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="bc9be-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="bc9be-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
