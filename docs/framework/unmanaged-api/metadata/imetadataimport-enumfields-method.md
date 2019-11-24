---
title: Metodo IMetaDataImport::EnumFields
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 2d32dc8ae59fc1a4a189d849437cc95ea3b94a4d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449546"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="508d1-102">Metodo IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="508d1-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="508d1-103">Enumera i token FieldDef per il tipo a cui fa riferimento il token TypeDef specificato.</span><span class="sxs-lookup"><span data-stu-id="508d1-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508d1-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="508d1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="508d1-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="508d1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="508d1-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="508d1-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="508d1-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="508d1-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="508d1-108">[out] The list of FieldDef tokens.</span><span class="sxs-lookup"><span data-stu-id="508d1-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="508d1-109">[in] Dimensione massima della matrice `rFields`.</span><span class="sxs-lookup"><span data-stu-id="508d1-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="508d1-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span><span class="sxs-lookup"><span data-stu-id="508d1-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="508d1-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="508d1-111">Return Value</span></span>  
  
|<span data-ttu-id="508d1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="508d1-112">HRESULT</span></span>|<span data-ttu-id="508d1-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="508d1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="508d1-114">`EnumFields` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="508d1-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="508d1-115">There are no fields to enumerate.</span><span class="sxs-lookup"><span data-stu-id="508d1-115">There are no fields to enumerate.</span></span> <span data-ttu-id="508d1-116">In that case, `pcTokens` is zero.</span><span class="sxs-lookup"><span data-stu-id="508d1-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="508d1-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="508d1-117">Requirements</span></span>  
 <span data-ttu-id="508d1-118">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508d1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508d1-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="508d1-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="508d1-120">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="508d1-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="508d1-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508d1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508d1-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="508d1-122">See also</span></span>

- [<span data-ttu-id="508d1-123">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="508d1-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="508d1-124">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="508d1-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
