---
title: Metodo IMetaDataImport::EnumUnresolvedMethods
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74d0c2e9777a7bd3d49622fb326ecb6b58fbec07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782540"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="0e7a8-102">Metodo IMetaDataImport::EnumUnresolvedMethods</span><span class="sxs-lookup"><span data-stu-id="0e7a8-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="0e7a8-103">Enumera i token MemberDef che rappresentano i metodi non risolti nell'ambito dei metadati corrente.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e7a8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0e7a8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e7a8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0e7a8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0e7a8-106">[in, out] Un puntatore all'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0e7a8-107">Per la prima chiamata di questo metodo deve essere NULL.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="0e7a8-108">[out] Matrice utilizzata per archiviare i token MemberDef.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0e7a8-109">[in] Dimensione massima della matrice `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0e7a8-110">[out] Il numero di token MemberDef restituiti in `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e7a8-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0e7a8-111">Return Value</span></span>  
  
|<span data-ttu-id="0e7a8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e7a8-112">HRESULT</span></span>|<span data-ttu-id="0e7a8-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0e7a8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0e7a8-114">`EnumUnresolvedMethods` stato restituito correttamente.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0e7a8-115">Non sono presenti token da enumerare.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0e7a8-116">In tal caso, `pcTokens` è uguale a zero.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e7a8-117">Note</span><span class="sxs-lookup"><span data-stu-id="0e7a8-117">Remarks</span></span>  
 <span data-ttu-id="0e7a8-118">Un metodo non risolto è quello che è stata dichiarata ma non implementato.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="0e7a8-119">Un metodo è incluso nell'enumerazione se il metodo è contrassegnato `miForwardRef` e il valore `mdPinvokeImpl` o `miRuntime` è impostato su zero.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="0e7a8-120">In altre parole, un metodo non risolto è un metodo di classe contrassegnato `miForwardRef` ma che non viene implementato in codice non gestito (raggiunto tramite PInvoke) né implementati internamente dal runtime stesso.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="0e7a8-121">L'enumerazione esclude tutti i metodi definiti nell'ambito del modulo (variabili globali) o in classi astratte o interfacce.</span><span class="sxs-lookup"><span data-stu-id="0e7a8-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e7a8-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0e7a8-122">Requirements</span></span>  
 <span data-ttu-id="0e7a8-123">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e7a8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e7a8-124">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0e7a8-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e7a8-125">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0e7a8-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e7a8-126">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e7a8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7a8-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e7a8-127">See also</span></span>

- [<span data-ttu-id="0e7a8-128">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0e7a8-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0e7a8-129">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0e7a8-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
