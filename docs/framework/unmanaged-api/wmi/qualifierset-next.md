---
title: Funzione QualifierSet_Next (riferimenti alle API non gestite)
description: La funzione QualifierSet_Next recupera il qualificatore successivo in un'enumerazione.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ac5cc8633881749bdc167e1b3925a83f7adf3b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760292"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="876f3-103">QualifierSet_Next (funzione)</span><span class="sxs-lookup"><span data-stu-id="876f3-103">QualifierSet_Next function</span></span>
<span data-ttu-id="876f3-104">Recupera il qualificatore successivo in un'enumerazione avviata con una chiamata alla funzione [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="876f3-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="876f3-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="876f3-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="876f3-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="876f3-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="876f3-107">[in] Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="876f3-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="876f3-108">[in] Un puntatore a un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) istanza.</span><span class="sxs-lookup"><span data-stu-id="876f3-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="876f3-109">[in] Riservato.</span><span class="sxs-lookup"><span data-stu-id="876f3-109">[in] Reserved.</span></span> <span data-ttu-id="876f3-110">Questo parametro deve essere 0.</span><span class="sxs-lookup"><span data-stu-id="876f3-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="876f3-111">[out] Il nome del qualificatore.</span><span class="sxs-lookup"><span data-stu-id="876f3-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="876f3-112">Se `null`, questo parametro viene ignorato; in caso contrario, `pstrName` non deve puntare a un valore valido `BSTR` o si verifica una perdita di memoria.</span><span class="sxs-lookup"><span data-stu-id="876f3-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="876f3-113">Se non è null, la funzione alloca sempre una nuova `BSTR` quando viene restituito `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="876f3-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="876f3-114">[out] Al termine, il valore del qualificatore.</span><span class="sxs-lookup"><span data-stu-id="876f3-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="876f3-115">Se la funzione ha esito negativo, il `VARIANT` a cui punta `pVal` non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="876f3-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="876f3-116">Se questo parametro è `null`, il parametro viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="876f3-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="876f3-117">[out] Puntatore a un valore LONG che riceve il contrassegno qualificatore.</span><span class="sxs-lookup"><span data-stu-id="876f3-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="876f3-118">Se non si desiderano informazioni di versione, questo parametro può essere `null`.</span><span class="sxs-lookup"><span data-stu-id="876f3-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="876f3-119">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="876f3-119">Return value</span></span>

<span data-ttu-id="876f3-120">I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="876f3-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="876f3-121">Costante</span><span class="sxs-lookup"><span data-stu-id="876f3-121">Constant</span></span>  |<span data-ttu-id="876f3-122">Value</span><span class="sxs-lookup"><span data-stu-id="876f3-122">Value</span></span>  |<span data-ttu-id="876f3-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="876f3-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="876f3-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="876f3-124">0x80041008</span></span> | <span data-ttu-id="876f3-125">Un parametro non è valido.</span><span class="sxs-lookup"><span data-stu-id="876f3-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="876f3-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="876f3-126">0x8004101d</span></span> | <span data-ttu-id="876f3-127">Il chiamante non ha chiamato [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="876f3-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="876f3-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="876f3-128">0x80041006</span></span> | <span data-ttu-id="876f3-129">Memoria insufficiente è disponibile per iniziare una nuova enumerazione.</span><span class="sxs-lookup"><span data-stu-id="876f3-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="876f3-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="876f3-130">0x40005</span></span> | <span data-ttu-id="876f3-131">Nessun altri qualificatori vengono lasciati nell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="876f3-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="876f3-132">0</span><span class="sxs-lookup"><span data-stu-id="876f3-132">0</span></span> | <span data-ttu-id="876f3-133">La chiamata di funzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="876f3-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="876f3-134">Note</span><span class="sxs-lookup"><span data-stu-id="876f3-134">Remarks</span></span>

<span data-ttu-id="876f3-135">Questa funzione esegue il wrapping di una chiamata per il [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) (metodo).</span><span class="sxs-lookup"><span data-stu-id="876f3-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="876f3-136">Si chiama il `QualifierSet_Next` funzione più volte per enumerare tutti i qualificatori finché la funzione restituita `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="876f3-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="876f3-137">Per terminare l'enumerazione all'inizio, chiamare il [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) (funzione).</span><span class="sxs-lookup"><span data-stu-id="876f3-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="876f3-138">L'ordine dei qualificatori restituito durante l'enumerazione è definito.</span><span class="sxs-lookup"><span data-stu-id="876f3-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="876f3-139">Requisiti</span><span class="sxs-lookup"><span data-stu-id="876f3-139">Requirements</span></span>  
 <span data-ttu-id="876f3-140">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="876f3-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="876f3-141">**Intestazione:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="876f3-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="876f3-142">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="876f3-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876f3-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="876f3-143">See also</span></span>

- [<span data-ttu-id="876f3-144">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="876f3-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
