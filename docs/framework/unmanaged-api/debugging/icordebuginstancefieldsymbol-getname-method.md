---
title: 'Metodo ICorDebugInstanceFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: d88e18b8d6d497098e340b396972f9ead28dbaf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139044"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="b637e-102">Metodo ICorDebugInstanceFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="b637e-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="b637e-103">Ottiene il nome del campo di istanza.</span><span class="sxs-lookup"><span data-stu-id="b637e-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b637e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b637e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b637e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b637e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b637e-106">[in] Numero di caratteri nel buffer `szName`.</span><span class="sxs-lookup"><span data-stu-id="b637e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b637e-107">[out] Puntatore al numero di caratteri effettivamente scritti nel buffer `szName`.</span><span class="sxs-lookup"><span data-stu-id="b637e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b637e-108">[out] Matrice di caratteri contenente il nome restituito.</span><span class="sxs-lookup"><span data-stu-id="b637e-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b637e-109">Note</span><span class="sxs-lookup"><span data-stu-id="b637e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b637e-110">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b637e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b637e-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b637e-111">Requirements</span></span>  
 <span data-ttu-id="b637e-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b637e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b637e-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b637e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b637e-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b637e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b637e-115">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b637e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b637e-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b637e-116">See also</span></span>

- [<span data-ttu-id="b637e-117">Interfaccia ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b637e-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b637e-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="b637e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
