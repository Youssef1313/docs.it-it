---
title: Interfaccia ICorDebugFunctionBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: a7876cd932558ad95dab7adac3c91a6f23ca647c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134659"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="eaa81-102">Interfaccia ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa81-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="eaa81-103">Estende l'interfaccia ICorDebugBreakpoint per supportare i punti di interruzione all'interno di funzioni.</span><span class="sxs-lookup"><span data-stu-id="eaa81-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaa81-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="eaa81-104">Methods</span></span>  
  
|<span data-ttu-id="eaa81-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="eaa81-105">Method</span></span>|<span data-ttu-id="eaa81-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="eaa81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaa81-107">Metodo GetFunction</span><span class="sxs-lookup"><span data-stu-id="eaa81-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="eaa81-108">Ottiene un puntatore a interfaccia a un ICorDebugFunction che fa riferimento alla funzione in cui è impostato il punto di interruzione.</span><span class="sxs-lookup"><span data-stu-id="eaa81-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="eaa81-109">Metodo GetOffset</span><span class="sxs-lookup"><span data-stu-id="eaa81-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="eaa81-110">Ottiene l'offset del punto di interruzione all'interno della funzione.</span><span class="sxs-lookup"><span data-stu-id="eaa81-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa81-111">Note</span><span class="sxs-lookup"><span data-stu-id="eaa81-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaa81-112">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="eaa81-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa81-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="eaa81-113">Requirements</span></span>  
 <span data-ttu-id="eaa81-114">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa81-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa81-115">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaa81-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaa81-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaa81-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaa81-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa81-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eaa81-118">See also</span></span>

- [<span data-ttu-id="eaa81-119">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="eaa81-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
