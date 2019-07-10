---
title: Metodo IMetaDataImport::EnumMethodImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8be30e8c3b6bc7c03ede5f897f176e04153003b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781969"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="c9b0a-102">Metodo IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="c9b0a-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="c9b0a-103">Enumera i token MethodBody e MethodDeclaration che rappresentano i metodi del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b0a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c9b0a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9b0a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="c9b0a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c9b0a-106">[in, out] Un puntatore all'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c9b0a-107">Per la prima chiamata di questo metodo deve essere NULL.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="c9b0a-108">[in] Token TypeDef per il tipo di cui implementazioni del metodo da enumerare.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="c9b0a-109">[out] Matrice in cui archiviare i token MethodBody.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="c9b0a-110">[out] Matrice in cui archiviare i token MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c9b0a-111">[in] Le dimensioni massime del `rMethodBody` e `rMethodDecl` matrici.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c9b0a-112">[in] Il numero effettivo di metodi restituiti in `rMethodBody` e `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9b0a-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c9b0a-113">Return Value</span></span>  
  
|<span data-ttu-id="c9b0a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9b0a-114">HRESULT</span></span>|<span data-ttu-id="c9b0a-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c9b0a-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c9b0a-116">`EnumMethodImpls` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c9b0a-117">Non sono presenti token di metodo da enumerare.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="c9b0a-118">In tal caso, `pcTokens` è uguale a zero.</span><span class="sxs-lookup"><span data-stu-id="c9b0a-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9b0a-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c9b0a-119">Requirements</span></span>  
 <span data-ttu-id="c9b0a-120">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b0a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b0a-121">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c9b0a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9b0a-122">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c9b0a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9b0a-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b0a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b0a-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9b0a-124">See also</span></span>

- [<span data-ttu-id="c9b0a-125">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c9b0a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c9b0a-126">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c9b0a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
