---
title: Struttura ASSEMBLYMETADATA
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444263"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="f3ac7-102">Struttura ASSEMBLYMETADATA</span><span class="sxs-lookup"><span data-stu-id="f3ac7-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="f3ac7-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ac7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f3ac7-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="f3ac7-105">Members</span><span class="sxs-lookup"><span data-stu-id="f3ac7-105">Members</span></span>  
  
|<span data-ttu-id="f3ac7-106">Member</span><span class="sxs-lookup"><span data-stu-id="f3ac7-106">Member</span></span>|<span data-ttu-id="f3ac7-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f3ac7-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="f3ac7-108">The major version number of the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="f3ac7-109">This value cannot be zero.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-109">This value cannot be zero.</span></span> <span data-ttu-id="f3ac7-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="f3ac7-111">The minor version number of the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="f3ac7-112">This value cannot be zero.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-112">This value cannot be zero.</span></span> <span data-ttu-id="f3ac7-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="f3ac7-114">The build number of the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="f3ac7-115">This value cannot be zero.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-115">This value cannot be zero.</span></span> <span data-ttu-id="f3ac7-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="f3ac7-117">The revision number of the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="f3ac7-118">This value cannot be zero.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-118">This value cannot be zero.</span></span> <span data-ttu-id="f3ac7-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="f3ac7-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="f3ac7-121">A null value indicates locale independence.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-121">A null value indicates locale independence.</span></span> <span data-ttu-id="f3ac7-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="f3ac7-123">The size in wide characters of `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="f3ac7-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="f3ac7-125">A NULL value indicates processor independence.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="f3ac7-126">The length of the `rdwProcessor` array.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="f3ac7-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="f3ac7-128">A NULL value indicates operating-system independence.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="f3ac7-129">The length of the `rOS` array.</span><span class="sxs-lookup"><span data-stu-id="f3ac7-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3ac7-130">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f3ac7-130">Requirements</span></span>  
 <span data-ttu-id="f3ac7-131">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ac7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ac7-132">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3ac7-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3ac7-133">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3ac7-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3ac7-134">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ac7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ac7-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f3ac7-135">See also</span></span>

- [<span data-ttu-id="f3ac7-136">Strutture di metadati</span><span class="sxs-lookup"><span data-stu-id="f3ac7-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f3ac7-137">Interfaccia IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f3ac7-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="f3ac7-138">Struttura OSINFO</span><span class="sxs-lookup"><span data-stu-id="f3ac7-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
