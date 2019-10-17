---
title: Metodo ICorDebugCode::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25349f7c8274b818df2cd1bc5d67856e31efecc4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395537"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="27480-102">Metodo ICorDebugCode::GetSize</span><span class="sxs-lookup"><span data-stu-id="27480-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="27480-103">Ottiene la dimensione, in byte, del codice binario rappresentato da questo "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="27480-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="27480-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="27480-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="27480-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="27480-105">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="27480-106">out Puntatore alla dimensione, in byte, del codice binario rappresentato da questo oggetto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="27480-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="27480-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="27480-107">Requirements</span></span>

<span data-ttu-id="27480-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27480-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="27480-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27480-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="27480-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27480-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="27480-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27480-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
