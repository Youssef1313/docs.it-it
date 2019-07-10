---
title: Get (riferimenti alle API non gestite) (funzione)
description: La funzione Get recupera il valore della proprietà specificata.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1f838c26d45c0f3cfbd50ac0ce02d234b82ddae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746668"
---
# <a name="get-function"></a><span data-ttu-id="1ca9f-103">Funzione Get</span><span class="sxs-lookup"><span data-stu-id="1ca9f-103">Get function</span></span>

<span data-ttu-id="1ca9f-104">Recupera il valore della proprietà specificata, se presente.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1ca9f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1ca9f-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a><span data-ttu-id="1ca9f-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="1ca9f-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1ca9f-107">[in] Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1ca9f-108">[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="1ca9f-109">[in] Il nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="1ca9f-110">[in] Riservato.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-110">[in] Reserved.</span></span> <span data-ttu-id="1ca9f-111">Questo parametro deve essere 0.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="1ca9f-112">[out] Se la funzione termina correttamente, contiene il valore della `wszName` proprietà.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="1ca9f-113">Il `pval` argomento è assegnato il tipo corretto e il valore del qualificatore.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="1ca9f-114">[out] Se la funzione termina correttamente, contiene un [costante di tipo CIM](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) che indica il tipo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="1ca9f-115">Il valore può anche essere `null`.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="1ca9f-116">[out] Se la funzione termina correttamente, riceve informazioni sull'origine della proprietà.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="1ca9f-117">Il valore può essere `null`, o una delle seguenti costanti WBEM_FLAVOR_TYPE definite nel *WbemCli.h* file di intestazione:</span><span class="sxs-lookup"><span data-stu-id="1ca9f-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="1ca9f-118">Costante</span><span class="sxs-lookup"><span data-stu-id="1ca9f-118">Constant</span></span>  |<span data-ttu-id="1ca9f-119">Value</span><span class="sxs-lookup"><span data-stu-id="1ca9f-119">Value</span></span>  |<span data-ttu-id="1ca9f-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1ca9f-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="1ca9f-121">0x40</span><span class="sxs-lookup"><span data-stu-id="1ca9f-121">0x40</span></span> | <span data-ttu-id="1ca9f-122">La proprietà è una proprietà di sistema standard.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="1ca9f-123">0x20</span><span class="sxs-lookup"><span data-stu-id="1ca9f-123">0x20</span></span> | <span data-ttu-id="1ca9f-124">Per una classe: La proprietà viene ereditata dalla classe padre.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="1ca9f-125">Per un'istanza: La proprietà, mentre ereditata dalla classe padre, non modificata dall'istanza.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="1ca9f-126">0</span><span class="sxs-lookup"><span data-stu-id="1ca9f-126">0</span></span> | <span data-ttu-id="1ca9f-127">Per una classe: La proprietà appartiene alla classe derivata.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="1ca9f-128">Per un'istanza: La proprietà viene modificata tramite l'istanza. vale a dire, è stato fornito un valore o un qualificatore è stato aggiunto o modificato.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1ca9f-129">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1ca9f-129">Return value</span></span>

<span data-ttu-id="1ca9f-130">I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="1ca9f-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1ca9f-131">Costante</span><span class="sxs-lookup"><span data-stu-id="1ca9f-131">Constant</span></span>  |<span data-ttu-id="1ca9f-132">Value</span><span class="sxs-lookup"><span data-stu-id="1ca9f-132">Value</span></span>  |<span data-ttu-id="1ca9f-133">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1ca9f-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1ca9f-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1ca9f-134">0x80041001</span></span> | <span data-ttu-id="1ca9f-135">Si è verificato un errore generale.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1ca9f-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1ca9f-136">0x80041008</span></span> | <span data-ttu-id="1ca9f-137">Uno o più parametri non vengono.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1ca9f-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1ca9f-138">0x80041002</span></span> | <span data-ttu-id="1ca9f-139">La proprietà specificata non è stata trovata.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1ca9f-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1ca9f-140">0x80041006</span></span> | <span data-ttu-id="1ca9f-141">Memoria insufficiente è disponibile per completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1ca9f-142">0</span><span class="sxs-lookup"><span data-stu-id="1ca9f-142">0</span></span> | <span data-ttu-id="1ca9f-143">La chiamata di funzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1ca9f-144">Note</span><span class="sxs-lookup"><span data-stu-id="1ca9f-144">Remarks</span></span>

<span data-ttu-id="1ca9f-145">Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) (metodo).</span><span class="sxs-lookup"><span data-stu-id="1ca9f-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="1ca9f-146">Il `Get` funzione può restituire anche le proprietà di sistema.</span><span class="sxs-lookup"><span data-stu-id="1ca9f-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="1ca9f-147">Il `pVal` argomento è assegnato il tipo corretto e il valore per il qualificatore e il modello COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) (funzione)</span><span class="sxs-lookup"><span data-stu-id="1ca9f-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="1ca9f-148">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ca9f-148">Requirements</span></span>

 <span data-ttu-id="1ca9f-149">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca9f-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1ca9f-150">**Intestazione:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1ca9f-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="1ca9f-151">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca9f-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca9f-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ca9f-152">See also</span></span>

- [<span data-ttu-id="1ca9f-153">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="1ca9f-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
