---
title: Metodo IMetaDataImport::ResetEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 3f965ab215ff861c6df61de82dcbbea6b389c8da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426771"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="f74ea-102">Metodo IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="f74ea-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="f74ea-103">Reimposta l'enumeratore specificato nella posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="f74ea-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f74ea-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f74ea-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f74ea-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f74ea-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f74ea-106">[in] The enumerator to reset.</span><span class="sxs-lookup"><span data-stu-id="f74ea-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="f74ea-107">[in] The new position at which to place the enumerator.</span><span class="sxs-lookup"><span data-stu-id="f74ea-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f74ea-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f74ea-108">Requirements</span></span>  
 <span data-ttu-id="f74ea-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f74ea-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f74ea-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f74ea-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f74ea-111">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f74ea-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f74ea-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f74ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f74ea-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f74ea-113">See also</span></span>

- [<span data-ttu-id="f74ea-114">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f74ea-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f74ea-115">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f74ea-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
