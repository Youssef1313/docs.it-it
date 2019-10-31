---
title: Interfaccia ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 930101f6cd4ebb9215d6420f774b8e066c54a4f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095362"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="bdad1-102">Interfaccia ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="bdad1-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="bdad1-103">Estende logicamente l'interfaccia ICorDebugAssembly per fornire supporto per gli assembly contenitore e i relativi assembly contenuti.</span><span class="sxs-lookup"><span data-stu-id="bdad1-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdad1-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="bdad1-104">Methods</span></span>  
  
|<span data-ttu-id="bdad1-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="bdad1-105">Method</span></span>|<span data-ttu-id="bdad1-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bdad1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdad1-107">Metodo EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="bdad1-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="bdad1-108">Ottiene un enumeratore per gli assembly contenuti in questo assembly.</span><span class="sxs-lookup"><span data-stu-id="bdad1-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="bdad1-109">Metodo GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="bdad1-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="bdad1-110">Restituisce l'assembly del contenitore di questo oggetto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="bdad1-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdad1-111">Note</span><span class="sxs-lookup"><span data-stu-id="bdad1-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdad1-112">L'interfaccia è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdad1-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bdad1-113">Il tentativo di chiamare `QueryInterface` per recuperare un puntatore a interfaccia restituisce `E_NOINTERFACE` per gli scenari ICorDebug al di fuori di .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdad1-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdad1-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bdad1-114">Requirements</span></span>  
 <span data-ttu-id="bdad1-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdad1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdad1-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdad1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdad1-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdad1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdad1-118">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdad1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdad1-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bdad1-119">See also</span></span>

- [<span data-ttu-id="bdad1-120">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="bdad1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bdad1-121">Debug</span><span class="sxs-lookup"><span data-stu-id="bdad1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
