---
title: Funzione Initialize (riferimenti alle API non gestite)
description: La funzione Initialize esegue l'inizializzazione WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc3688b30180bdcde0a87027955a789de749f90
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798435"
---
# <a name="initialize-function"></a><span data-ttu-id="3c77e-103">Initialize (funzione)</span><span class="sxs-lookup"><span data-stu-id="3c77e-103">Initialize function</span></span>

<span data-ttu-id="3c77e-104">Esegue l'inizializzazione di WMI.</span><span class="sxs-lookup"><span data-stu-id="3c77e-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3c77e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3c77e-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="3c77e-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3c77e-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="3c77e-107">in `true` per indicare che le chiamate a QueryInterface sugli oggetti WMI sono consentite; `false` in caso contrario,.</span><span class="sxs-lookup"><span data-stu-id="3c77e-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="3c77e-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3c77e-108">Return value</span></span>

<span data-ttu-id="3c77e-109">La funzione restituisce `S_OK` sempre (0).</span><span class="sxs-lookup"><span data-stu-id="3c77e-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="3c77e-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3c77e-110">Requirements</span></span>

<span data-ttu-id="3c77e-111">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c77e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3c77e-112">**Intestazione:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="3c77e-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="3c77e-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3c77e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3c77e-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3c77e-114">See also</span></span>

- [<span data-ttu-id="3c77e-115">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="3c77e-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
