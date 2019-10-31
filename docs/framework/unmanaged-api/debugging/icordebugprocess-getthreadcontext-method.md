---
title: Metodo ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: c6def272ecc7bd2b6e946e2c9623f0b60587d317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128801"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="703a7-102">Metodo ICorDebugProcess::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="703a7-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="703a7-103">Ottiene il contesto per il thread specificato in questo processo.</span><span class="sxs-lookup"><span data-stu-id="703a7-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703a7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="703a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703a7-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="703a7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="703a7-106">in ID del thread per il quale recuperare il contesto.</span><span class="sxs-lookup"><span data-stu-id="703a7-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="703a7-107">[in] Dimensione della matrice `context`.</span><span class="sxs-lookup"><span data-stu-id="703a7-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="703a7-108">[in, out] Matrice di byte che descrivono il contesto del thread.</span><span class="sxs-lookup"><span data-stu-id="703a7-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="703a7-109">Il contesto specifica l'architettura del processore in cui è in esecuzione il thread.</span><span class="sxs-lookup"><span data-stu-id="703a7-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="703a7-110">Note</span><span class="sxs-lookup"><span data-stu-id="703a7-110">Remarks</span></span>  
 <span data-ttu-id="703a7-111">Il debugger deve chiamare questo metodo anziché il metodo Win32 `GetThreadContext`, perché il thread potrebbe essere effettivamente in stato "Hijack", in cui il contesto è stato modificato temporaneamente.</span><span class="sxs-lookup"><span data-stu-id="703a7-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="703a7-112">Questo metodo deve essere utilizzato solo quando un thread è in codice nativo.</span><span class="sxs-lookup"><span data-stu-id="703a7-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="703a7-113">Usare [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) per i thread nel codice gestito.</span><span class="sxs-lookup"><span data-stu-id="703a7-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="703a7-114">I dati restituiti sono una struttura di contesto per la piattaforma corrente.</span><span class="sxs-lookup"><span data-stu-id="703a7-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="703a7-115">Analogamente al metodo Win32 `GetThreadContext`, il chiamante deve inizializzare il parametro `context` prima di chiamare questo metodo.</span><span class="sxs-lookup"><span data-stu-id="703a7-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703a7-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="703a7-116">Requirements</span></span>  
 <span data-ttu-id="703a7-117">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703a7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703a7-118">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="703a7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="703a7-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="703a7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703a7-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
