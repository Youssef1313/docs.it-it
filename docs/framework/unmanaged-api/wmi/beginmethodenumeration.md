---
title: Funzione BeginMethodEnumeration (riferimenti alle API non gestite)
description: La funzione BeginMethodEnumeration avvia un'enumerazione dei metodi dell'oggetto
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ef53acdfa06b0c2be9d2aa55e89ce8fa34dfb0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761746"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="1d907-103">Funzione BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="1d907-103">BeginEnumeration function</span></span>
<span data-ttu-id="1d907-104">Avvia un'enumerazione dei metodi disponibili per l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="1d907-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="1d907-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1d907-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="1d907-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="1d907-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1d907-107">[in] Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="1d907-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1d907-108">[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.</span><span class="sxs-lookup"><span data-stu-id="1d907-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="1d907-109">[in] Zero (0) per tutti i metodi, o un flag che specifica l'ambito dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="1d907-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="1d907-110">I flag seguenti sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="1d907-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="1d907-111">Costante</span><span class="sxs-lookup"><span data-stu-id="1d907-111">Constant</span></span>  |<span data-ttu-id="1d907-112">Value</span><span class="sxs-lookup"><span data-stu-id="1d907-112">Value</span></span>  |<span data-ttu-id="1d907-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1d907-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1d907-114">0x10</span><span class="sxs-lookup"><span data-stu-id="1d907-114">0x10</span></span> | <span data-ttu-id="1d907-115">Limitare l'enumerazione per i metodi definiti nella classe stessa.</span><span class="sxs-lookup"><span data-stu-id="1d907-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="1d907-116">0x20</span><span class="sxs-lookup"><span data-stu-id="1d907-116">0x20</span></span> | <span data-ttu-id="1d907-117">Limitare l'enumerazione delle proprietà ereditate dalle classi di base.</span><span class="sxs-lookup"><span data-stu-id="1d907-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1d907-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1d907-118">Return value</span></span>

<span data-ttu-id="1d907-119">I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="1d907-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1d907-120">Costante</span><span class="sxs-lookup"><span data-stu-id="1d907-120">Constant</span></span>  |<span data-ttu-id="1d907-121">Value</span><span class="sxs-lookup"><span data-stu-id="1d907-121">Value</span></span>  |<span data-ttu-id="1d907-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1d907-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1d907-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1d907-123">0x80041008</span></span> | <span data-ttu-id="1d907-124">`lEnnumFlags` è diverso da zero e non è uno dei flag specificati.</span><span class="sxs-lookup"><span data-stu-id="1d907-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1d907-125">0</span><span class="sxs-lookup"><span data-stu-id="1d907-125">0</span></span> | <span data-ttu-id="1d907-126">La chiamata di funzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="1d907-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1d907-127">Note</span><span class="sxs-lookup"><span data-stu-id="1d907-127">Remarks</span></span>

<span data-ttu-id="1d907-128">Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) (metodo).</span><span class="sxs-lookup"><span data-stu-id="1d907-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="1d907-129">Questa chiamata al metodo è supportata solo se l'oggetto corrente è una definizione di classe.</span><span class="sxs-lookup"><span data-stu-id="1d907-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="1d907-130">Manipolazione di metodo non è disponibile dal [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) puntatori che puntano a istanze.</span><span class="sxs-lookup"><span data-stu-id="1d907-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="1d907-131">L'ordine in cui vengono enumerati i metodi è garantito a essere invariante per una determinata istanza del [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="1d907-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="1d907-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1d907-132">Requirements</span></span>  
 <span data-ttu-id="1d907-133">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d907-134">**Intestazione:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1d907-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1d907-135">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1d907-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d907-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d907-136">See also</span></span>

- [<span data-ttu-id="1d907-137">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="1d907-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
