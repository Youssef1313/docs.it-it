---
title: 'Metodo ICorDebugVariableHome:: GetLocationType'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125103"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="10ef9-102">Metodo ICorDebugVariableHome:: GetLocationType</span><span class="sxs-lookup"><span data-stu-id="10ef9-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="10ef9-103">Ottiene il tipo della posizione nativa della variabile.</span><span class="sxs-lookup"><span data-stu-id="10ef9-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ef9-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="10ef9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10ef9-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="10ef9-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="10ef9-106">out Puntatore al tipo della posizione nativa della variabile.</span><span class="sxs-lookup"><span data-stu-id="10ef9-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="10ef9-107">Per ulteriori informazioni, vedere l'enumerazione [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="10ef9-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ef9-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="10ef9-108">Requirements</span></span>  
 <span data-ttu-id="10ef9-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ef9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ef9-110">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10ef9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10ef9-111">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10ef9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10ef9-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ef9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ef9-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10ef9-113">See also</span></span>

- [<span data-ttu-id="10ef9-114">Interfaccia ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="10ef9-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="10ef9-115">Enumerazione VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="10ef9-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
