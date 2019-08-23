---
title: Metodo ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5436f56d3dcad7de3df2296485b0a36e5b3cfd79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967970"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="3b1da-102">Metodo ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="3b1da-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="3b1da-103">Assegna il valore di una matrice di byte a una variabile.</span><span class="sxs-lookup"><span data-stu-id="3b1da-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1da-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3b1da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1da-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3b1da-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="3b1da-106">[in] Offset iniziale nella variabile da cui leggere il valore.</span><span class="sxs-lookup"><span data-stu-id="3b1da-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="3b1da-107">Questo parametro viene usato durante la scrittura nei campi membro di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="3b1da-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="3b1da-108">[in] Identificatore del thread il cui contesto deve essere aggiornato per riflettere il nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="3b1da-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="3b1da-109">[in] Dimensioni in byte del contesto del thread.</span><span class="sxs-lookup"><span data-stu-id="3b1da-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="3b1da-110">[in] Contesto del thread usato per scrivere il valore.</span><span class="sxs-lookup"><span data-stu-id="3b1da-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="3b1da-111">[in] Dimensioni in byte del buffer `pValue`.</span><span class="sxs-lookup"><span data-stu-id="3b1da-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3b1da-112">[in] Buffer contenente il valore da configurare.</span><span class="sxs-lookup"><span data-stu-id="3b1da-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b1da-113">Note</span><span class="sxs-lookup"><span data-stu-id="3b1da-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b1da-114">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3b1da-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1da-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3b1da-115">Requirements</span></span>  
 <span data-ttu-id="3b1da-116">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b1da-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b1da-117">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b1da-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b1da-118">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b1da-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b1da-119">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1da-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1da-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b1da-120">See also</span></span>

- [<span data-ttu-id="3b1da-121">Interfaccia ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="3b1da-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3b1da-122">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="3b1da-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
