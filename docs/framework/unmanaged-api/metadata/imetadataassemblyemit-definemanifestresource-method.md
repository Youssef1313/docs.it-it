---
title: Metodo IMetaDataAssemblyEmit::DefineManifestResource
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781953fe5bf209f195ef4887dff45e1902741f0c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775315"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="ceccf-102">Metodo IMetaDataAssemblyEmit::DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="ceccf-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="ceccf-103">Crea una struttura `ManifestResource` che contiene i metadati per la risorsa di manifesto specificata e restituisce il token di metadati associato.</span><span class="sxs-lookup"><span data-stu-id="ceccf-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceccf-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ceccf-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceccf-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ceccf-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ceccf-106">[in] Il nome della risorsa.</span><span class="sxs-lookup"><span data-stu-id="ceccf-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="ceccf-107">[in] Un token di metadati di tipo `mdtFile` o `mdtAssemblyRef` che esegue il mapping al provider di risorse.</span><span class="sxs-lookup"><span data-stu-id="ceccf-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="ceccf-108">Un valore NULL indica che il file in cui sono incorporati i metadati sia il provider di risorse.</span><span class="sxs-lookup"><span data-stu-id="ceccf-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ceccf-109">[in] L'offset all'inizio della risorsa all'interno del file.</span><span class="sxs-lookup"><span data-stu-id="ceccf-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="ceccf-110">Per le risorse in file autonomi, questo valore sarà sempre zero.</span><span class="sxs-lookup"><span data-stu-id="ceccf-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="ceccf-111">Se la risorsa è incorporata in un file di PE (eseguibile), questo è un offset pari a risorse BLOB, che inizia nella posizione specificata nel file di intestazione Cor. h.</span><span class="sxs-lookup"><span data-stu-id="ceccf-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="ceccf-112">[in] Combinazione bit per bit dei valori di flag che specificano le impostazioni delle proprietà per la definizione di risorsa.</span><span class="sxs-lookup"><span data-stu-id="ceccf-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="ceccf-113">[out] Un puntatore al token di metadati restituiti.</span><span class="sxs-lookup"><span data-stu-id="ceccf-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceccf-114">Note</span><span class="sxs-lookup"><span data-stu-id="ceccf-114">Remarks</span></span>  
 <span data-ttu-id="ceccf-115">Uno `ManifestResource` struttura dei metadati deve essere definita per ogni risorsa che viene implementata in ciascuno dei file dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="ceccf-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceccf-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ceccf-116">Requirements</span></span>  
 <span data-ttu-id="ceccf-117">**Piattaforma:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceccf-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceccf-118">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ceccf-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ceccf-119">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ceccf-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ceccf-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceccf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceccf-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ceccf-121">See also</span></span>

- [<span data-ttu-id="ceccf-122">Interfaccia IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="ceccf-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
