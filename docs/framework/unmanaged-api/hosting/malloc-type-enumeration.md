---
title: Enumerazione MALLOC_TYPE
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090830"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="10283-102">Enumerazione MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="10283-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="10283-103">Contiene valori che specificano le caratteristiche della memoria da allocare.</span><span class="sxs-lookup"><span data-stu-id="10283-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10283-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="10283-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="10283-105">Members</span><span class="sxs-lookup"><span data-stu-id="10283-105">Members</span></span>  
  
|<span data-ttu-id="10283-106">Member</span><span class="sxs-lookup"><span data-stu-id="10283-106">Member</span></span>|<span data-ttu-id="10283-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="10283-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="10283-108">La memoria allocata può contenere un file eseguibile.</span><span class="sxs-lookup"><span data-stu-id="10283-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="10283-109">La memoria allocata è thread-safe.</span><span class="sxs-lookup"><span data-stu-id="10283-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="10283-110">Ovvero, la memoria può essere accessibile da più thread senza sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="10283-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="10283-111">Se questo flag non è impostato, le chiamate all'oggetto devono essere serializzate.</span><span class="sxs-lookup"><span data-stu-id="10283-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10283-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="10283-112">Requirements</span></span>  
 <span data-ttu-id="10283-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10283-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10283-114">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10283-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10283-115">**Libreria:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10283-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10283-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10283-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10283-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10283-117">See also</span></span>

- [<span data-ttu-id="10283-118">Enumerazioni di hosting</span><span class="sxs-lookup"><span data-stu-id="10283-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
