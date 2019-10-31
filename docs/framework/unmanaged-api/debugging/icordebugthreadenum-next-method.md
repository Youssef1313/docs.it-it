---
title: Metodo ICorDebugThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 0c455706b0d644d2444e9fbdf49c5a5d4f5295a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122395"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="eb676-102">Metodo ICorDebugThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="eb676-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="eb676-103">Ottiene il numero di istanze di ICorDebugThread specificate dall'enumerazione, a partire dalla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="eb676-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb676-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="eb676-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb676-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="eb676-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="eb676-106">in Numero di istanze di `ICorDebugThread` da recuperare.</span><span class="sxs-lookup"><span data-stu-id="eb676-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="eb676-107">out Matrice di puntatori, ciascuno dei quali punta a un oggetto `ICorDebugThread` che rappresenta un thread.</span><span class="sxs-lookup"><span data-stu-id="eb676-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="eb676-108">out Puntatore al numero di istanze di `ICorDebugThread` restituite effettivamente.</span><span class="sxs-lookup"><span data-stu-id="eb676-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="eb676-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="eb676-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb676-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="eb676-110">Requirements</span></span>  
 <span data-ttu-id="eb676-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb676-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb676-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb676-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb676-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb676-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb676-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb676-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
