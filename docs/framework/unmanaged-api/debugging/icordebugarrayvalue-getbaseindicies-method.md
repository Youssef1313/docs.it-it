---
title: Metodo ICorDebugArrayValue::GetBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f4ecb700a19a4e06f9f0056881fe3cdb9753aae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737601"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="e1c74-102">Metodo ICorDebugArrayValue::GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="e1c74-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="e1c74-103">Ottiene l'indice di base di ogni dimensione della matrice.</span><span class="sxs-lookup"><span data-stu-id="e1c74-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c74-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e1c74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c74-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e1c74-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e1c74-106">[in] Il numero di dimensioni di questo `ICorDebugArrayValue` oggetto.</span><span class="sxs-lookup"><span data-stu-id="e1c74-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="e1c74-107">Questo valore viene anche le dimensioni dei `indicies` matrice perché la dimensione è uguale al numero di dimensioni del `ICorDebugArrayValue` oggetto.</span><span class="sxs-lookup"><span data-stu-id="e1c74-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="e1c74-108">[out] Matrice di interi, ognuno dei quali è l'indice di base (vale a dire, l'indice iniziale) di una dimensione di questo `ICorDebugArrayValue` oggetto.</span><span class="sxs-lookup"><span data-stu-id="e1c74-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c74-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e1c74-109">Requirements</span></span>  
 <span data-ttu-id="e1c74-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c74-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c74-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1c74-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1c74-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1c74-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1c74-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
