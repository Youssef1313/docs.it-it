---
title: Funzione GetObjectText (riferimenti alle API non gestite)
description: La funzione GetObjectText restituisce un testo per il rendering di un oggetto in sintassi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746491"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="22a18-103">Funzione GetObjectText</span><span class="sxs-lookup"><span data-stu-id="22a18-103">GetObjectText function</span></span>
<span data-ttu-id="22a18-104">Restituisce un testo per il rendering dell'oggetto nella sintassi del formato MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="22a18-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="22a18-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="22a18-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="22a18-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="22a18-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="22a18-107">[in] Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="22a18-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="22a18-108">[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.</span><span class="sxs-lookup"><span data-stu-id="22a18-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="22a18-109">[in] In genere 0.</span><span class="sxs-lookup"><span data-stu-id="22a18-109">[in] Normally 0.</span></span> <span data-ttu-id="22a18-110">Se `WBEM_FLAG_NO_FLAVORS` (o 0x1) viene specificato, i qualificatori sono inclusi senza informazioni di propagazione o una versione.</span><span class="sxs-lookup"><span data-stu-id="22a18-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="22a18-111">[out] Un puntatore a un `null` in ingresso.</span><span class="sxs-lookup"><span data-stu-id="22a18-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="22a18-112">Restituzione, appena allocato `BSTR` che contiene informazioni sul rendering sintassi MOF dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="22a18-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="22a18-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="22a18-113">Return value</span></span>

<span data-ttu-id="22a18-114">I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="22a18-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="22a18-115">Costante</span><span class="sxs-lookup"><span data-stu-id="22a18-115">Constant</span></span>  |<span data-ttu-id="22a18-116">Value</span><span class="sxs-lookup"><span data-stu-id="22a18-116">Value</span></span>  |<span data-ttu-id="22a18-117">Descrizione</span><span class="sxs-lookup"><span data-stu-id="22a18-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="22a18-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="22a18-118">0x80041001</span></span> | <span data-ttu-id="22a18-119">Si è verificato un errore generale.</span><span class="sxs-lookup"><span data-stu-id="22a18-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="22a18-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="22a18-120">0x80041008</span></span> | <span data-ttu-id="22a18-121">Un parametro non è valido.</span><span class="sxs-lookup"><span data-stu-id="22a18-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="22a18-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="22a18-122">0x80041006</span></span> | <span data-ttu-id="22a18-123">Memoria insufficiente è disponibile per completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="22a18-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="22a18-124">0</span><span class="sxs-lookup"><span data-stu-id="22a18-124">0</span></span> | <span data-ttu-id="22a18-125">La chiamata di funzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="22a18-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="22a18-126">Note</span><span class="sxs-lookup"><span data-stu-id="22a18-126">Remarks</span></span>

<span data-ttu-id="22a18-127">Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) (metodo).</span><span class="sxs-lookup"><span data-stu-id="22a18-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="22a18-128">Il testo MOF restituito non contiene tutte le informazioni sull'oggetto, ma solo le informazioni sufficienti per il file MOF essere in grado di ricreare l'oggetto originale.</span><span class="sxs-lookup"><span data-stu-id="22a18-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="22a18-129">Ad esempio, non i qualificatori propagati o proprietà della classe padre sono incluse.</span><span class="sxs-lookup"><span data-stu-id="22a18-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="22a18-130">Per ricostruire il testo dei parametri di un metodo viene usato l'algoritmo seguente:</span><span class="sxs-lookup"><span data-stu-id="22a18-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="22a18-131">I parametri sono resequenced nell'ordine dei relativi valori di identificatore.</span><span class="sxs-lookup"><span data-stu-id="22a18-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="22a18-132">I parametri specificati come `[in]` e `[out]` vengono combinati in un singolo parametro.</span><span class="sxs-lookup"><span data-stu-id="22a18-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="22a18-133">`pstrObjectText` deve essere un puntatore a un `null` quando viene chiamata la funzione; non deve puntare a una stringa valida prima della chiamata al metodo, perché verrà deallocato non il puntatore del mouse.</span><span class="sxs-lookup"><span data-stu-id="22a18-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="22a18-134">Requisiti</span><span class="sxs-lookup"><span data-stu-id="22a18-134">Requirements</span></span>  
<span data-ttu-id="22a18-135">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a18-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a18-136">**Intestazione:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="22a18-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="22a18-137">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="22a18-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a18-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="22a18-138">See also</span></span>

- [<span data-ttu-id="22a18-139">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="22a18-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
