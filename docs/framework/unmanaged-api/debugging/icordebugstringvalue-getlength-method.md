---
title: Metodo ICorDebugStringValue::GetLength
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: a6f2f536d360ffe41caf2a96c8b051f9167343c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138963"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="a0457-102">Metodo ICorDebugStringValue::GetLength</span><span class="sxs-lookup"><span data-stu-id="a0457-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="a0457-103">Ottiene il numero di caratteri nella stringa a cui fa riferimento questo ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="a0457-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0457-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a0457-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0457-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a0457-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="a0457-106">out Puntatore a un valore che specifica la lunghezza della stringa a cui fa riferimento questo oggetto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="a0457-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0457-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a0457-107">Requirements</span></span>  
 <span data-ttu-id="a0457-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0457-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0457-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0457-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0457-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0457-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0457-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0457-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
