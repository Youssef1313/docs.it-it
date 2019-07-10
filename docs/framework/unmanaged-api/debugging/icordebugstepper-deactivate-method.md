---
title: Metodo ICorDebugStepper::Deactivate
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b577e915422814fbd0060fdda53b9e2bf7cd091a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760722"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="cf474-102">Metodo ICorDebugStepper::Deactivate</span><span class="sxs-lookup"><span data-stu-id="cf474-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="cf474-103">Fa sì che questo ICorDebugStepper annullare l'ultimo comando passaggio che ha ricevuto.</span><span class="sxs-lookup"><span data-stu-id="cf474-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf474-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf474-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf474-105">Note</span><span class="sxs-lookup"><span data-stu-id="cf474-105">Remarks</span></span>  
 <span data-ttu-id="cf474-106">Un nuovo comando debug passo a passo può essere rilasciato dopo il comando passaggio ricevuto più di recente è stato annullato.</span><span class="sxs-lookup"><span data-stu-id="cf474-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf474-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cf474-107">Requirements</span></span>  
 <span data-ttu-id="cf474-108">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf474-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf474-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf474-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf474-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf474-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf474-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf474-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
