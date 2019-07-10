---
title: Metodo ICorDebug::Initialize
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80465c8d1f1f9e09c0675de1667b999b332b9f6b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738141"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="6a8eb-102">Metodo ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="6a8eb-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="6a8eb-103">Inizializza il `ICorDebug` oggetto.</span><span class="sxs-lookup"><span data-stu-id="6a8eb-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8eb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6a8eb-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6a8eb-105">Note</span><span class="sxs-lookup"><span data-stu-id="6a8eb-105">Remarks</span></span>  
 <span data-ttu-id="6a8eb-106">Il debugger deve chiamare `Initialize` al momento della creazione di servizi tempo necessario per inizializzare il debug.</span><span class="sxs-lookup"><span data-stu-id="6a8eb-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="6a8eb-107">Questo metodo deve essere chiamato prima di qualsiasi altro metodo nel `ICorDebug` viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="6a8eb-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8eb-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6a8eb-108">Requirements</span></span>  
 <span data-ttu-id="6a8eb-109">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8eb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8eb-110">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a8eb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a8eb-111">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a8eb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a8eb-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8eb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8eb-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6a8eb-113">See also</span></span>

- [<span data-ttu-id="6a8eb-114">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="6a8eb-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
