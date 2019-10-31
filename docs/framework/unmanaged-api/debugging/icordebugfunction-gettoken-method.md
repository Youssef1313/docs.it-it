---
title: Metodo ICorDebugFunction::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 4229d567fc4ced5e3b78b390ced29fb9ea60f93b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137835"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="feee8-102">Metodo ICorDebugFunction::GetToken</span><span class="sxs-lookup"><span data-stu-id="feee8-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="feee8-103">Ottiene il token di metadati per questa funzione.</span><span class="sxs-lookup"><span data-stu-id="feee8-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feee8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="feee8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feee8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="feee8-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="feee8-106">out Puntatore a un token di `mdMethodDef` che fa riferimento ai metadati per questa funzione.</span><span class="sxs-lookup"><span data-stu-id="feee8-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feee8-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="feee8-107">Requirements</span></span>  
 <span data-ttu-id="feee8-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feee8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feee8-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="feee8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="feee8-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feee8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feee8-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feee8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
