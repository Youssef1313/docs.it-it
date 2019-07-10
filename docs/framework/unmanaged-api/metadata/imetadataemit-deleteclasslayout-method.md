---
title: Metodo IMetaDataEmit::DeleteClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84de8e3c688a23198762fca5219d317fabb69c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777463"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="ce9d2-102">Metodo IMetaDataEmit::DeleteClassLayout</span><span class="sxs-lookup"><span data-stu-id="ce9d2-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="ce9d2-103">Elimina definitivamente la firma dei metadati di layout di classe per il tipo rappresentato dal token specificato.</span><span class="sxs-lookup"><span data-stu-id="ce9d2-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9d2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ce9d2-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9d2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ce9d2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ce9d2-106">[in] Un `mdTypeDef` token di metadati che rappresenta il tipo per il quale verrà eliminato il layout della classe.</span><span class="sxs-lookup"><span data-stu-id="ce9d2-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9d2-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ce9d2-107">Requirements</span></span>  
 <span data-ttu-id="ce9d2-108">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9d2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9d2-109">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ce9d2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce9d2-110">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ce9d2-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce9d2-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9d2-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce9d2-112">See also</span></span>

- [<span data-ttu-id="ce9d2-113">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ce9d2-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ce9d2-114">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ce9d2-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
