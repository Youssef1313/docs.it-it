---
title: Metodo ICorDebugManagedCallback::LoadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5619dea17b9a7140238fd559d2f6b1a5d190ac33
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761891"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="aa0b6-102">Metodo ICorDebugManagedCallback::LoadClass</span><span class="sxs-lookup"><span data-stu-id="aa0b6-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="aa0b6-103">Notifica al debugger che una classe è stata caricata.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa0b6-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa0b6-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa0b6-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="aa0b6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="aa0b6-106">[in] Un puntatore a un oggetto ICorDebugAppDomain che rappresenta il dominio applicazione in cui è stata caricata la classe.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="aa0b6-107">[in] Un puntatore a un oggetto ICorDebugClass che rappresenta la classe.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa0b6-108">Note</span><span class="sxs-lookup"><span data-stu-id="aa0b6-108">Remarks</span></span>  
 <span data-ttu-id="aa0b6-109">Questo callback si verifica solo se è stato abilitato il caricamento delle classi per il modulo che contiene la classe.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="aa0b6-110">Il caricamento delle classi è sempre abilitato per i moduli dinamici.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="aa0b6-111">Il `LoadClass` callback offre un tempo appropriato per associare i punti di interruzione per le classi appena generate nei moduli dinamici.</span><span class="sxs-lookup"><span data-stu-id="aa0b6-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa0b6-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aa0b6-112">Requirements</span></span>  
 <span data-ttu-id="aa0b6-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa0b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa0b6-114">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa0b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa0b6-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa0b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa0b6-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa0b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0b6-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa0b6-117">See also</span></span>

- [<span data-ttu-id="aa0b6-118">Metodo UnloadClass</span><span class="sxs-lookup"><span data-stu-id="aa0b6-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="aa0b6-119">Interfaccia ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="aa0b6-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
