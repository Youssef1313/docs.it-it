---
title: Metodo IMetaDataEmit::DeleteFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 652169c67461c1663c005dd014290c4cf2d993ba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434375"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="1cc4e-102">Metodo IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="1cc4e-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="1cc4e-103">Elimina la firma dei metadati di marshalling PInvoke per l'oggetto a cui fa riferimento il token specificato.</span><span class="sxs-lookup"><span data-stu-id="1cc4e-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc4e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1cc4e-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cc4e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="1cc4e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1cc4e-106">in Token `mdFieldDef` o `mdParamDef` che rappresenta il campo o il parametro per il quale eliminare la firma dei metadati di marshalling.</span><span class="sxs-lookup"><span data-stu-id="1cc4e-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cc4e-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1cc4e-107">Requirements</span></span>  
 <span data-ttu-id="1cc4e-108">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc4e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc4e-109">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1cc4e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cc4e-110">**Libreria:** Usato come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1cc4e-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cc4e-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc4e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc4e-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1cc4e-112">See also</span></span>

- [<span data-ttu-id="1cc4e-113">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1cc4e-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1cc4e-114">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1cc4e-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
