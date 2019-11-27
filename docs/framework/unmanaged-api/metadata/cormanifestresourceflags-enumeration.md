---
title: Enumerazione CorManifestResourceFlags
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: 35966e25d02bd6f1a9bdd21ad4e9cc44b7bb480e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450251"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="35881-102">Enumerazione CorManifestResourceFlags</span><span class="sxs-lookup"><span data-stu-id="35881-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="35881-103">Indica la visibilità delle risorse codificate in un manifesto dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="35881-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35881-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="35881-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="35881-105">Membri</span><span class="sxs-lookup"><span data-stu-id="35881-105">Members</span></span>  
  
|<span data-ttu-id="35881-106">Membro</span><span class="sxs-lookup"><span data-stu-id="35881-106">Member</span></span>|<span data-ttu-id="35881-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="35881-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="35881-108">Riservato.</span><span class="sxs-lookup"><span data-stu-id="35881-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="35881-109">Le risorse sono pubbliche.</span><span class="sxs-lookup"><span data-stu-id="35881-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="35881-110">Le risorse sono private.</span><span class="sxs-lookup"><span data-stu-id="35881-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35881-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="35881-111">Requirements</span></span>  
 <span data-ttu-id="35881-112">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35881-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35881-113">**Intestazione:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="35881-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="35881-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35881-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35881-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="35881-115">See also</span></span>

- [<span data-ttu-id="35881-116">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="35881-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
