---
title: Metodo ICorDebugThread2::GetActiveFunctions
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf3998d7430348cb71af8e7dd75cf2203d380ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769039"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="87109-102">Metodo ICorDebugThread2::GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="87109-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="87109-103">Ottiene informazioni sulla funzione attiva in ognuno dei frame di questo thread.</span><span class="sxs-lookup"><span data-stu-id="87109-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87109-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="87109-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87109-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="87109-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="87109-106">[in] Dimensione della matrice `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="87109-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="87109-107">[out] Un puntatore al numero di oggetti restituiti nel `pFunctions` matrice.</span><span class="sxs-lookup"><span data-stu-id="87109-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="87109-108">Il numero di oggetti restituito sarà uguale al numero di frame gestiti nello stack.</span><span class="sxs-lookup"><span data-stu-id="87109-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="87109-109">[in, out] Matrice di oggetti COR_ACTIVE_FUNCTION, ognuno dei quali contiene informazioni sulle funzioni attive nei frame di questo thread.</span><span class="sxs-lookup"><span data-stu-id="87109-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="87109-110">Il primo elemento da utilizzare per il frame foglia e così via fino alla radice dello stack.</span><span class="sxs-lookup"><span data-stu-id="87109-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87109-111">Note</span><span class="sxs-lookup"><span data-stu-id="87109-111">Remarks</span></span>  
 <span data-ttu-id="87109-112">Se `pFunctions` è null per input, `GetActiveFunctions` restituisce solo il numero di funzioni sullo stack.</span><span class="sxs-lookup"><span data-stu-id="87109-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="87109-113">Vale a dire, se `pFunctions` è null per input, `GetActiveFunctions` restituisce un valore solo in `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="87109-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="87109-114">Il `GetActiveFunctions` metodo è inteso come ottimizzazione acquisizione le stesse informazioni da una traccia dello stack frame e include solo i frame che avrebbe dovuto un oggetto ICorDebugILFrame per essi nell'analisi dello stack completo.</span><span class="sxs-lookup"><span data-stu-id="87109-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87109-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="87109-115">Requirements</span></span>  
 <span data-ttu-id="87109-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87109-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87109-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87109-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87109-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87109-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87109-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87109-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
