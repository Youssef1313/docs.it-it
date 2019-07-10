---
title: Metodo ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6629af393eeadb68292f8f2360ecb60c09a0cd03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764608"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="48984-102">Metodo ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="48984-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="48984-103">Imposta il contesto (valori del registro) per un thread.</span><span class="sxs-lookup"><span data-stu-id="48984-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48984-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="48984-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48984-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="48984-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="48984-106">[in] Identificatore del thread definito dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="48984-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="48984-107">[in] Dimensioni del buffer `pContext` da scrivere.</span><span class="sxs-lookup"><span data-stu-id="48984-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="48984-108">[in] Puntatore ai byte da scrivere.</span><span class="sxs-lookup"><span data-stu-id="48984-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48984-109">Note</span><span class="sxs-lookup"><span data-stu-id="48984-109">Remarks</span></span>  
 <span data-ttu-id="48984-110">Il metodo `SetThreadContext` aggiorna il contesto corrente per il thread specificato dall'argomento `dwThreadID` definito dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="48984-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="48984-111">Il formato del record di contesto è determinato dalla piattaforma indicata per la [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="48984-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="48984-112">In Windows, si tratta di un [contesto](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) struttura.</span><span class="sxs-lookup"><span data-stu-id="48984-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48984-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="48984-113">Requirements</span></span>  
 <span data-ttu-id="48984-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48984-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48984-115">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48984-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48984-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48984-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48984-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48984-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48984-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48984-118">See also</span></span>

- [<span data-ttu-id="48984-119">Interfaccia ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="48984-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="48984-120">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="48984-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
