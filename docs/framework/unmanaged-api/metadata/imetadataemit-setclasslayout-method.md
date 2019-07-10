---
title: Metodo IMetaDataEmit::SetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c455b5196ceafef924de59e9134b89ed62455520
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737220"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="56639-102">Metodo IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="56639-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="56639-103">Completa il layout dei campi per una classe che è stato definito da una chiamata precedente a [metodo DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="56639-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56639-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="56639-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56639-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="56639-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="56639-106">[in] Un `mdTypeDef` token che specifica la classe disposizione.</span><span class="sxs-lookup"><span data-stu-id="56639-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="56639-107">[in] La dimensione di compressione: 1, 2, 4, 8 o 16 byte.</span><span class="sxs-lookup"><span data-stu-id="56639-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="56639-108">La dimensione di compressione è il numero di byte tra i campi adiacenti.</span><span class="sxs-lookup"><span data-stu-id="56639-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="56639-109">[in] Matrice di [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) strutture, ognuno dei quali specifica un campo della classe e il campo dell'offset all'interno della classe.</span><span class="sxs-lookup"><span data-stu-id="56639-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="56639-110">Terminare la matrice con `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="56639-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="56639-111">[in] Le dimensioni, in byte, della classe.</span><span class="sxs-lookup"><span data-stu-id="56639-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56639-112">Note</span><span class="sxs-lookup"><span data-stu-id="56639-112">Remarks</span></span>  
 <span data-ttu-id="56639-113">La classe viene definita inizialmente chiamando il [DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metodo e specificando uno dei tre layout per i campi della classe: automatici, sequenziale o esplicito.</span><span class="sxs-lookup"><span data-stu-id="56639-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="56639-114">In genere, di usare un layout automatico e consentire il runtime di scegliere il modo migliore per disporre i campi.</span><span class="sxs-lookup"><span data-stu-id="56639-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="56639-115">Tuttavia, è possibile che i campi disposti in base alla disposizione che non gestiti di codice viene utilizzato.</span><span class="sxs-lookup"><span data-stu-id="56639-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="56639-116">In questo caso, scegliere il layout sequenziale o esplicito e chiamata `SetClassLayout` per completare il layout dei campi:</span><span class="sxs-lookup"><span data-stu-id="56639-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="56639-117">Layout sequenziale: Specificare la dimensione di compressione.</span><span class="sxs-lookup"><span data-stu-id="56639-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="56639-118">Un campo è allineato in base alle dimensioni naturali o la dimensione di compressione, qualunque sia il risultati in più piccoli offset del campo.</span><span class="sxs-lookup"><span data-stu-id="56639-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="56639-119">Impostare `rFieldOffsets` e `ulClassSize` su zero.</span><span class="sxs-lookup"><span data-stu-id="56639-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="56639-120">Layout esplicito: Specificare l'offset di ogni campo o specificare le dimensioni di classe e la dimensione di compressione.</span><span class="sxs-lookup"><span data-stu-id="56639-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56639-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="56639-121">Requirements</span></span>  
 <span data-ttu-id="56639-122">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56639-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56639-123">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56639-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56639-124">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="56639-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56639-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56639-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56639-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56639-126">See also</span></span>

- [<span data-ttu-id="56639-127">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="56639-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="56639-128">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="56639-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
