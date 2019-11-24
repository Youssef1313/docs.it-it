---
title: Metodo IMetaDataImport2::GetMethodSpecProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 6b5b3b3b5a3613668f4470f48083ae010cc9d336
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445249"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="89752-102">Metodo IMetaDataImport2::GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="89752-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="89752-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="89752-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89752-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="89752-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="89752-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="89752-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="89752-106">[in] A MethodSpec token that represents the instantiation of the method.</span><span class="sxs-lookup"><span data-stu-id="89752-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="89752-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span><span class="sxs-lookup"><span data-stu-id="89752-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="89752-108">[out] A pointer to the binary metadata signature of the method.</span><span class="sxs-lookup"><span data-stu-id="89752-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="89752-109">[out] The size, in bytes, of `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="89752-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89752-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="89752-110">Requirements</span></span>  
 <span data-ttu-id="89752-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89752-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89752-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89752-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89752-113">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89752-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89752-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89752-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89752-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89752-115">See also</span></span>

- [<span data-ttu-id="89752-116">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="89752-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="89752-117">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="89752-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
