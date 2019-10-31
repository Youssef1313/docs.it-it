---
title: Funzione InheritsFrom (riferimenti alle API non gestite)
description: La funzione InheritsFrom determina se una classe o un'istanza deriva da una classe padre specifica.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6bda63377251e3a208dfb1620896535ccdf8ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127435"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="f6584-103">InheritsFrom (funzione)</span><span class="sxs-lookup"><span data-stu-id="f6584-103">InheritsFrom function</span></span>
<span data-ttu-id="f6584-104">Determina se la classe o l'istanza corrente deriva da una classe padre specificata.</span><span class="sxs-lookup"><span data-stu-id="f6584-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f6584-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6584-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f6584-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="f6584-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f6584-107">in Questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="f6584-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f6584-108">in Puntatore a un'istanza di [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="f6584-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="f6584-109">in Nome della classe.</span><span class="sxs-lookup"><span data-stu-id="f6584-109">[in] The name of the class.</span></span> <span data-ttu-id="f6584-110">`wszAncestor` deve puntare a una `LPCWSTR`valida.</span><span class="sxs-lookup"><span data-stu-id="f6584-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6584-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f6584-111">Return value</span></span>

<span data-ttu-id="f6584-112">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="f6584-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f6584-113">Costante</span><span class="sxs-lookup"><span data-stu-id="f6584-113">Constant</span></span>  |<span data-ttu-id="f6584-114">Value</span><span class="sxs-lookup"><span data-stu-id="f6584-114">Value</span></span>  |<span data-ttu-id="f6584-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f6584-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f6584-116">0</span><span class="sxs-lookup"><span data-stu-id="f6584-116">0</span></span> | <span data-ttu-id="f6584-117">L'oggetto corrente eredita da `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f6584-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="f6584-118">1</span><span class="sxs-lookup"><span data-stu-id="f6584-118">1</span></span> | <span data-ttu-id="f6584-119">L'oggetto corrente non eredita da `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f6584-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f6584-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f6584-120">0x80041008</span></span> | <span data-ttu-id="f6584-121">`wszAncestor` è `null`.</span><span class="sxs-lookup"><span data-stu-id="f6584-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f6584-122">Note</span><span class="sxs-lookup"><span data-stu-id="f6584-122">Remarks</span></span>

<span data-ttu-id="f6584-123">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemClassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .</span><span class="sxs-lookup"><span data-stu-id="f6584-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6584-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f6584-124">Requirements</span></span>  
 <span data-ttu-id="f6584-125">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6584-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6584-126">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="f6584-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f6584-127">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f6584-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6584-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6584-128">See also</span></span>

- [<span data-ttu-id="f6584-129">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="f6584-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
