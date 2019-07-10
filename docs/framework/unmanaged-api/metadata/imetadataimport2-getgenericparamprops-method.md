---
title: Metodo IMetaDataImport2::GetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9f6cc1e568463f2ca9afa38c10f50d0c247013
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755347"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="c7a64-102">Metodo IMetaDataImport2::GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="c7a64-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="c7a64-103">Ottiene i metadati associati al parametro generico rappresentato dal token specificato.</span><span class="sxs-lookup"><span data-stu-id="c7a64-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a64-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c7a64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7a64-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="c7a64-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="c7a64-106">[in] Il token che rappresenta il parametro generico per il quale restituire i metadati.</span><span class="sxs-lookup"><span data-stu-id="c7a64-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="c7a64-107">[out] La posizione ordinale del `Type` parametro nel costruttore padre o nel metodo.</span><span class="sxs-lookup"><span data-stu-id="c7a64-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="c7a64-108">[out] Valore di [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumerazione che descrive il `Type` per il parametro generico.</span><span class="sxs-lookup"><span data-stu-id="c7a64-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="c7a64-109">[out] Token TypeDef o MethodDef che rappresenta il proprietario del parametro.</span><span class="sxs-lookup"><span data-stu-id="c7a64-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="c7a64-110">[out] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="c7a64-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="c7a64-111">[out] Il nome del parametro generico.</span><span class="sxs-lookup"><span data-stu-id="c7a64-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c7a64-112">[in] Le dimensioni del `wzName` buffer.</span><span class="sxs-lookup"><span data-stu-id="c7a64-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c7a64-113">[out] Dimensioni restituite del nome, in caratteri "wide".</span><span class="sxs-lookup"><span data-stu-id="c7a64-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a64-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c7a64-114">Requirements</span></span>  
 <span data-ttu-id="c7a64-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a64-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a64-116">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7a64-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7a64-117">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c7a64-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7a64-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a64-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a64-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7a64-119">See also</span></span>

- [<span data-ttu-id="c7a64-120">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c7a64-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="c7a64-121">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c7a64-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
