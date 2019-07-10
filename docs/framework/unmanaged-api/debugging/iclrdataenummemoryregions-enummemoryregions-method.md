---
title: Metodo ICLRDataEnumMemoryRegions::EnumMemoryRegions
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 489ea22e17178398f53e103da04a47e8fe15a936
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738929"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="f792a-102">Metodo ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="f792a-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="f792a-103">Enumera aree specifiche della memoria.</span><span class="sxs-lookup"><span data-stu-id="f792a-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f792a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f792a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f792a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f792a-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="f792a-106">[in] Un puntatore a un [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) istanza che viene chiamato da questo metodo per ogni area di memoria in fase di enumerazione per notificare al debugger del risultato.</span><span class="sxs-lookup"><span data-stu-id="f792a-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="f792a-107">L'enumerazione delle aree di memoria continua anche se il callback indica un errore.</span><span class="sxs-lookup"><span data-stu-id="f792a-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="f792a-108">[in] Non utilizzato.</span><span class="sxs-lookup"><span data-stu-id="f792a-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="f792a-109">[in] Valore di [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumerazione che specifica le aree di memoria da enumerare.</span><span class="sxs-lookup"><span data-stu-id="f792a-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f792a-110">Note</span><span class="sxs-lookup"><span data-stu-id="f792a-110">Remarks</span></span>  
 <span data-ttu-id="f792a-111">Questo metodo Usa l'oggetto specificato [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) istanza per notificare i risultati al chiamante.</span><span class="sxs-lookup"><span data-stu-id="f792a-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f792a-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f792a-112">Requirements</span></span>  
 <span data-ttu-id="f792a-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f792a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f792a-114">**Intestazione:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f792a-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f792a-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f792a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f792a-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f792a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f792a-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f792a-117">See also</span></span>

- [<span data-ttu-id="f792a-118">Interfaccia ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="f792a-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
