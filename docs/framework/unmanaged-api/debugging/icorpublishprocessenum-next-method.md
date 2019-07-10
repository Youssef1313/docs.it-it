---
title: Metodo ICorPublishProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40a6376d4f4ffd09743441df1965d0a0f0d969b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764847"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="12c46-102">Metodo ICorPublishProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="12c46-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="12c46-103">Ottiene il numero di processi specificato dalla raccolta, a partire dalla posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="12c46-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c46-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="12c46-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12c46-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="12c46-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="12c46-106">[in] Il numero di processi da recuperare.</span><span class="sxs-lookup"><span data-stu-id="12c46-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="12c46-107">[out] Un puntatore alla matrice di recuperati [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) oggetti, ognuno dei quali rappresenta un processo.</span><span class="sxs-lookup"><span data-stu-id="12c46-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="12c46-108">[out] Puntatore al numero di processi effettivamente restituiti.</span><span class="sxs-lookup"><span data-stu-id="12c46-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="12c46-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="12c46-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c46-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="12c46-110">Requirements</span></span>  
 <span data-ttu-id="12c46-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c46-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c46-112">**Intestazione:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="12c46-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="12c46-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12c46-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12c46-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12c46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c46-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12c46-115">See also</span></span>

- [<span data-ttu-id="12c46-116">Interfaccia ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="12c46-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
