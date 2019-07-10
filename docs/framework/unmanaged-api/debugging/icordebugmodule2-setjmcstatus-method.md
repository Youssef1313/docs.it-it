---
title: Metodo ICorDebugModule2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764113"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="b30ef-102">Metodo ICorDebugModule2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="b30ef-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="b30ef-103">Imposta lo stato di Just My Code (JMC) di tutti i metodi di tutte le classi in questo ICorDebugModule2 sul valore specificato, eccetto quelli presenti il `pTokens` matrice, che imposta il valore opposto.</span><span class="sxs-lookup"><span data-stu-id="b30ef-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30ef-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b30ef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b30ef-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b30ef-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="b30ef-106">[in] Impostare su `true` se il codice deve essere sottoposto a debug; in caso contrario, impostato su `false`.</span><span class="sxs-lookup"><span data-stu-id="b30ef-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="b30ef-107">[in] Dimensione della matrice `pTokens`.</span><span class="sxs-lookup"><span data-stu-id="b30ef-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="b30ef-108">[in] Matrice di `mdToken` valori, ognuno dei quali fa riferimento a un metodo che avrà lo stato JMC impostato su!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="b30ef-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b30ef-109">Note</span><span class="sxs-lookup"><span data-stu-id="b30ef-109">Remarks</span></span>  
 <span data-ttu-id="b30ef-110">Lo stato JMC di ogni metodo specificato nel `pTokens` matrice è impostata su opposto di `bIsJustMycode` valore.</span><span class="sxs-lookup"><span data-stu-id="b30ef-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="b30ef-111">Lo stato di tutti gli altri metodi in questo modulo viene impostato sul `bIsJustMycode` valore.</span><span class="sxs-lookup"><span data-stu-id="b30ef-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="b30ef-112">Il `SetJMCStatus` metodo cancella tutte le impostazioni precedenti JMC in questo modulo.</span><span class="sxs-lookup"><span data-stu-id="b30ef-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="b30ef-113">Il `SetJMCStatus` metodo restituisce un HRESULT S_OK se tutte le funzioni sono state impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="b30ef-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="b30ef-114">Restituisce un HRESULT invece CORDBG_E_FUNCTION_NOT_DEBUGGABLE se alcune funzioni che sono contrassegnate `true` non sono ancora debuggable.</span><span class="sxs-lookup"><span data-stu-id="b30ef-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b30ef-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b30ef-115">Requirements</span></span>  
 <span data-ttu-id="b30ef-116">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b30ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b30ef-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b30ef-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b30ef-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b30ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b30ef-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b30ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
