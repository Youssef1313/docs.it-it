---
title: Metodo ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6a8be489ff2a99bb9da393577514b2442d50db8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967958"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="11222-102">Metodo ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="11222-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="11222-103">Ottiene il contesto corrente di questo agente di rimozione.</span><span class="sxs-lookup"><span data-stu-id="11222-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11222-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="11222-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11222-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="11222-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="11222-106">[in] Flag che specificano le parti del contesto da restituire (definite in WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="11222-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="11222-107">[in] Numero di byte in `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="11222-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="11222-108">[out] Puntatore al numero di byte effettivamente scritti in `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="11222-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="11222-109">[out] Matrice di byte che contiene il contesto corrente di questo agente di rimozione.</span><span class="sxs-lookup"><span data-stu-id="11222-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11222-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="11222-110">Return Value</span></span>  
 <span data-ttu-id="11222-111">Qualsiasi valore HRESULT con errori ricevuto da mscordbi viene considerato irreversibile e causa la restituzione di `CORDBG_E_DATA_TARGET_ERROR` da parte delle API ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="11222-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11222-112">Note</span><span class="sxs-lookup"><span data-stu-id="11222-112">Remarks</span></span>  
 <span data-ttu-id="11222-113">Il valore iniziale dell' `contextBuf` argomento viene impostato sul buffer del contesto restituito chiamando il metodo [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="11222-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11222-114">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="11222-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="11222-115">Poiché l'agente di rimozione potrebbe ripristinare solo un subset dei registri, ad esempio solo quelli non volatili, il contesto potrebbe non corrispondere esattamente allo stato del registro al momento dell'effettiva chiamata al metodo.</span><span class="sxs-lookup"><span data-stu-id="11222-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11222-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="11222-116">Requirements</span></span>  
 <span data-ttu-id="11222-117">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11222-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11222-118">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11222-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11222-119">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11222-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11222-120">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11222-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11222-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="11222-121">See also</span></span>

- [<span data-ttu-id="11222-122">Interfaccia ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="11222-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="11222-123">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="11222-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
