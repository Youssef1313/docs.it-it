---
title: Metodo ICorDebugNativeFrame::GetLocalMemoryValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: cee095003c136142052b8f946fa8227927c80ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096872"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="479e8-102">Metodo ICorDebugNativeFrame::GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="479e8-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="479e8-103">Ottiene il valore di un argomento o di una variabile locale archiviata nella posizione di memoria specificata per il frame nativo.</span><span class="sxs-lookup"><span data-stu-id="479e8-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479e8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="479e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="479e8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="479e8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="479e8-106">in Valore `CORDB_ADDRESS` che specifica la posizione di memoria contenente il valore.</span><span class="sxs-lookup"><span data-stu-id="479e8-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="479e8-107">in Integer che specifica la dimensione della firma dei metadati binari a cui fa riferimento il parametro `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="479e8-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="479e8-108">in Valore `PCCOR_SIGNATURE` che punta alla firma dei metadati binaria del tipo del valore.</span><span class="sxs-lookup"><span data-stu-id="479e8-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="479e8-109">out Puntatore all'indirizzo di un oggetto "ICorDebugValue" che rappresenta il valore recuperato archiviato nella posizione di memoria specificata.</span><span class="sxs-lookup"><span data-stu-id="479e8-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="479e8-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="479e8-110">Requirements</span></span>  
 <span data-ttu-id="479e8-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="479e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479e8-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="479e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="479e8-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="479e8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="479e8-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="479e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479e8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="479e8-115">See also</span></span>
