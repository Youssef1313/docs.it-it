---
title: Metodo IMetaDataEmit::SetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: baee8566e923f9cb31868f8aa0e379ff1dfa42fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777219"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="ec5bd-102">Metodo IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="ec5bd-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="ec5bd-103">Imposta le funzionalità di un tipo definito da una chiamata precedente a [DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec5bd-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5bd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ec5bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec5bd-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ec5bd-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ec5bd-106">[in] Un' `mdTypeDef` token ottenuto dalla chiamata originale a [DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec5bd-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="ec5bd-107">[in] `TypeDef` attributi.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="ec5bd-108">Si tratta di una maschera di bit delle `CorTypeAttr` valori.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="ec5bd-109">[in] Il `mdToken` della classe di base.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="ec5bd-110">Ottenuto da una chiamata precedente a [DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), o `null`.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="ec5bd-111">[in] Matrice dei token per le interfacce implementate da questo tipo.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="ec5bd-112">Questi `mdTypeRef` i token vengano ottenuti utilizzando [DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec5bd-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="ec5bd-113">È l'ultimo elemento della matrice deve essere `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="ec5bd-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec5bd-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ec5bd-114">Requirements</span></span>  
 <span data-ttu-id="ec5bd-115">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec5bd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec5bd-116">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec5bd-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec5bd-117">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ec5bd-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec5bd-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec5bd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5bd-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec5bd-119">See also</span></span>

- [<span data-ttu-id="ec5bd-120">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ec5bd-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ec5bd-121">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ec5bd-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
