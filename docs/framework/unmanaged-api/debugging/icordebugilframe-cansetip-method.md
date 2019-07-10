---
title: Metodo ICorDebugILFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756586"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="207c3-102">Metodo ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="207c3-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="207c3-103">Ottiene un valore HRESULT che indica se è sicuro impostare il puntatore all'istruzione per la posizione di offset specificata nel codice Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="207c3-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="207c3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="207c3-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="207c3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="207c3-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="207c3-106">[in] L'impostazione desiderata per il puntatore all'istruzione.</span><span class="sxs-lookup"><span data-stu-id="207c3-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="207c3-107">Note</span><span class="sxs-lookup"><span data-stu-id="207c3-107">Remarks</span></span>  
 <span data-ttu-id="207c3-108">Usare la `CanSetIP` metodo prima di chiamare il [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="207c3-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="207c3-109">Se `CanSetIP` restituisce qualsiasi valore HRESULT diverso da S_OK, sarà comunque possibile richiamare `ICorDebugILFrame::SetIP`, ma non c'è garanzia che il debugger continua l'esecuzione sicura e corretta del codice sottoposto a debug.</span><span class="sxs-lookup"><span data-stu-id="207c3-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="207c3-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="207c3-110">Requirements</span></span>  
 <span data-ttu-id="207c3-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="207c3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="207c3-112">**Intestazione:** CorDebug.idl, CorDebug,h</span><span class="sxs-lookup"><span data-stu-id="207c3-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="207c3-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="207c3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="207c3-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="207c3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
