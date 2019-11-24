---
title: Metodo IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431697"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="44f12-102">Metodo IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="44f12-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="44f12-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span><span class="sxs-lookup"><span data-stu-id="44f12-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f12-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="44f12-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44f12-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="44f12-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="44f12-106">[in] The token for the method whose parameter is being defined.</span><span class="sxs-lookup"><span data-stu-id="44f12-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="44f12-107">[in] The parameter sequence number.</span><span class="sxs-lookup"><span data-stu-id="44f12-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="44f12-108">[in] The name of the parameter in Unicode.</span><span class="sxs-lookup"><span data-stu-id="44f12-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="44f12-109">[in] Flags for the parameter.</span><span class="sxs-lookup"><span data-stu-id="44f12-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="44f12-110">This is a bitmask of `CorParamAttr` values.</span><span class="sxs-lookup"><span data-stu-id="44f12-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="44f12-111">[in] `ELEMENT_TYPE_` *\** for the constant value.</span><span class="sxs-lookup"><span data-stu-id="44f12-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="44f12-112">[in] The constant value for the parameter.</span><span class="sxs-lookup"><span data-stu-id="44f12-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="44f12-113">[in] The size, in Unicode characters, of `pValue`.</span><span class="sxs-lookup"><span data-stu-id="44f12-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="44f12-114">[out] The `mdParamDef` token assigned.</span><span class="sxs-lookup"><span data-stu-id="44f12-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44f12-115">Note</span><span class="sxs-lookup"><span data-stu-id="44f12-115">Remarks</span></span>  
 <span data-ttu-id="44f12-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span><span class="sxs-lookup"><span data-stu-id="44f12-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="44f12-117">A return value has a sequence number of 0.</span><span class="sxs-lookup"><span data-stu-id="44f12-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44f12-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="44f12-118">Requirements</span></span>  
 <span data-ttu-id="44f12-119">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f12-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f12-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44f12-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44f12-121">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44f12-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44f12-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f12-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f12-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="44f12-123">See also</span></span>

- [<span data-ttu-id="44f12-124">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="44f12-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="44f12-125">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="44f12-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
