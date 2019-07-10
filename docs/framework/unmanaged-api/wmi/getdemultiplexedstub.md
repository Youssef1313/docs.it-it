---
title: Funzione GetDemultiplexedStub (riferimenti alle API non gestite)
description: La funzione GetDemultiplexedStub crea un oggetto sink di server d'inoltro per facilitare un client riceve le chiamate asincrone dalla gestione di Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b519ea4062682a56b5b4e277de22b14799f65d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783223"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="a6623-103">GetDemultiplexedStub (funzione)</span><span class="sxs-lookup"><span data-stu-id="a6623-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="a6623-104">Crea un sink di inoltro oggetti per consentire a un client di ricevere chiamate asincrone da Gestione Windows.</span><span class="sxs-lookup"><span data-stu-id="a6623-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a6623-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a6623-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="a6623-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="a6623-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="a6623-107">[in] Un puntatore all'implementazione in-process del client di [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="a6623-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="a6623-108">[in] Un flag che indica se l'evento è locale (`true`); in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="a6623-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="a6623-109">[out] Un sink di server d'inoltro di oggetto per facilitare un client riceve le chiamate asincrone dalla gestione di Windows.</span><span class="sxs-lookup"><span data-stu-id="a6623-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="a6623-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="a6623-110">Return value</span></span>

<span data-ttu-id="a6623-111">Se la funzione ha esito positivo, il valore restituito è `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="a6623-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="a6623-112">Se la funzione ha esito negativo, il valore restituito è un codice di errore diverso da zero.</span><span class="sxs-lookup"><span data-stu-id="a6623-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="a6623-113">Per ottenere informazioni sull'errore, chiamare il [GetErrorInfo](geterrorinfo.md) (funzione).</span><span class="sxs-lookup"><span data-stu-id="a6623-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="a6623-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a6623-114">Requirements</span></span>  
 <span data-ttu-id="a6623-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6623-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6623-116">**Intestazione:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a6623-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a6623-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6623-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6623-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a6623-118">See also</span></span>

- [<span data-ttu-id="a6623-119">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="a6623-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
