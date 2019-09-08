---
title: Funzione GetPropertyQualifierSet (riferimenti alle API non gestite)
description: La funzione GetPropertyQualifierSet Recupera il set di qualificatori per una proprietà.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7bce241d10051e4c6be94cdfa40de23773fb0bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798479"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="4018d-103">GetPropertyQualifierSet (funzione)</span><span class="sxs-lookup"><span data-stu-id="4018d-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="4018d-104">Recupera il qualificatore impostato per una particolare proprietà.</span><span class="sxs-lookup"><span data-stu-id="4018d-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4018d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4018d-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="4018d-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="4018d-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="4018d-107">in Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="4018d-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="4018d-108">in Puntatore a un'istanza di [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="4018d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="4018d-109">in Nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="4018d-109">[in] The property  name.</span></span> <span data-ttu-id="4018d-110">`wszProperty`deve puntare a un oggetto `LPCWSTR`valido.</span><span class="sxs-lookup"><span data-stu-id="4018d-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="4018d-111">out Riceve il puntatore a interfaccia che consente di accedere ai qualificatori della proprietà.</span><span class="sxs-lookup"><span data-stu-id="4018d-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="4018d-112">Il parametro `ppQualSet` non può essere `null`.</span><span class="sxs-lookup"><span data-stu-id="4018d-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="4018d-113">Se si verifica un errore, non viene restituito un nuovo oggetto e il puntatore è impostato in modo da `null`puntare a.</span><span class="sxs-lookup"><span data-stu-id="4018d-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4018d-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4018d-114">Return value</span></span>

<span data-ttu-id="4018d-115">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="4018d-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4018d-116">Costante</span><span class="sxs-lookup"><span data-stu-id="4018d-116">Constant</span></span>  |<span data-ttu-id="4018d-117">Value</span><span class="sxs-lookup"><span data-stu-id="4018d-117">Value</span></span>  |<span data-ttu-id="4018d-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4018d-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="4018d-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4018d-119">0x80041001</span></span> | <span data-ttu-id="4018d-120">Si è verificato un errore generale.</span><span class="sxs-lookup"><span data-stu-id="4018d-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="4018d-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4018d-121">0x80041002</span></span> | <span data-ttu-id="4018d-122">Il metodo specificato non esiste.</span><span class="sxs-lookup"><span data-stu-id="4018d-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4018d-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4018d-123">0x80041006</span></span> | <span data-ttu-id="4018d-124">Memoria insufficiente per completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="4018d-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4018d-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4018d-125">0x80041008</span></span> | <span data-ttu-id="4018d-126">Un parametro è `null`.</span><span class="sxs-lookup"><span data-stu-id="4018d-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="4018d-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="4018d-127">0x80041030</span></span> | <span data-ttu-id="4018d-128">La funzione tenta di ottenere i qualificatori di una proprietà di sistema.</span><span class="sxs-lookup"><span data-stu-id="4018d-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4018d-129">0</span><span class="sxs-lookup"><span data-stu-id="4018d-129">0</span></span> | <span data-ttu-id="4018d-130">La chiamata di funzione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="4018d-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="4018d-131">Note</span><span class="sxs-lookup"><span data-stu-id="4018d-131">Remarks</span></span>

<span data-ttu-id="4018d-132">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="4018d-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="4018d-133">Una chiamata a questa funzione è supportata solo se l'oggetto corrente è una definizione di classe CIM.</span><span class="sxs-lookup"><span data-stu-id="4018d-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="4018d-134">La manipolazione del metodo non è disponibile per i puntatori [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) che puntano a istanze CIM.</span><span class="sxs-lookup"><span data-stu-id="4018d-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="4018d-135">Poiché ogni metodo può avere qualificatori propri, il [puntatore IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) consente al chiamante di aggiungere, modificare o eliminare questi qualificatori.</span><span class="sxs-lookup"><span data-stu-id="4018d-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="4018d-136">Poiché le proprietà di sistema non hanno qualificatori, la `WBEM_E_SYSTEM_PROPERTY` funzione restituisce se si tenta di ottenere un puntatore [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) per una proprietà di sistema.</span><span class="sxs-lookup"><span data-stu-id="4018d-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="4018d-137">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4018d-137">Requirements</span></span>

<span data-ttu-id="4018d-138">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4018d-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4018d-139">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="4018d-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="4018d-140">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4018d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4018d-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4018d-141">See also</span></span>

- [<span data-ttu-id="4018d-142">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="4018d-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
