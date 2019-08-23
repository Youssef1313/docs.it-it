---
title: Interfaccia ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd7a5f630bcf97277a4f98f2408ecaf04883fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916982"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="622bd-102">Interfaccia ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="622bd-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="622bd-103">Fornisce informazioni su un assembly unito.</span><span class="sxs-lookup"><span data-stu-id="622bd-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="622bd-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="622bd-104">Methods</span></span>  
  
|<span data-ttu-id="622bd-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="622bd-105">Method</span></span>|<span data-ttu-id="622bd-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="622bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="622bd-107">Metodo GetCulture</span><span class="sxs-lookup"><span data-stu-id="622bd-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="622bd-108">Ottiene la stringa del nome delle impostazioni cultura dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="622bd-109">Metodo GetIndex</span><span class="sxs-lookup"><span data-stu-id="622bd-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="622bd-110">Ottiene l'indice del prefisso dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="622bd-111">Metodo GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="622bd-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="622bd-112">Ottiene la chiave pubblica dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="622bd-113">Metodo GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="622bd-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="622bd-114">Ottiene il token di chiave pubblica dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="622bd-115">Metodo GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="622bd-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="622bd-116">Ottiene il nome semplice dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="622bd-117">Metodo GetVersion</span><span class="sxs-lookup"><span data-stu-id="622bd-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="622bd-118">Ottiene le informazioni sulla versione dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="622bd-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="622bd-119">Note</span><span class="sxs-lookup"><span data-stu-id="622bd-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="622bd-120">Questa interfaccia è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="622bd-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="622bd-121">Se questa interfaccia viene implementata per scenari ICorDebug al di fuori di .NET Native, sarà ignorata da Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="622bd-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="622bd-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="622bd-122">Requirements</span></span>  
 <span data-ttu-id="622bd-123">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="622bd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622bd-124">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="622bd-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="622bd-125">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="622bd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="622bd-126">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="622bd-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622bd-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="622bd-127">See also</span></span>

- [<span data-ttu-id="622bd-128">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="622bd-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="622bd-129">Debug</span><span class="sxs-lookup"><span data-stu-id="622bd-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
