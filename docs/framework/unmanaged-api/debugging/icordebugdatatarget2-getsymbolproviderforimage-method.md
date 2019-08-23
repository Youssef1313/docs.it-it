---
title: Metodo ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e5a6e70d5148756a5ed8d17c56577da920d1b69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911456"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="8d033-102">Metodo ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="8d033-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="8d033-103">Restituisce il provider di simboli per un modulo dall'indirizzo di base del modulo.</span><span class="sxs-lookup"><span data-stu-id="8d033-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d033-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8d033-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d033-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="8d033-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="8d033-106">in Valore [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) che rappresenta l'indirizzo di base di un modulo.</span><span class="sxs-lookup"><span data-stu-id="8d033-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="8d033-107">out Puntatore all'indirizzo di un oggetto [Metodo icordebugsymbolprovider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8d033-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d033-108">Note</span><span class="sxs-lookup"><span data-stu-id="8d033-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d033-109">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d033-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d033-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8d033-110">Requirements</span></span>  
 <span data-ttu-id="8d033-111">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d033-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d033-112">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8d033-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d033-113">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d033-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d033-114">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d033-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d033-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8d033-115">See also</span></span>

- [<span data-ttu-id="8d033-116">Interfaccia ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="8d033-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="8d033-117">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="8d033-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
