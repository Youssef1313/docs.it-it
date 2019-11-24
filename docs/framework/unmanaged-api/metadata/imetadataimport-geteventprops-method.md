---
title: Metodo IMetaDataImport::GetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437579"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="b549b-102">Metodo IMetaDataImport::GetEventProps</span><span class="sxs-lookup"><span data-stu-id="b549b-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="b549b-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span><span class="sxs-lookup"><span data-stu-id="b549b-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b549b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b549b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b549b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b549b-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="b549b-106">[in] The event metadata token representing the event to get metadata for.</span><span class="sxs-lookup"><span data-stu-id="b549b-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b549b-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="b549b-108">[out] The name of the event referenced by `ev`.</span><span class="sxs-lookup"><span data-stu-id="b549b-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="b549b-109">[in] The requested length in wide characters of `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b549b-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="b549b-110">[out] The returned length in wide characters of `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b549b-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="b549b-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="b549b-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="b549b-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="b549b-114">[out] A pointer to the metadata token representing the method that raises the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b549b-115">[out] An array of token pointers to other methods associated with the event.</span><span class="sxs-lookup"><span data-stu-id="b549b-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b549b-116">[in] Dimensione massima della matrice `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b549b-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b549b-117">[out] The number of tokens returned in `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b549b-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b549b-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b549b-118">Requirements</span></span>  
 <span data-ttu-id="b549b-119">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b549b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b549b-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b549b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b549b-121">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b549b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b549b-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b549b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b549b-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b549b-123">See also</span></span>

- [<span data-ttu-id="b549b-124">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b549b-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b549b-125">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b549b-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
