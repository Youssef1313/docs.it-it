---
title: Metodo IMetaDataImport::GetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437121"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="729ef-102">Metodo IMetaDataImport::GetParamProps</span><span class="sxs-lookup"><span data-stu-id="729ef-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="729ef-103">Ottiene i valori di metadati relativi al parametro a cui fa riferimento il token ParamDef specificato.</span><span class="sxs-lookup"><span data-stu-id="729ef-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729ef-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="729ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="729ef-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="729ef-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="729ef-106">[in] A ParamDef token that represents the parameter to return metadata for.</span><span class="sxs-lookup"><span data-stu-id="729ef-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="729ef-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span><span class="sxs-lookup"><span data-stu-id="729ef-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="729ef-108">[out] The ordinal position of the parameter in the method argument list.</span><span class="sxs-lookup"><span data-stu-id="729ef-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="729ef-109">[out] A buffer to hold the name of the parameter.</span><span class="sxs-lookup"><span data-stu-id="729ef-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="729ef-110">[in] The requested size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="729ef-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="729ef-111">[out] The returned size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="729ef-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="729ef-112">[out] A pointer to any attribute flags associated with the parameter.</span><span class="sxs-lookup"><span data-stu-id="729ef-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="729ef-113">This is a bitmask of `CorParamAttr` values.</span><span class="sxs-lookup"><span data-stu-id="729ef-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="729ef-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="729ef-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="729ef-115">[out] A pointer to a constant string returned by the parameter.</span><span class="sxs-lookup"><span data-stu-id="729ef-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="729ef-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span><span class="sxs-lookup"><span data-stu-id="729ef-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="729ef-117">Note</span><span class="sxs-lookup"><span data-stu-id="729ef-117">Remarks</span></span>

<span data-ttu-id="729ef-118">The sequence values in `pulSequence` begin with 1 for parameters.</span><span class="sxs-lookup"><span data-stu-id="729ef-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="729ef-119">A return value has a sequence number of 0.</span><span class="sxs-lookup"><span data-stu-id="729ef-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="729ef-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="729ef-120">Requirements</span></span>  
 <span data-ttu-id="729ef-121">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="729ef-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="729ef-122">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="729ef-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="729ef-123">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="729ef-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="729ef-124">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="729ef-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729ef-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="729ef-125">See also</span></span>

- [<span data-ttu-id="729ef-126">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="729ef-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="729ef-127">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="729ef-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
