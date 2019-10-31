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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132423"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="43058-102">Struttura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="43058-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="43058-103">Definisce la versione del prodotto di Common Language Runtime (CLR) per fini di debug.</span><span class="sxs-lookup"><span data-stu-id="43058-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43058-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43058-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="43058-105">Members</span><span class="sxs-lookup"><span data-stu-id="43058-105">Members</span></span>  
  
|<span data-ttu-id="43058-106">Member</span><span class="sxs-lookup"><span data-stu-id="43058-106">Member</span></span>|<span data-ttu-id="43058-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43058-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="43058-108">Numero di versione della struttura</span><span class="sxs-lookup"><span data-stu-id="43058-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="43058-109">Numero di versione principale.</span><span class="sxs-lookup"><span data-stu-id="43058-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="43058-110">Numero di versione secondario.</span><span class="sxs-lookup"><span data-stu-id="43058-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="43058-111">Numero di Build.</span><span class="sxs-lookup"><span data-stu-id="43058-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="43058-112">Numero di revisione.</span><span class="sxs-lookup"><span data-stu-id="43058-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43058-113">Note</span><span class="sxs-lookup"><span data-stu-id="43058-113">Remarks</span></span>  
 <span data-ttu-id="43058-114">La struttura di `CLR_DEBUGGING_VERSION` corrisponde alla struttura COR_VERSION, tuttavia, la struttura `CLR_DEBUGGING_VERSION` fornisce un campo della versione della struttura aggiuntiva (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="43058-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="43058-115">Attualmente, questo campo deve essere impostato su zero.</span><span class="sxs-lookup"><span data-stu-id="43058-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43058-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="43058-116">Requirements</span></span>  
 <span data-ttu-id="43058-117">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43058-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43058-118">**Intestazione:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="43058-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="43058-119">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43058-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43058-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43058-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43058-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43058-121">See also</span></span>

- [<span data-ttu-id="43058-122">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="43058-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="43058-123">Debug</span><span class="sxs-lookup"><span data-stu-id="43058-123">Debugging</span></span>](index.md)
