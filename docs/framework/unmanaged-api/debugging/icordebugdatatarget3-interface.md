---
title: Interfaccia ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee94e25201dee4999fd5acb2be44a80454e9efbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911406"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="1813f-102">Interfaccia ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1813f-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="1813f-103">Estende logicamente l'interfaccia [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) per fornire informazioni sui moduli caricati.</span><span class="sxs-lookup"><span data-stu-id="1813f-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="1813f-104">Metodo</span><span class="sxs-lookup"><span data-stu-id="1813f-104">Method</span></span>  
  
|<span data-ttu-id="1813f-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="1813f-105">Method</span></span>|<span data-ttu-id="1813f-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1813f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1813f-107">Metodo GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="1813f-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="1813f-108">Ottiene un elenco dei moduli caricati fino a questo momento.</span><span class="sxs-lookup"><span data-stu-id="1813f-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1813f-109">Note</span><span class="sxs-lookup"><span data-stu-id="1813f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1813f-110">Questa interfaccia è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1813f-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1813f-111">Se questa interfaccia viene implementata per scenari ICorDebug al di fuori di .NET Native, sarà ignorata da Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="1813f-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1813f-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1813f-112">Requirements</span></span>  
 <span data-ttu-id="1813f-113">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1813f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1813f-114">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1813f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1813f-115">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1813f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1813f-116">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1813f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1813f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1813f-117">See also</span></span>

- [<span data-ttu-id="1813f-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="1813f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1813f-119">Debug</span><span class="sxs-lookup"><span data-stu-id="1813f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
