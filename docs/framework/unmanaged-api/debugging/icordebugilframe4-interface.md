---
title: Interfaccia ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130842"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="061f0-102">Interfaccia ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="061f0-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="061f0-103">[Supportato in .NET Framework 4.5.2 e versioni successive]</span><span class="sxs-lookup"><span data-stu-id="061f0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="061f0-104">Fornisce metodi che consentono di accedere alle variabili locali e al codice in uno stack frame del codice in linguaggio intermedio.</span><span class="sxs-lookup"><span data-stu-id="061f0-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="061f0-105">L'accesso del debugger a variabili e codice aggiunti nella strumentazione del profiler ReJIT viene specificato da un parametro.</span><span class="sxs-lookup"><span data-stu-id="061f0-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="061f0-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="061f0-106">Methods</span></span>  
  
|<span data-ttu-id="061f0-107">Metodo</span><span class="sxs-lookup"><span data-stu-id="061f0-107">Method</span></span>|<span data-ttu-id="061f0-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="061f0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="061f0-109">Metodo EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="061f0-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="061f0-110">Restituisce un elenco delle variabili locali disponibili nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="061f0-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="061f0-111">Metodo GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="061f0-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="061f0-112">Restituisce il codice eseguito da questo stack frame.</span><span class="sxs-lookup"><span data-stu-id="061f0-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="061f0-113">Metodo GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="061f0-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="061f0-114">Restituisce il valore di una variabile locale nel frame del linguaggio intermedio.</span><span class="sxs-lookup"><span data-stu-id="061f0-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="061f0-115">Note</span><span class="sxs-lookup"><span data-stu-id="061f0-115">Remarks</span></span>  
 <span data-ttu-id="061f0-116">Questi metodi offrono funzionalità oltre a quelle fornite dai metodi [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)e [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="061f0-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="061f0-117">Ogni metodo include un parametro `flags` che specifica se le variabili locali aggiuntive o il codice definito dalla richiesta ReJIT di un profiler sono visibili.</span><span class="sxs-lookup"><span data-stu-id="061f0-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="061f0-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="061f0-118">Requirements</span></span>  
 <span data-ttu-id="061f0-119">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="061f0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="061f0-120">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="061f0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="061f0-121">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="061f0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="061f0-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="061f0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061f0-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="061f0-123">See also</span></span>

- [<span data-ttu-id="061f0-124">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="061f0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="061f0-125">Debug</span><span class="sxs-lookup"><span data-stu-id="061f0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
