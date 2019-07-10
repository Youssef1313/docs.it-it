---
title: Struttura CLR_DEBUGGING_VERSION
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e71a1538e42061c6cb949b22bb63fe6b17a0dfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741115"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="7b862-102">Struttura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="7b862-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="7b862-103">Definisce la versione del prodotto di Common Language Runtime (CLR) per fini di debug.</span><span class="sxs-lookup"><span data-stu-id="7b862-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b862-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7b862-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="7b862-105">Membri</span><span class="sxs-lookup"><span data-stu-id="7b862-105">Members</span></span>  
  
|<span data-ttu-id="7b862-106">Member</span><span class="sxs-lookup"><span data-stu-id="7b862-106">Member</span></span>|<span data-ttu-id="7b862-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7b862-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="7b862-108">Il numero di versione della struttura</span><span class="sxs-lookup"><span data-stu-id="7b862-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="7b862-109">Numero di versione principale.</span><span class="sxs-lookup"><span data-stu-id="7b862-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="7b862-110">Numero di versione secondario.</span><span class="sxs-lookup"><span data-stu-id="7b862-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="7b862-111">Il numero di build.</span><span class="sxs-lookup"><span data-stu-id="7b862-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="7b862-112">Il numero di revisione.</span><span class="sxs-lookup"><span data-stu-id="7b862-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b862-113">Note</span><span class="sxs-lookup"><span data-stu-id="7b862-113">Remarks</span></span>  
 <span data-ttu-id="7b862-114">Il `CLR_DEBUGGING_VERSION` struttura è uguale alla struttura COR_VERSION, tuttavia, il `CLR_DEBUGGING_VERSION` struttura fornisce un campo della versione struttura aggiuntiva (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="7b862-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="7b862-115">Attualmente, questo campo deve essere impostato su zero.</span><span class="sxs-lookup"><span data-stu-id="7b862-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b862-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7b862-116">Requirements</span></span>  
 <span data-ttu-id="7b862-117">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b862-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b862-118">**Intestazione:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="7b862-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7b862-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b862-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b862-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b862-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b862-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b862-121">See also</span></span>

- [<span data-ttu-id="7b862-122">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="7b862-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="7b862-123">Debug</span><span class="sxs-lookup"><span data-stu-id="7b862-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
