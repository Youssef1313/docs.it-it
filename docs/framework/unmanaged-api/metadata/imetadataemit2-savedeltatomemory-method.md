---
title: Metodo IMetaDataEmit2::SaveDeltaToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79b21613ba844ca4c749d9c04d75260e326e6512
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777136"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="daecd-102">Metodo IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="daecd-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="daecd-103">Salva le modifiche dalla sessione corrente di modifica e continuazione per la memoria.</span><span class="sxs-lookup"><span data-stu-id="daecd-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daecd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="daecd-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daecd-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="daecd-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="daecd-106">[out] L'indirizzo in corrispondenza del quale iniziare a scrivere il delta di metadati.</span><span class="sxs-lookup"><span data-stu-id="daecd-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="daecd-107">[in] Le dimensioni delle modifiche.</span><span class="sxs-lookup"><span data-stu-id="daecd-107">[in] The size of the changes.</span></span> <span data-ttu-id="daecd-108">Uso [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) per determinare le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="daecd-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daecd-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="daecd-109">Requirements</span></span>  
 <span data-ttu-id="daecd-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daecd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daecd-111">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="daecd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="daecd-112">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="daecd-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="daecd-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daecd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daecd-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="daecd-114">See also</span></span>

- [<span data-ttu-id="daecd-115">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="daecd-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="daecd-116">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="daecd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
