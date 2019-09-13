---
title: Metodo ICorDebugModule::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894983"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="ea219-102">Metodo ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="ea219-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="ea219-103">Ottiene il nome file del modulo.</span><span class="sxs-lookup"><span data-stu-id="ea219-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea219-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ea219-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea219-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ea219-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="ea219-106">[in] Dimensione della matrice `szName`.</span><span class="sxs-lookup"><span data-stu-id="ea219-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ea219-107">in Puntatore alla lunghezza del nome restituito.</span><span class="sxs-lookup"><span data-stu-id="ea219-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea219-108">out Matrice che archivia il nome restituito.</span><span class="sxs-lookup"><span data-stu-id="ea219-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea219-109">Note</span><span class="sxs-lookup"><span data-stu-id="ea219-109">Remarks</span></span>  
 <span data-ttu-id="ea219-110">Il `GetName` metodo restituisce un valore HRESULT S_OK se il nome file del modulo corrisponde al nome su disco.</span><span class="sxs-lookup"><span data-stu-id="ea219-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="ea219-111">`GetName`Restituisce un valore HRESULT S_FALSE se il nome viene fabbricato, ad esempio per un modulo dinamico o in memoria.</span><span class="sxs-lookup"><span data-stu-id="ea219-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea219-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ea219-112">Requirements</span></span>  
 <span data-ttu-id="ea219-113">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea219-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea219-114">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea219-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea219-115">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea219-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea219-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea219-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea219-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea219-117">See also</span></span>
