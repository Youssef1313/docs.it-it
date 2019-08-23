---
title: Interfaccia ICorDebugThread3
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9622716e3a2cca7e3af0b1e1b134458a50ad1bec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962971"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="3fc74-102">Interfaccia ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="3fc74-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="3fc74-103">Fornisce il punto di ingresso per [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e le interfacce corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="3fc74-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3fc74-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="3fc74-104">Methods</span></span>  
  
|<span data-ttu-id="3fc74-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="3fc74-105">Method</span></span>|<span data-ttu-id="3fc74-106">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="3fc74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3fc74-107">Metodo CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="3fc74-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="3fc74-108">Crea un oggetto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) per il thread il cui stack si vuole rimuovere.</span><span class="sxs-lookup"><span data-stu-id="3fc74-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="3fc74-109">Metodo GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="3fc74-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="3fc74-110">Restituisce una matrice di frame interni (oggetti[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) nello stack.</span><span class="sxs-lookup"><span data-stu-id="3fc74-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fc74-111">Note</span><span class="sxs-lookup"><span data-stu-id="3fc74-111">Remarks</span></span>  
 <span data-ttu-id="3fc74-112">`ICorDebugThread3`è un'estensione logica dell'interfaccia ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3fc74-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fc74-113">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="3fc74-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc74-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3fc74-114">Requirements</span></span>  
 <span data-ttu-id="3fc74-115">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc74-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc74-116">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3fc74-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fc74-117">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fc74-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc74-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc74-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc74-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3fc74-119">See also</span></span>

- [<span data-ttu-id="3fc74-120">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="3fc74-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3fc74-121">Debug</span><span class="sxs-lookup"><span data-stu-id="3fc74-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
