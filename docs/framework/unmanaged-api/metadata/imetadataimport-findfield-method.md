---
title: Metodo IMetaDataImport::FindField
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1baee71b5b8575f51eb54fbc8a037a5dddd24500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782530"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="f40ab-102">Metodo IMetaDataImport::FindField</span><span class="sxs-lookup"><span data-stu-id="f40ab-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="f40ab-103">Ottiene un puntatore a FieldDef token per il campo che è racchiuso da specificato <xref:System.Type> e avente il nome e i metadati della firma specificata.</span><span class="sxs-lookup"><span data-stu-id="f40ab-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40ab-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f40ab-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f40ab-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f40ab-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f40ab-106">[in] Il token TypeDef per la classe o interfaccia che racchiude il campo da cercare.</span><span class="sxs-lookup"><span data-stu-id="f40ab-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="f40ab-107">Se questo valore è `mdTokenNil`, la ricerca viene eseguita per una variabile globale.</span><span class="sxs-lookup"><span data-stu-id="f40ab-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="f40ab-108">[in] Il nome del campo da cercare.</span><span class="sxs-lookup"><span data-stu-id="f40ab-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f40ab-109">[in] Un puntatore per la firma binaria dei metadati del campo.</span><span class="sxs-lookup"><span data-stu-id="f40ab-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f40ab-110">[in] La dimensione in byte di `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f40ab-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="f40ab-111">[out] Puntatore al token FieldDef corrispondente.</span><span class="sxs-lookup"><span data-stu-id="f40ab-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f40ab-112">Note</span><span class="sxs-lookup"><span data-stu-id="f40ab-112">Remarks</span></span>  
 <span data-ttu-id="f40ab-113">Si specifica il campo utilizzando la classe o interfaccia contenitore (`td`), il relativo nome (`szName`) e facoltativamente la firma (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="f40ab-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="f40ab-114">La firma è passato a `FindField` deve essere stata generata nell'ambito corrente, in quanto le firme sono associate a un particolare ambito.</span><span class="sxs-lookup"><span data-stu-id="f40ab-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="f40ab-115">Una firma possibile incorporare un token che identifica il tipo di classe o valore di inclusione.</span><span class="sxs-lookup"><span data-stu-id="f40ab-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="f40ab-116">(Il token è un indice nella tabella di TypeDef locale).</span><span class="sxs-lookup"><span data-stu-id="f40ab-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="f40ab-117">Non è possibile generare una firma in fase di esecuzione all'esterno del contesto dell'ambito corrente e usare tale firma come input per `FindField`.</span><span class="sxs-lookup"><span data-stu-id="f40ab-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="f40ab-118">`FindField` Trova solo i campi che sono stati definiti direttamente nella classe o interfaccia. i campi ereditati non viene trovato.</span><span class="sxs-lookup"><span data-stu-id="f40ab-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40ab-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f40ab-119">Requirements</span></span>  
 <span data-ttu-id="f40ab-120">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f40ab-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40ab-121">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f40ab-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f40ab-122">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f40ab-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f40ab-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40ab-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40ab-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f40ab-124">See also</span></span>

- [<span data-ttu-id="f40ab-125">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f40ab-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f40ab-126">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f40ab-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
