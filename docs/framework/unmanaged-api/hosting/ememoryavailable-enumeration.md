---
title: Enumerazione EMemoryAvailable
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fc5f578e6da731ffd6406344d00cda8b57f493
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772400"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="823be-102">Enumerazione EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="823be-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="823be-103">Contiene valori che indicano la quantità di memoria fisica disponibile nel computer.</span><span class="sxs-lookup"><span data-stu-id="823be-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="823be-104">Questi valori eseguire il mapping logico agli eventi massimo e minimo della memoria restituita dal `CreateMemoryResourceNotification` funzione nell'API di Windows.</span><span class="sxs-lookup"><span data-stu-id="823be-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="823be-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="823be-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="823be-106">Membri</span><span class="sxs-lookup"><span data-stu-id="823be-106">Members</span></span>  
  
|<span data-ttu-id="823be-107">Member</span><span class="sxs-lookup"><span data-stu-id="823be-107">Member</span></span>|<span data-ttu-id="823be-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="823be-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="823be-109">Una notevole quantità di memoria fisica disponibile.</span><span class="sxs-lookup"><span data-stu-id="823be-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="823be-110">Memoria fisica minima è disponibile.</span><span class="sxs-lookup"><span data-stu-id="823be-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="823be-111">La memoria fisica disponibile è neutra.</span><span class="sxs-lookup"><span data-stu-id="823be-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="823be-112">Note</span><span class="sxs-lookup"><span data-stu-id="823be-112">Remarks</span></span>  
 <span data-ttu-id="823be-113">Questo valore viene passato dall'host per common language runtime (CLR) da tramite una chiamata ai [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="823be-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="823be-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="823be-114">Requirements</span></span>  
 <span data-ttu-id="823be-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="823be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="823be-116">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="823be-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="823be-117">**Libreria:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="823be-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="823be-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="823be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823be-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="823be-119">See also</span></span>

- [<span data-ttu-id="823be-120">Enumerazioni di hosting</span><span class="sxs-lookup"><span data-stu-id="823be-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
