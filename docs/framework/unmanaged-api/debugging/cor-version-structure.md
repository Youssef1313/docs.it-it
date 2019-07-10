---
title: Struttura COR_VERSION
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f0a36d186c6d9788d43b075bf9d67c36ed1acb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740562"
---
# <a name="corversion-structure"></a><span data-ttu-id="b564f-102">Struttura COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="b564f-102">COR_VERSION Structure</span></span>
<span data-ttu-id="b564f-103">Archivia il numero di versione in quattro parti standard di Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="b564f-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b564f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b564f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="b564f-105">Membri</span><span class="sxs-lookup"><span data-stu-id="b564f-105">Members</span></span>  
  
|<span data-ttu-id="b564f-106">Member</span><span class="sxs-lookup"><span data-stu-id="b564f-106">Member</span></span>|<span data-ttu-id="b564f-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b564f-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="b564f-108">Numero di versione principale.</span><span class="sxs-lookup"><span data-stu-id="b564f-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="b564f-109">Numero di versione secondario.</span><span class="sxs-lookup"><span data-stu-id="b564f-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="b564f-110">Il numero di build.</span><span class="sxs-lookup"><span data-stu-id="b564f-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="b564f-111">Il numero di build secondaria.</span><span class="sxs-lookup"><span data-stu-id="b564f-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b564f-112">Note</span><span class="sxs-lookup"><span data-stu-id="b564f-112">Remarks</span></span>  
 <span data-ttu-id="b564f-113">Se il numero di versione è 1.0.3705.288, il numero di versione principale è 1, 0 è il numero di versione secondaria, 3705 è il numero di build e 288 è il numero di build secondaria.</span><span class="sxs-lookup"><span data-stu-id="b564f-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b564f-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b564f-114">Requirements</span></span>  
 <span data-ttu-id="b564f-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b564f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b564f-116">**Intestazione:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b564f-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b564f-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b564f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b564f-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b564f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b564f-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b564f-119">See also</span></span>

- [<span data-ttu-id="b564f-120">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="b564f-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b564f-121">Debug</span><span class="sxs-lookup"><span data-stu-id="b564f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
