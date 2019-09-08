---
title: Funzione ResetSecurity (riferimenti alle API non gestite)
description: La funzione ResetSecurity assegna un token di rappresentazione al thread corrente.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798259"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="f082f-103">ResetSecurity (funzione)</span><span class="sxs-lookup"><span data-stu-id="f082f-103">ResetSecurity function</span></span>
<span data-ttu-id="f082f-104">Assegna il token di rappresentazione fornito al thread corrente.</span><span class="sxs-lookup"><span data-stu-id="f082f-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f082f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f082f-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="f082f-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="f082f-106">Parameters</span></span>

`token`  
<span data-ttu-id="f082f-107">in Token di rappresentazione da associare al thread corrente.</span><span class="sxs-lookup"><span data-stu-id="f082f-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="f082f-108">Il valore può essere `null`.</span><span class="sxs-lookup"><span data-stu-id="f082f-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f082f-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f082f-109">Return value</span></span>

<span data-ttu-id="f082f-110">Se la funzione ha esito positivo, il valore `S_OK` restituito è (0).</span><span class="sxs-lookup"><span data-stu-id="f082f-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="f082f-111">Se la funzione ha esito negativo, il valore restituito è un codice di errore diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="f082f-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="f082f-112">Per ottenere informazioni estese sull'errore, chiamare la funzione [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="f082f-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f082f-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f082f-113">Requirements</span></span>  
 <span data-ttu-id="f082f-114">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f082f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f082f-115">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="f082f-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f082f-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f082f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f082f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f082f-117">See also</span></span>

- [<span data-ttu-id="f082f-118">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="f082f-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
