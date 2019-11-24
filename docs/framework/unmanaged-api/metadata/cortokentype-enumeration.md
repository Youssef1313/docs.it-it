---
title: Enumerazione CorTokenType
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 74807a678b5c0c2738f33fe552f6462af93ca1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436461"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="e655b-102">Enumerazione CorTokenType</span><span class="sxs-lookup"><span data-stu-id="e655b-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="e655b-103">Indicates the type of a metadata token.</span><span class="sxs-lookup"><span data-stu-id="e655b-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e655b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e655b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="e655b-105">Members</span><span class="sxs-lookup"><span data-stu-id="e655b-105">Members</span></span>  
  
|<span data-ttu-id="e655b-106">Member</span><span class="sxs-lookup"><span data-stu-id="e655b-106">Member</span></span>|<span data-ttu-id="e655b-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e655b-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="e655b-108">An `mdModule` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="e655b-109">An `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="e655b-110">An `mdTypeDef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="e655b-111">An `mdFieldDef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="e655b-112">An `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="e655b-113">An `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="e655b-114">An `mdInterfaceImpl` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="e655b-115">An `mdMemberRef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="e655b-116">An `mdCustomAttribute` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="e655b-117">An `mdPermission` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="e655b-118">An `mdSignature` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="e655b-119">An `mdEvent` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="e655b-120">An `mdProperty` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="e655b-121">An `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="e655b-122">An `mdTypeSpec` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="e655b-123">An `mdAssembly` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="e655b-124">An `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="e655b-125">An `mdFile` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="e655b-126">An `mdExportedType` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="e655b-127">An `mdManifestResource` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="e655b-128">An `mdGenericParam` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="e655b-129">An `mdMethodSpec` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="e655b-130">An `mdGenericParamConstraint` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="e655b-131">An `mdString` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="e655b-132">An `mdName` token.</span><span class="sxs-lookup"><span data-stu-id="e655b-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="e655b-133">Non usato.</span><span class="sxs-lookup"><span data-stu-id="e655b-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e655b-134">Note</span><span class="sxs-lookup"><span data-stu-id="e655b-134">Remarks</span></span>  
 <span data-ttu-id="e655b-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span><span class="sxs-lookup"><span data-stu-id="e655b-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e655b-136">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e655b-136">Requirements</span></span>  
 <span data-ttu-id="e655b-137">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e655b-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e655b-138">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e655b-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e655b-139">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e655b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e655b-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e655b-140">See also</span></span>

- [<span data-ttu-id="e655b-141">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="e655b-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
