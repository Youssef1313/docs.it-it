---
title: Metodo IMetaDataImport::EnumEvents
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f3d74830de0541ec789081c47352beca8d81d74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780703"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="84d70-102">Metodo IMetaDataImport::EnumEvents</span><span class="sxs-lookup"><span data-stu-id="84d70-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="84d70-103">Enumera i token di definizione di evento per il token TypeDef specificato.</span><span class="sxs-lookup"><span data-stu-id="84d70-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84d70-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="84d70-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84d70-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="84d70-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="84d70-106">[in, out] Un puntatore all'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="84d70-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="84d70-107">[in] Il token TypeDef le cui definizioni di evento devono essere enumerati.</span><span class="sxs-lookup"><span data-stu-id="84d70-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="84d70-108">[out] Matrice di eventi restituiti.</span><span class="sxs-lookup"><span data-stu-id="84d70-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="84d70-109">[in] Dimensione massima della matrice `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="84d70-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="84d70-110">[out] Il numero effettivo di eventi restituiti `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="84d70-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84d70-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="84d70-111">Return Value</span></span>  
  
|<span data-ttu-id="84d70-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84d70-112">HRESULT</span></span>|<span data-ttu-id="84d70-113">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="84d70-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="84d70-114">`EnumEvents` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="84d70-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="84d70-115">Non sono presenti eventi da enumerare.</span><span class="sxs-lookup"><span data-stu-id="84d70-115">There are no events to enumerate.</span></span> <span data-ttu-id="84d70-116">In tal caso, `pcEvents` è uguale a zero.</span><span class="sxs-lookup"><span data-stu-id="84d70-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84d70-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="84d70-117">Requirements</span></span>  
 <span data-ttu-id="84d70-118">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84d70-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84d70-119">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="84d70-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84d70-120">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="84d70-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84d70-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84d70-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d70-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="84d70-122">See also</span></span>

- [<span data-ttu-id="84d70-123">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="84d70-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="84d70-124">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="84d70-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
