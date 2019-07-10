---
title: Enumerazione CorLocalRefPreservation
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6338034d6714e8770e06ff61994fdf4433eb1684
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781782"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="fc9f8-102">Enumerazione CorLocalRefPreservation</span><span class="sxs-lookup"><span data-stu-id="fc9f8-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="fc9f8-103">Contiene valori di flag per il trattamento dei riferimenti locali.</span><span class="sxs-lookup"><span data-stu-id="fc9f8-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9f8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fc9f8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="fc9f8-105">Membri</span><span class="sxs-lookup"><span data-stu-id="fc9f8-105">Members</span></span>  
  
|<span data-ttu-id="fc9f8-106">Member</span><span class="sxs-lookup"><span data-stu-id="fc9f8-106">Member</span></span>|<span data-ttu-id="fc9f8-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="fc9f8-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="fc9f8-108">Non Preserve riferimenti locali.</span><span class="sxs-lookup"><span data-stu-id="fc9f8-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="fc9f8-109">Mantenere i riferimenti ai tipi locali.</span><span class="sxs-lookup"><span data-stu-id="fc9f8-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="fc9f8-110">Mantenere i riferimenti membro locale.</span><span class="sxs-lookup"><span data-stu-id="fc9f8-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc9f8-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fc9f8-111">Requirements</span></span>  
 <span data-ttu-id="fc9f8-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc9f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9f8-113">**Intestazione:** CorHdr. H</span><span class="sxs-lookup"><span data-stu-id="fc9f8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fc9f8-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc9f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9f8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fc9f8-115">See also</span></span>

- [<span data-ttu-id="fc9f8-116">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="fc9f8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
