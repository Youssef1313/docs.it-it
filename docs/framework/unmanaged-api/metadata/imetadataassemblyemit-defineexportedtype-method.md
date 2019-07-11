---
title: Metodo IMetaDataAssemblyEmit::DefineExportedType
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4d143d8dd5391283736d0140e8f1ced1dec53e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775330"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>Metodo IMetaDataAssemblyEmit::DefineExportedType
Crea una struttura `ExportedType` che contiene i metadati per il tipo esportato specificato e restituisce il token di metadati associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `szName`  
 [in] Il nome del tipo da esportare. Per la versione 1.1 di common language runtime, il nome del tipo esportato deve corrispondere esattamente al nome fornito nel `TypeDef` per il tipo.  
  
 `tkImplementation`  
 [in] Un token che specifica in cui viene implementato il tipo esportato. I valori validi e i relativi significati associati sono:  
  
- `mdFile` Il tipo è implementato in un altro file all'interno dell'assembly.  
  
- `mdAssemblyRef` Il tipo è implementato in un assembly diverso.  
  
- `mdExportedTYpe` Il tipo è annidato all'interno di un altro tipo.  
  
- `mdFileNil` Il tipo è nello stesso file del manifesto e non è un tipo annidato.  
  
 `tkTypeDef`  
 [in] Un token per i metadati che specifica il tipo da esportare. Questo valore viene immesso nel `TypeDef` tabella del file che implementa il tipo e che è pertinente solo se tale file si trova in questo assembly.  
  
 `dwExportedTypeFlags`  
 [in] Una combinazione bit per bit di [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valori di enumerazione che definiscono le impostazioni delle proprietà per il tipo esportato.  
  
 `pmdct`  
 [out] Puntatore al token di metadati restituito che indica il tipo esportato.  
  
## <a name="remarks"></a>Note  
 Un `ExportedType` struttura dei metadati deve essere definito per ogni tipo che viene esposta dall'assembly e che viene implementato in un modulo diverso da quello contenente il manifesto.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforma:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
