---
title: Metodo ICorDebugEval::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24bc096a0ba01c58aa963d69fa46a1d1bbe8be75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752897"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="4ffc2-102">Metodo ICorDebugEval::GetThread</span><span class="sxs-lookup"><span data-stu-id="4ffc2-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="4ffc2-103">Ottiene il thread in cui questa valutazione è in esecuzione o verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="4ffc2-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ffc2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4ffc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ffc2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4ffc2-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="4ffc2-106">[out] Un puntatore all'indirizzo di un oggetto ICorDebugThread che rappresenta il thread.</span><span class="sxs-lookup"><span data-stu-id="4ffc2-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ffc2-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4ffc2-107">Requirements</span></span>  
 <span data-ttu-id="4ffc2-108">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ffc2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ffc2-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ffc2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ffc2-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ffc2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ffc2-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ffc2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
