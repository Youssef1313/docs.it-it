---
title: Metodo IMetaDataEmit2::SetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0c9f104329818f47597e8735389e5e6205ca617
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777112"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="8aa97-102">Metodo IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="8aa97-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="8aa97-103">Imposta i valori di proprietà per la definizione di parametro generico a cui fanno riferimento al token specificato.</span><span class="sxs-lookup"><span data-stu-id="8aa97-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa97-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8aa97-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aa97-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="8aa97-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="8aa97-106">[in] Il token per la definizione di parametro generico per il quale impostare i valori.</span><span class="sxs-lookup"><span data-stu-id="8aa97-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="8aa97-107">[in] Valore di [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumerazione che descrive il tipo parametro generico.</span><span class="sxs-lookup"><span data-stu-id="8aa97-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="8aa97-108">[in] Facoltativo.</span><span class="sxs-lookup"><span data-stu-id="8aa97-108">[in] Optional.</span></span> <span data-ttu-id="8aa97-109">Il nome del parametro per cui impostare i valori.</span><span class="sxs-lookup"><span data-stu-id="8aa97-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="8aa97-110">[in] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="8aa97-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="8aa97-111">[in] Facoltativo.</span><span class="sxs-lookup"><span data-stu-id="8aa97-111">[in] Optional.</span></span> <span data-ttu-id="8aa97-112">Una matrice con terminazione zero di vincoli di tipo.</span><span class="sxs-lookup"><span data-stu-id="8aa97-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="8aa97-113">I membri della matrice devono essere un' `mdTypeDef`, `mdTypeRef`, o `mdTypeSpec` token di metadati.</span><span class="sxs-lookup"><span data-stu-id="8aa97-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa97-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8aa97-114">Requirements</span></span>  
 <span data-ttu-id="8aa97-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aa97-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa97-116">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8aa97-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8aa97-117">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8aa97-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8aa97-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa97-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa97-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8aa97-119">See also</span></span>

- [<span data-ttu-id="8aa97-120">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8aa97-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8aa97-121">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8aa97-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
