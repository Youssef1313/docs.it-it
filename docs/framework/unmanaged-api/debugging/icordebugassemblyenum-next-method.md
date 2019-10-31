---
title: Metodo ICorDebugAssemblyEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: 86fa44b609b4b89cfaa28f0bfa7bbdce6217623f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122866"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="bf90e-102">Metodo ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="bf90e-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="bf90e-103">Ottiene il numero specificato di assembly dalla raccolta, a partire dalla posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="bf90e-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf90e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bf90e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf90e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bf90e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bf90e-106">in Numero di assembly da recuperare.</span><span class="sxs-lookup"><span data-stu-id="bf90e-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="bf90e-107">out Matrice di puntatori, ciascuno dei quali punta a un oggetto ICorDebugAssembly che rappresenta un assembly.</span><span class="sxs-lookup"><span data-stu-id="bf90e-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bf90e-108">out Puntatore al numero di assembly effettivamente restituiti.</span><span class="sxs-lookup"><span data-stu-id="bf90e-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="bf90e-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="bf90e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf90e-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bf90e-110">Requirements</span></span>  
 <span data-ttu-id="bf90e-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf90e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf90e-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf90e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf90e-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf90e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf90e-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf90e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
