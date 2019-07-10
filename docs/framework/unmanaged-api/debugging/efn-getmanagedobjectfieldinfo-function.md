---
title: Funzione _EFN_GetManagedObjectFieldInfo
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739004"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="3affa-102">\_EFN\_GetManagedObjectFieldInfo (funzione)</span><span class="sxs-lookup"><span data-stu-id="3affa-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="3affa-103">Ottiene l'offset per un campo dall'inizio di un oggetto e il valore del campo, usando il puntatore all'oggetto e il nome di campo forniti.</span><span class="sxs-lookup"><span data-stu-id="3affa-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3affa-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3affa-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3affa-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3affa-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="3affa-106">[in] Puntatore al client di debug.</span><span class="sxs-lookup"><span data-stu-id="3affa-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="3affa-107">[in] Un puntatore all'oggetto gestito.</span><span class="sxs-lookup"><span data-stu-id="3affa-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="3affa-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="3affa-108">szFieldName</span></span>  
 <span data-ttu-id="3affa-109">[in] Un puntatore all'oggetto gestito per il nome del campo.</span><span class="sxs-lookup"><span data-stu-id="3affa-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3affa-110">[out] Il valore del campo.</span><span class="sxs-lookup"><span data-stu-id="3affa-110">[out] The field value.</span></span> <span data-ttu-id="3affa-111">Questo parametro può essere null.</span><span class="sxs-lookup"><span data-stu-id="3affa-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="3affa-112">[out] L'offset dal `objAddr` al campo.</span><span class="sxs-lookup"><span data-stu-id="3affa-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="3affa-113">Questo parametro può essere null.</span><span class="sxs-lookup"><span data-stu-id="3affa-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3affa-114">Note</span><span class="sxs-lookup"><span data-stu-id="3affa-114">Remarks</span></span>  
 <span data-ttu-id="3affa-115">Se l'offset è 0, non viene scritto alcun offset.</span><span class="sxs-lookup"><span data-stu-id="3affa-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="3affa-116">Se non vi è nessun codice gestito sul thread attualmente nel contesto, la funzione restituisce HRESULT SOS_E_NOMANAGEDCODE con un valore di impianto pari a 0xa0 e un codice di errore di 0x1000.</span><span class="sxs-lookup"><span data-stu-id="3affa-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3affa-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3affa-117">Requirements</span></span>  
 <span data-ttu-id="3affa-118">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3affa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3affa-119">**Intestazione:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="3affa-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="3affa-120">**Versione di .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3affa-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3affa-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3affa-121">See also</span></span>

- [<span data-ttu-id="3affa-122">Funzioni statiche globali di debug</span><span class="sxs-lookup"><span data-stu-id="3affa-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
