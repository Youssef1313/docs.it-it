---
title: Metodo ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc62618c5872a2c3e3740be4c60ae02e386c1868
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750024"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="75f14-102">Metodo ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="75f14-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="75f14-103">Ottiene un elenco dei moduli caricati fino a questo momento.</span><span class="sxs-lookup"><span data-stu-id="75f14-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f14-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75f14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f14-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="75f14-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="75f14-106">[in] Numero di moduli per i quali sono richieste informazioni.</span><span class="sxs-lookup"><span data-stu-id="75f14-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="75f14-107">[out] Puntatore al numero di moduli sui quali sono state restituite informazioni.</span><span class="sxs-lookup"><span data-stu-id="75f14-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="75f14-108">[out] Un puntatore a una matrice di [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) gli oggetti che forniscono informazioni sui moduli caricati.</span><span class="sxs-lookup"><span data-stu-id="75f14-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f14-109">Note</span><span class="sxs-lookup"><span data-stu-id="75f14-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75f14-110">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="75f14-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f14-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="75f14-111">Requirements</span></span>  
 <span data-ttu-id="75f14-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f14-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f14-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75f14-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75f14-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f14-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f14-115">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f14-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f14-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75f14-116">See also</span></span>

- [<span data-ttu-id="75f14-117">Interfaccia ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="75f14-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="75f14-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="75f14-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
