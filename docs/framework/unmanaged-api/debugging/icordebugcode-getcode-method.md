---
title: Metodo ICorDebugCode::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e18097dd380ee354e5652886544d40da074f1230
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747618"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="b9d0c-102">Metodo ICorDebugCode::GetCode</span><span class="sxs-lookup"><span data-stu-id="b9d0c-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="b9d0c-103">Ottiene tutto il codice per la funzione specificata, formattata per il disassembly.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="b9d0c-104">Questo metodo è stato deprecato in .NET Framework versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b9d0c-105">Uso [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) invece.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d0c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b9d0c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d0c-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="b9d0c-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="b9d0c-108">[in] L'offset dell'inizio della funzione.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b9d0c-109">[in] L'offset della fine della funzione.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="b9d0c-110">[in] Le dimensioni del `buffer` della matrice in cui verrà restituito il codice.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b9d0c-111">[out] Matrice in cui verrà restituito il codice.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="b9d0c-112">[out] Il numero di byte restituiti.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d0c-113">Note</span><span class="sxs-lookup"><span data-stu-id="b9d0c-113">Remarks</span></span>  
 <span data-ttu-id="b9d0c-114">Se il codice della funzione è stato diviso in più blocchi, questi vengono concatenati in ordine crescente offset nativo.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="b9d0c-115">I limiti di istruzioni non vengono controllati.</span><span class="sxs-lookup"><span data-stu-id="b9d0c-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d0c-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b9d0c-116">Requirements</span></span>  
 <span data-ttu-id="b9d0c-117">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9d0c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d0c-118">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9d0c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9d0c-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9d0c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9d0c-120">**Versioni di .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="b9d0c-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d0c-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9d0c-121">See also</span></span>

- [<span data-ttu-id="b9d0c-122">Metodo GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="b9d0c-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
