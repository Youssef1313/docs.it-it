---
title: Metodo IMetaDataAssemblyImport::EnumAssemblyRefs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450351"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="869fc-102">Metodo IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="869fc-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="869fc-103">Enumera le istanze di `mdAssemblyRef` definite nel manifesto dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="869fc-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="869fc-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="869fc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="869fc-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="869fc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="869fc-106">[in, out] Puntatore all'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="869fc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="869fc-107">Deve essere un valore null quando viene chiamato il metodo `EnumAssemblyRefs` per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="869fc-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="869fc-108">out Enumerazione dei token di metadati `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="869fc-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="869fc-109">in Numero massimo di token che possono essere inseriti nella matrice `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="869fc-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="869fc-110">out Numero di token effettivamente inseriti in `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="869fc-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="869fc-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="869fc-111">Return Value</span></span>  
  
|<span data-ttu-id="869fc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="869fc-112">HRESULT</span></span>|<span data-ttu-id="869fc-113">description</span><span class="sxs-lookup"><span data-stu-id="869fc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="869fc-114">`EnumAssemblyRefs` ha restituito un esito positivo.</span><span class="sxs-lookup"><span data-stu-id="869fc-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="869fc-115">Nessun token da enumerare.</span><span class="sxs-lookup"><span data-stu-id="869fc-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="869fc-116">In questo caso, `pcTokens` è impostato su zero.</span><span class="sxs-lookup"><span data-stu-id="869fc-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="869fc-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="869fc-117">Requirements</span></span>  
 <span data-ttu-id="869fc-118">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="869fc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="869fc-119">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="869fc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="869fc-120">**Libreria:** Usato come risorsa in MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="869fc-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="869fc-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="869fc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869fc-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="869fc-122">See also</span></span>

- [<span data-ttu-id="869fc-123">Interfaccia IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="869fc-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
