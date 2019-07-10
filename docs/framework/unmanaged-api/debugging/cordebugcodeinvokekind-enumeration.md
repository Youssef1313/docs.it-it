---
title: Enumerazione CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059e823110686a2b939c9664fa5b67e4041c3486
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740320"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="60e2d-102">Enumerazione CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="60e2d-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="60e2d-103">Descrive in che modo una funzione esportata richiama il codice gestito.</span><span class="sxs-lookup"><span data-stu-id="60e2d-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e2d-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="60e2d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="60e2d-105">Membri</span><span class="sxs-lookup"><span data-stu-id="60e2d-105">Members</span></span>  
  
|<span data-ttu-id="60e2d-106">Member</span><span class="sxs-lookup"><span data-stu-id="60e2d-106">Member</span></span>|<span data-ttu-id="60e2d-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="60e2d-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="60e2d-108">Se il codice gestito viene richiamato con questo metodo, in un secondo momento dovrà essere individuato mediante eventi espliciti o punti di interruzione.</span><span class="sxs-lookup"><span data-stu-id="60e2d-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="60e2d-109">--oppure--</span><span class="sxs-lookup"><span data-stu-id="60e2d-109">--or--</span></span><br /><br /> <span data-ttu-id="60e2d-110">È possibile che alcune parti di codice gestito chiamate dal metodo vadano perdute perché non esiste un modo semplice per arrestarlo.</span><span class="sxs-lookup"><span data-stu-id="60e2d-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="60e2d-111">--oppure--</span><span class="sxs-lookup"><span data-stu-id="60e2d-111">--or--</span></span><br /><br /> <span data-ttu-id="60e2d-112">Il metodo può non richiamare il codice gestito.</span><span class="sxs-lookup"><span data-stu-id="60e2d-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="60e2d-113">Il metodo richiama il codice gestito mediante un'istruzione di restituzione.</span><span class="sxs-lookup"><span data-stu-id="60e2d-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="60e2d-114">Nel codice gestito successivo viene eseguita l'uscita.</span><span class="sxs-lookup"><span data-stu-id="60e2d-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="60e2d-115">Questo metodo richiama il codice gestito mediante una chiamata tail.</span><span class="sxs-lookup"><span data-stu-id="60e2d-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="60e2d-116">L'esecuzione passo-passo e l'esecuzione di istruzioni per tutte le istruzioni della chiamata vengono completate nel codice gestito.</span><span class="sxs-lookup"><span data-stu-id="60e2d-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60e2d-117">Note</span><span class="sxs-lookup"><span data-stu-id="60e2d-117">Remarks</span></span>  
 <span data-ttu-id="60e2d-118">Questa enumerazione viene utilizzata per la [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodo per fornire informazioni sull'esecuzione di istruzioni tramite codice gestito.</span><span class="sxs-lookup"><span data-stu-id="60e2d-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60e2d-119">Questa enumerazione è progettata per l'uso solo in scenari di debug di .NET Native.</span><span class="sxs-lookup"><span data-stu-id="60e2d-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60e2d-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="60e2d-120">Requirements</span></span>  
 <span data-ttu-id="60e2d-121">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60e2d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60e2d-122">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60e2d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60e2d-123">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60e2d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60e2d-124">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60e2d-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e2d-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="60e2d-125">See also</span></span>

- [<span data-ttu-id="60e2d-126">Enumerazioni di debug</span><span class="sxs-lookup"><span data-stu-id="60e2d-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="60e2d-127">Debug</span><span class="sxs-lookup"><span data-stu-id="60e2d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
