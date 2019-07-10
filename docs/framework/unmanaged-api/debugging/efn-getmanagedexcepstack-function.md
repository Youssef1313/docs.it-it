---
title: Funzione _EFN_GetManagedExcepStack
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f4e057a487462feb385ca0e3ca977fdd165f56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739102"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="bac8f-102">\_EFN\_GetManagedExcepStack (funzione)</span><span class="sxs-lookup"><span data-stu-id="bac8f-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="bac8f-103">Restituisce una versione stringa della traccia dello stack contenuta internamente, dato l'indirizzo di un oggetto eccezione gestita.</span><span class="sxs-lookup"><span data-stu-id="bac8f-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac8f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bac8f-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bac8f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bac8f-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="bac8f-106">[in] Il client in fase di debug.</span><span class="sxs-lookup"><span data-stu-id="bac8f-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="bac8f-107">[in] Puntatore a un oggetto gestito, derivato da <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="bac8f-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="bac8f-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="bac8f-108">szStackString</span></span>  
 <span data-ttu-id="bac8f-109">[out] La stringa restituita.</span><span class="sxs-lookup"><span data-stu-id="bac8f-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="bac8f-110">[out] Il numero di caratteri disponibili nel buffer di stringa.</span><span class="sxs-lookup"><span data-stu-id="bac8f-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bac8f-111">Note</span><span class="sxs-lookup"><span data-stu-id="bac8f-111">Remarks</span></span>  
 <span data-ttu-id="bac8f-112">Se non vi è nessun codice gestito sul thread attualmente nel contesto, la funzione restituisce HRESULT SOS_E_NOMANAGEDCODE con un valore di impianto pari a 0xa0 e un codice di errore di 0x1000.</span><span class="sxs-lookup"><span data-stu-id="bac8f-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac8f-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bac8f-113">Requirements</span></span>  
 <span data-ttu-id="bac8f-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac8f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac8f-115">**Intestazione:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="bac8f-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="bac8f-116">**Versione di .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac8f-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac8f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bac8f-117">See also</span></span>

- [<span data-ttu-id="bac8f-118">Funzioni statiche globali di debug</span><span class="sxs-lookup"><span data-stu-id="bac8f-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
