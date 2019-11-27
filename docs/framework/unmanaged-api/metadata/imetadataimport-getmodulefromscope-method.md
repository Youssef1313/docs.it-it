---
title: Metodo IMetaDataImport::GetModuleFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 026a952e14cda2ef4ebc32ca91006026e920e3c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437362"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="9a942-102">Metodo IMetaDataImport::GetModuleFromScope</span><span class="sxs-lookup"><span data-stu-id="9a942-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="9a942-103">Ottiene un token di metadati per il modulo a cui si fa riferimento nell'ambito dei metadati corrente.</span><span class="sxs-lookup"><span data-stu-id="9a942-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a942-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a942-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a942-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="9a942-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="9a942-106">out Puntatore al token che rappresenta il modulo a cui si fa riferimento nell'ambito dei metadati corrente.</span><span class="sxs-lookup"><span data-stu-id="9a942-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a942-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9a942-107">Requirements</span></span>  
 <span data-ttu-id="9a942-108">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a942-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a942-109">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9a942-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a942-110">**Libreria:** Incluso come risorsa in MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a942-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a942-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a942-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a942-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a942-112">See also</span></span>

- [<span data-ttu-id="9a942-113">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9a942-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a942-114">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9a942-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
