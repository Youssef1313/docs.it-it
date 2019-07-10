---
title: Metodo ICorDebugILFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af3f58fa7714b3c2b0ba387b1da650f0638dd6c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758782"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="06178-102">Metodo ICorDebugILFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="06178-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="06178-103">Imposta il puntatore all'istruzione alla posizione di offset specificata nel codice Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="06178-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06178-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="06178-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06178-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="06178-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="06178-106">Posizione di offset nel codice MSIL.</span><span class="sxs-lookup"><span data-stu-id="06178-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06178-107">Note</span><span class="sxs-lookup"><span data-stu-id="06178-107">Remarks</span></span>  
 <span data-ttu-id="06178-108">Le chiamate a `SetIP` immediatamente invalidare tutti i frame e sulle sequenze per il thread corrente.</span><span class="sxs-lookup"><span data-stu-id="06178-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="06178-109">Se il debugger ha bisogno delle informazioni di frame dopo una chiamata a `SetIP`, è necessario eseguire una nuova traccia dello stack.</span><span class="sxs-lookup"><span data-stu-id="06178-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="06178-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) proverà a mantenere lo stack frame in uno stato valido.</span><span class="sxs-lookup"><span data-stu-id="06178-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="06178-111">Tuttavia, anche se il frame è in uno stato valido, è comunque possibile problemi come variabili locali non inizializzate.</span><span class="sxs-lookup"><span data-stu-id="06178-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="06178-112">Il chiamante è responsabile di garantire la coerenza del programma in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="06178-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="06178-113">Su piattaforme a 64 bit, il puntatore all'istruzione non può essere spostato fuori da un `catch` o `finally` blocco.</span><span class="sxs-lookup"><span data-stu-id="06178-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="06178-114">Se `SetIP` viene chiamato per rendere tale cambiamento su una piattaforma a 64 bit, verrà restituito un HRESULT che indica un errore.</span><span class="sxs-lookup"><span data-stu-id="06178-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06178-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="06178-115">Requirements</span></span>  
 <span data-ttu-id="06178-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06178-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06178-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06178-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06178-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06178-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06178-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06178-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
