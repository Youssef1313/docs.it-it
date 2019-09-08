---
title: Funzione QualifierSet_BeginEnumeration (riferimenti alle API non gestite)
description: La funzione QualifierSet_BeginEnumeration Reimposta un enumeratore dei qualificatori di un oggetto.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798341"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="54b4a-103">QualifierSet_BeginEnumeration (funzione)</span><span class="sxs-lookup"><span data-stu-id="54b4a-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="54b4a-104">Reimposta un enumeratore dei qualificatori di un oggetto all'inizio dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="54b4a-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="54b4a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="54b4a-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="54b4a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="54b4a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="54b4a-107">in Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="54b4a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="54b4a-108">in Puntatore a un'istanza di [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="54b4a-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="54b4a-109">in Combinazione bit per bit dei flag o valori descritti nella sezione [osservazioni](#remarks) che specifica i qualificatori da includere nell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="54b4a-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="54b4a-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="54b4a-110">Return value</span></span>

<span data-ttu-id="54b4a-111">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="54b4a-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="54b4a-112">Costante</span><span class="sxs-lookup"><span data-stu-id="54b4a-112">Constant</span></span>  |<span data-ttu-id="54b4a-113">Value</span><span class="sxs-lookup"><span data-stu-id="54b4a-113">Value</span></span>  |<span data-ttu-id="54b4a-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="54b4a-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="54b4a-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="54b4a-115">0x80041008</span></span> | <span data-ttu-id="54b4a-116">Il parametro `lFlags` non è valido.</span><span class="sxs-lookup"><span data-stu-id="54b4a-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="54b4a-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="54b4a-117">0x8004101d</span></span> | <span data-ttu-id="54b4a-118">Una seconda chiamata a `QualifierSet_BeginEnumeration` è stata effettuata senza una chiamata corrispondente a [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="54b4a-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="54b4a-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="54b4a-119">0x80041006</span></span> | <span data-ttu-id="54b4a-120">La memoria disponibile non è sufficiente per iniziare una nuova enumerazione.</span><span class="sxs-lookup"><span data-stu-id="54b4a-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="54b4a-121">0</span><span class="sxs-lookup"><span data-stu-id="54b4a-121">0</span></span> | <span data-ttu-id="54b4a-122">La chiamata di funzione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="54b4a-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="54b4a-123">Note</span><span class="sxs-lookup"><span data-stu-id="54b4a-123">Remarks</span></span>

<span data-ttu-id="54b4a-124">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemQualifierSet:: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .</span><span class="sxs-lookup"><span data-stu-id="54b4a-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="54b4a-125">Per enumerare tutti i qualificatori in un oggetto, questo metodo deve essere chiamato prima della prima chiamata a [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="54b4a-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="54b4a-126">L'ordine in cui vengono enumerati i qualificatori è sicuramente invariante per una determinata enumerazione.</span><span class="sxs-lookup"><span data-stu-id="54b4a-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="54b4a-127">I flag che possono essere passati come `lEnumFlags` argomento vengono definiti nel file di intestazione *WbemCli. h* oppure possono essere definiti come costanti nel codice.</span><span class="sxs-lookup"><span data-stu-id="54b4a-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="54b4a-128">Costante</span><span class="sxs-lookup"><span data-stu-id="54b4a-128">Constant</span></span>  |<span data-ttu-id="54b4a-129">Valore</span><span class="sxs-lookup"><span data-stu-id="54b4a-129">Value</span></span>  |<span data-ttu-id="54b4a-130">Descrizione</span><span class="sxs-lookup"><span data-stu-id="54b4a-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="54b4a-131">0</span><span class="sxs-lookup"><span data-stu-id="54b4a-131">0</span></span> | <span data-ttu-id="54b4a-132">Restituisce i nomi di tutti i qualificatori.</span><span class="sxs-lookup"><span data-stu-id="54b4a-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="54b4a-133">0x10</span><span class="sxs-lookup"><span data-stu-id="54b4a-133">0x10</span></span> | <span data-ttu-id="54b4a-134">Restituisce solo i nomi dei qualificatori specifici della proprietà o dell'oggetto corrente.</span><span class="sxs-lookup"><span data-stu-id="54b4a-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="54b4a-135">Per una proprietà: Restituire solo i qualificatori specifici della proprietà (incluse le sostituzioni) e non i qualificatori propagati dalla definizione della classe.</span><span class="sxs-lookup"><span data-stu-id="54b4a-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="54b4a-136">Per un'istanza: Restituisce solo nomi di qualificatori specifici dell'istanza.</span><span class="sxs-lookup"><span data-stu-id="54b4a-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="54b4a-137">Per una classe: Restituisce solo i qualificatori specifici della classe derivata.</span><span class="sxs-lookup"><span data-stu-id="54b4a-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="54b4a-138">0x20</span><span class="sxs-lookup"><span data-stu-id="54b4a-138">0x20</span></span> | <span data-ttu-id="54b4a-139">Restituisce solo i nomi dei qualificatori propagati da un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="54b4a-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="54b4a-140">Per una proprietà: Restituisce solo i qualificatori propagati a questa proprietà dalla definizione della classe e non da quelli della proprietà stessa.</span><span class="sxs-lookup"><span data-stu-id="54b4a-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="54b4a-141">Per un'istanza: Restituisce solo i qualificatori propagati dalla definizione della classe.</span><span class="sxs-lookup"><span data-stu-id="54b4a-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="54b4a-142">Per una classe: Restituisce solo i nomi dei qualificatori ereditati dalle classi padre.</span><span class="sxs-lookup"><span data-stu-id="54b4a-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="54b4a-143">Requisiti</span><span class="sxs-lookup"><span data-stu-id="54b4a-143">Requirements</span></span>

<span data-ttu-id="54b4a-144">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b4a-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="54b4a-145">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="54b4a-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="54b4a-146">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="54b4a-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="54b4a-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54b4a-147">See also</span></span>

- [<span data-ttu-id="54b4a-148">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="54b4a-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
