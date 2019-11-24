---
title: Metodo IMetaDataImport::EnumMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450072"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="1b5fe-102">Metodo IMetaDataImport::EnumMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="1b5fe-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="1b5fe-103">Enumera le proprietà e gli eventi di modifica delle proprietà a cui è correlato il metodo specificato.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b5fe-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1b5fe-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b5fe-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="1b5fe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1b5fe-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1b5fe-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="1b5fe-108">[in] A MethodDef token that limits the scope of the enumeration.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="1b5fe-109">[out] The array used to store the events or properties.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1b5fe-110">[in] Dimensione massima della matrice `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="1b5fe-111">[out] The number of events or properties returned in `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b5fe-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1b5fe-112">Return Value</span></span>  
  
|<span data-ttu-id="1b5fe-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b5fe-113">HRESULT</span></span>|<span data-ttu-id="1b5fe-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1b5fe-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1b5fe-115">`EnumMethodSemantics` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1b5fe-116">There are no events or properties to enumerate.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="1b5fe-117">In that case, `pcEventProp` is zero.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b5fe-118">Note</span><span class="sxs-lookup"><span data-stu-id="1b5fe-118">Remarks</span></span>  
 <span data-ttu-id="1b5fe-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="1b5fe-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="1b5fe-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="1b5fe-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span><span class="sxs-lookup"><span data-stu-id="1b5fe-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b5fe-123">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1b5fe-123">Requirements</span></span>  
 <span data-ttu-id="1b5fe-124">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b5fe-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b5fe-125">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b5fe-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b5fe-126">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b5fe-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b5fe-127">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5fe-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b5fe-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1b5fe-128">See also</span></span>

- [<span data-ttu-id="1b5fe-129">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1b5fe-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1b5fe-130">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1b5fe-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
