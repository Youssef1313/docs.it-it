---
title: Metodo ICorDebugModule3::CreateReaderForInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137309"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="bd0db-102">Metodo ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="bd0db-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="bd0db-103">Crea un lettore di simboli di debug per un modulo dinamico.</span><span class="sxs-lookup"><span data-stu-id="bd0db-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0db-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bd0db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd0db-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bd0db-105">Parameters</span></span>  
 <span data-ttu-id="bd0db-106">riid</span><span class="sxs-lookup"><span data-stu-id="bd0db-106">riid</span></span>  
 <span data-ttu-id="bd0db-107">in IID dell'interfaccia COM da restituire.</span><span class="sxs-lookup"><span data-stu-id="bd0db-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="bd0db-108">Si tratta in genere di un' [interfaccia ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bd0db-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="bd0db-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="bd0db-109">ppObj</span></span>  
 <span data-ttu-id="bd0db-110">out Puntatore a un puntatore all'interfaccia restituita.</span><span class="sxs-lookup"><span data-stu-id="bd0db-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd0db-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bd0db-111">Return Value</span></span>  
 <span data-ttu-id="bd0db-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd0db-112">S_OK</span></span>  
 <span data-ttu-id="bd0db-113">Creazione del Reader completata.</span><span class="sxs-lookup"><span data-stu-id="bd0db-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="bd0db-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="bd0db-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="bd0db-115">Il modulo non è un modulo in memoria o dinamico.</span><span class="sxs-lookup"><span data-stu-id="bd0db-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="bd0db-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd0db-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="bd0db-117">I simboli non sono stati forniti dall'applicazione o non sono ancora disponibili.</span><span class="sxs-lookup"><span data-stu-id="bd0db-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="bd0db-118">E_FAIL (o altri codici E_ restituiti)</span><span class="sxs-lookup"><span data-stu-id="bd0db-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bd0db-119">Impossibile creare il lettore.</span><span class="sxs-lookup"><span data-stu-id="bd0db-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd0db-120">Note</span><span class="sxs-lookup"><span data-stu-id="bd0db-120">Remarks</span></span>  
 <span data-ttu-id="bd0db-121">Questo metodo può essere usato anche per creare un oggetto lettore di simboli per i moduli in memoria (non dinamici), ma solo dopo che i simboli sono disponibili per la prima volta (indicati dal callback del [Metodo UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="bd0db-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="bd0db-122">Questo metodo restituisce una nuova istanza di Reader ogni volta che viene chiamata (ad esempio [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="bd0db-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="bd0db-123">Pertanto, il debugger deve memorizzare nella cache il risultato e richiedere una nuova istanza solo quando è possibile che i dati sottostanti siano stati modificati, ovvero quando viene ricevuto un callback del [metodo loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd0db-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="bd0db-124">I moduli dinamici non hanno alcun simbolo disponibile fino a quando non è stato caricato il primo tipo (come indicato dal callback del [metodo loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="bd0db-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd0db-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bd0db-125">Requirements</span></span>  
 <span data-ttu-id="bd0db-126">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd0db-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd0db-127">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd0db-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd0db-128">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd0db-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd0db-129">**Versioni .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="bd0db-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0db-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bd0db-130">See also</span></span>

- [<span data-ttu-id="bd0db-131">Interfaccia ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="bd0db-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="bd0db-132">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="bd0db-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="bd0db-133">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="bd0db-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
