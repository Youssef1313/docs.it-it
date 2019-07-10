---
title: Funzione CreateAssemblyEnum
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778450"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="2d51e-102">Funzione CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="2d51e-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="2d51e-103">Ottiene un puntatore a un [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) istanza che può enumerare gli oggetti nell'assembly con l'oggetto specificato [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2d51e-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d51e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2d51e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d51e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="2d51e-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="2d51e-106">[out] Puntatore a una posizione di memoria che contiene l'oggetto richiesto `IAssemblyEnum` puntatore.</span><span class="sxs-lookup"><span data-stu-id="2d51e-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="2d51e-107">[in] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="2d51e-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2d51e-108">`pUnkReserved` deve essere un riferimento null.</span><span class="sxs-lookup"><span data-stu-id="2d51e-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="2d51e-109">[in] Il `IAssemblyName` dell'assembly richiesto.</span><span class="sxs-lookup"><span data-stu-id="2d51e-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="2d51e-110">Questo nome viene usato per filtrare l'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="2d51e-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="2d51e-111">Può essere null per enumerare tutti gli assembly nella global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2d51e-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2d51e-112">[in] Flag per la modifica del comportamento dell'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="2d51e-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="2d51e-113">Questo parametro contiene esattamente un bit di [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumerazione.</span><span class="sxs-lookup"><span data-stu-id="2d51e-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2d51e-114">[in] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="2d51e-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2d51e-115">`pvReserved` deve essere un riferimento null.</span><span class="sxs-lookup"><span data-stu-id="2d51e-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d51e-116">Note</span><span class="sxs-lookup"><span data-stu-id="2d51e-116">Remarks</span></span>  
 <span data-ttu-id="2d51e-117">Il `dwFlags` parametro contiene esattamente un bit di `ASM_CACHE_FLAGS` enumerazione.</span><span class="sxs-lookup"><span data-stu-id="2d51e-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d51e-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2d51e-118">Requirements</span></span>  
 <span data-ttu-id="2d51e-119">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d51e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d51e-120">**Intestazione:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2d51e-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2d51e-121">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2d51e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d51e-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d51e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d51e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2d51e-123">See also</span></span>

- [<span data-ttu-id="2d51e-124">Interfaccia IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="2d51e-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="2d51e-125">Interfaccia IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="2d51e-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2d51e-126">Funzioni statiche globali Fusion</span><span class="sxs-lookup"><span data-stu-id="2d51e-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
