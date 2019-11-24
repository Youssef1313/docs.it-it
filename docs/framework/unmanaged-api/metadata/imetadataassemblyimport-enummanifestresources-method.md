---
title: Metodo IMetaDataAssemblyImport::EnumManifestResources
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449548"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="0ccb2-102">Metodo IMetaDataAssemblyImport::EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="0ccb2-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="0ccb2-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccb2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0ccb2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0ccb2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0ccb2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0ccb2-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0ccb2-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="0ccb2-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0ccb2-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0ccb2-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ccb2-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0ccb2-111">Return Value</span></span>  
  
|<span data-ttu-id="0ccb2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ccb2-112">HRESULT</span></span>|<span data-ttu-id="0ccb2-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0ccb2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ccb2-114">`EnumManifestResources` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0ccb2-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0ccb2-116">In this case, `pcTokens` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ccb2-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0ccb2-117">Requirements</span></span>  
 <span data-ttu-id="0ccb2-118">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ccb2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ccb2-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ccb2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ccb2-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ccb2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ccb2-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ccb2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccb2-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ccb2-122">See also</span></span>

- [<span data-ttu-id="0ccb2-123">Interfaccia IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="0ccb2-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
