---
title: Metodo ICorDebugFrame::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a637cebb9e1aef20c600353eb14fe900ad7513c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754164"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="ba779-102">Metodo ICorDebugFrame::GetCaller</span><span class="sxs-lookup"><span data-stu-id="ba779-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="ba779-103">Ottiene un puntatore all'oggetto ICorDebugFrame nella catena che ha chiamato il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="ba779-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba779-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ba779-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba779-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ba779-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="ba779-106">[out] Un puntatore all'indirizzo di un `ICorDebugFrame` oggetto che rappresenta il frame di chiamata.</span><span class="sxs-lookup"><span data-stu-id="ba779-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="ba779-107">Questo valore è null se il frame di chiamata è il frame più esterno nella catena di corrente.</span><span class="sxs-lookup"><span data-stu-id="ba779-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba779-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ba779-108">Requirements</span></span>  
 <span data-ttu-id="ba779-109">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba779-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba779-110">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba779-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba779-111">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba779-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba779-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba779-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
