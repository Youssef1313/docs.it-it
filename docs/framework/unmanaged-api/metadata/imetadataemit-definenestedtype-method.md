---
title: Metodo IMetaDataEmit::DefineNestedType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7676c83e8b231606896cb6d1224633b4fa15e725
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777563"
---
# <a name="imetadataemitdefinenestedtype-method"></a>Metodo IMetaDataEmit::DefineNestedType
Crea la firma dei metadati di una definizione di tipo, restituisce un `mdTypeDef` token per il tipo e specifica che il tipo definito è un membro del tipo fa riferimento il `tdEncloser` parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `szTypeDef`  
 [in] Il nome del tipo in formato Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` attributi. Si tratta di una maschera di bit delle `CorTypeAttr` valori.  
  
 `tkExtends`  
 [in] Il token della classe di base. Questo è un `mdTypeDef` o un `mdTypeRef` token.  
  
 `rtkImplements`[]  
 [in] Matrice dei token che specificano le interfacce implementate da questa classe o interfaccia.  
  
 `tdEncloser`  
 [in] Il token del tipo di inclusione. L'ultimo elemento della matrice deve essere `mdTokenNil`.  
  
 `ptd`  
 [out] Il `mdTypeDef` token assegnato.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interfaccia IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
