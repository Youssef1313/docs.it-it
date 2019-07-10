---
title: Metodo IMetaDataImport::GetFieldProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 574ac706a07e7fcd701ab04f923d5171bea6f64a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782382"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="a4f2e-102">Metodo IMetaDataImport::GetFieldProps</span><span class="sxs-lookup"><span data-stu-id="a4f2e-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="a4f2e-103">Ottiene i metadati associati al campo a cui fa riferimento il token FieldDef specificato.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f2e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a4f2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4f2e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a4f2e-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="a4f2e-106">[in] Token FieldDef che rappresenta il campo per ottenere i metadati associati.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a4f2e-107">[out] Un puntatore a un token TypeDef che rappresenta il tipo della classe a cui appartiene il campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="a4f2e-108">[out] Il nome del campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="a4f2e-109">[in] La dimensione in caratteri wide del buffer per *szField*.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="a4f2e-110">[out] Le dimensioni effettive del buffer restituito.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="a4f2e-111">[out] Flag associato ai metadati del campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="a4f2e-112">[in] Puntatore al valore binario dei metadati che descrive il campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="a4f2e-113">[out] La dimensione in byte di `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="a4f2e-114">[out] Un flag che specifica il tipo di valore del campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a4f2e-115">[out] Un valore costante per il campo.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="a4f2e-116">[out] La dimensione in caratteri di `ppValue`, oppure zero se è presente alcuna stringa.</span><span class="sxs-lookup"><span data-stu-id="a4f2e-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4f2e-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a4f2e-117">Requirements</span></span>  
 <span data-ttu-id="a4f2e-118">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f2e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4f2e-119">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a4f2e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4f2e-120">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a4f2e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4f2e-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4f2e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f2e-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4f2e-122">See also</span></span>

- [<span data-ttu-id="a4f2e-123">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a4f2e-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a4f2e-124">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a4f2e-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
