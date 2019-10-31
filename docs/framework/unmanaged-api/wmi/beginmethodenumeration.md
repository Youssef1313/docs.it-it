---
title: Funzione BeginMethodEnumeration (riferimenti alle API non gestite)
description: La funzione BeginMethodEnumeration inizia un'enumerazione dei metodi dell'oggetto
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a27787052757098d4edb2d8516e22d8a03b7009a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138794"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="e5ac0-103">Funzione BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="e5ac0-103">BeginEnumeration function</span></span>
<span data-ttu-id="e5ac0-104">Inizia un'enumerazione dei metodi disponibili per l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e5ac0-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e5ac0-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="e5ac0-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e5ac0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e5ac0-107">in Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e5ac0-108">in Puntatore a un'istanza di [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="e5ac0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="e5ac0-109">in Zero (0) per tutti i metodi o un flag che specifica l'ambito dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="e5ac0-110">I flag seguenti sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="e5ac0-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="e5ac0-111">Costante</span><span class="sxs-lookup"><span data-stu-id="e5ac0-111">Constant</span></span>  |<span data-ttu-id="e5ac0-112">Value</span><span class="sxs-lookup"><span data-stu-id="e5ac0-112">Value</span></span>  |<span data-ttu-id="e5ac0-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e5ac0-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e5ac0-114">0x10</span><span class="sxs-lookup"><span data-stu-id="e5ac0-114">0x10</span></span> | <span data-ttu-id="e5ac0-115">Limitare l'enumerazione ai metodi definiti nella classe stessa.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="e5ac0-116">0x20</span><span class="sxs-lookup"><span data-stu-id="e5ac0-116">0x20</span></span> | <span data-ttu-id="e5ac0-117">Limitare l'enumerazione alle proprietà ereditate dalle classi di base.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e5ac0-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e5ac0-118">Return value</span></span>

<span data-ttu-id="e5ac0-119">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="e5ac0-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5ac0-120">Costante</span><span class="sxs-lookup"><span data-stu-id="e5ac0-120">Constant</span></span>  |<span data-ttu-id="e5ac0-121">Value</span><span class="sxs-lookup"><span data-stu-id="e5ac0-121">Value</span></span>  |<span data-ttu-id="e5ac0-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e5ac0-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5ac0-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5ac0-123">0x80041008</span></span> | <span data-ttu-id="e5ac0-124">`lEnnumFlags` è diverso da zero e non è uno dei flag specificati.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5ac0-125">0</span><span class="sxs-lookup"><span data-stu-id="e5ac0-125">0</span></span> | <span data-ttu-id="e5ac0-126">La chiamata di funzione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e5ac0-127">Note</span><span class="sxs-lookup"><span data-stu-id="e5ac0-127">Remarks</span></span>

<span data-ttu-id="e5ac0-128">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="e5ac0-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="e5ac0-129">Questa chiamata al metodo è supportata solo se l'oggetto corrente è una definizione di classe.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="e5ac0-130">La manipolazione del metodo non è disponibile dai puntatori [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) che puntano alle istanze.</span><span class="sxs-lookup"><span data-stu-id="e5ac0-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="e5ac0-131">L'ordine in cui vengono enumerati i metodi è sicuramente invariante per un'istanza specificata di [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="e5ac0-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="e5ac0-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e5ac0-132">Requirements</span></span>  
 <span data-ttu-id="e5ac0-133">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ac0-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ac0-134">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="e5ac0-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e5ac0-135">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ac0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ac0-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e5ac0-136">See also</span></span>

- [<span data-ttu-id="e5ac0-137">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="e5ac0-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
