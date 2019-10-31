---
title: Metodo ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125522"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="b35a0-102">Metodo ICorDebugCodeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="b35a0-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="b35a0-103">Ottiene il numero specificato di istanze "ICorDebugCode" dall'enumerazione, a partire dalla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="b35a0-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="b35a0-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b35a0-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="b35a0-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b35a0-105">Parameters</span></span>

`celt`  
<span data-ttu-id="b35a0-106">in Numero di istanze di `ICorDebugCode` da recuperare.</span><span class="sxs-lookup"><span data-stu-id="b35a0-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="b35a0-107">out Matrice di puntatori, ciascuno dei quali punta a un oggetto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="b35a0-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="b35a0-108">out Puntatore al numero di istanze di `ICorDebugCode` restituite effettivamente.</span><span class="sxs-lookup"><span data-stu-id="b35a0-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="b35a0-109">Questo valore può essere null se `celt` è uno.</span><span class="sxs-lookup"><span data-stu-id="b35a0-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="b35a0-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b35a0-110">Requirements</span></span>

<span data-ttu-id="b35a0-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b35a0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b35a0-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b35a0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b35a0-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b35a0-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b35a0-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35a0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
