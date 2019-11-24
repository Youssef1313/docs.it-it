---
title: Enumerazione CorCallingConvention
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 9d4690cb6adedc77717e577d409cb52b18b1b5ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443829"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="bf6e1-102">Enumerazione CorCallingConvention</span><span class="sxs-lookup"><span data-stu-id="bf6e1-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="bf6e1-103">Contiene valori che descrivono i tipi di convenzioni per le chiamate effettuate in codice gestito.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6e1-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bf6e1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="bf6e1-105">Members</span><span class="sxs-lookup"><span data-stu-id="bf6e1-105">Members</span></span>  
  
|<span data-ttu-id="bf6e1-106">Member</span><span class="sxs-lookup"><span data-stu-id="bf6e1-106">Member</span></span>|<span data-ttu-id="bf6e1-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bf6e1-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="bf6e1-108">Indicates a default calling convention.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="bf6e1-109">Indicates that the method takes a variable number of parameters.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="bf6e1-110">Indicates that the call is to a field.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="bf6e1-111">Indicates that the call is to a local method.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="bf6e1-112">Indicates that the call is to a property.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="bf6e1-113">Indicates that the call is unmanaged.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="bf6e1-114">Indicates a generic method instantiation.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="bf6e1-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="bf6e1-116">Describes an invalid 4-bit value.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="bf6e1-117">Indicates that the calling convention is described by the bottom four bits.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="bf6e1-118">Indicates that the top bit describes a `this` parameter.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="bf6e1-119">Indicates that a `this` parameter is explicitly described in the signature.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="bf6e1-120">Indicates a generic method signature with an explicit number of type arguments.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="bf6e1-121">This precedes an ordinary parameter count.</span><span class="sxs-lookup"><span data-stu-id="bf6e1-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf6e1-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bf6e1-122">Requirements</span></span>  
 <span data-ttu-id="bf6e1-123">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6e1-124">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bf6e1-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bf6e1-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6e1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6e1-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bf6e1-126">See also</span></span>

- [<span data-ttu-id="bf6e1-127">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="bf6e1-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
