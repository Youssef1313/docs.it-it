---
title: Metodo IMetaDataEmit::DefineEvent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432559"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="d44db-102">Metodo IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="d44db-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="d44db-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span><span class="sxs-lookup"><span data-stu-id="d44db-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44db-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d44db-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d44db-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d44db-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d44db-106">[in] The token for the target class or interface.</span><span class="sxs-lookup"><span data-stu-id="d44db-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="d44db-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="d44db-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="d44db-108">[in] The name of the event.</span><span class="sxs-lookup"><span data-stu-id="d44db-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="d44db-109">[in] Event flags.</span><span class="sxs-lookup"><span data-stu-id="d44db-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="d44db-110">[in] The token for the event class.</span><span class="sxs-lookup"><span data-stu-id="d44db-110">[in] The token for the event class.</span></span> <span data-ttu-id="d44db-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="d44db-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="d44db-112">[in] The method used to subscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="d44db-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="d44db-113">[in] The method used to unsubscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="d44db-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="d44db-114">[in] The method used (by a derived class) to raise the event.</span><span class="sxs-lookup"><span data-stu-id="d44db-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d44db-115">[in] An array of tokens for other methods associated with the event.</span><span class="sxs-lookup"><span data-stu-id="d44db-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="d44db-116">The array is terminated with a `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="d44db-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="d44db-117">[out] The metadata token assigned to the event.</span><span class="sxs-lookup"><span data-stu-id="d44db-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44db-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d44db-118">Requirements</span></span>  
 <span data-ttu-id="d44db-119">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44db-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44db-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d44db-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d44db-121">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d44db-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d44db-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44db-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44db-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d44db-123">See also</span></span>

- [<span data-ttu-id="d44db-124">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d44db-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d44db-125">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d44db-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
