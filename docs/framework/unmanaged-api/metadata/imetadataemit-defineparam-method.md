---
title: Metodo IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431697"
---
# <a name="imetadataemitdefineparam-method"></a>Metodo IMetaDataEmit::DefineParam
Crea una definizione di parametro con la firma specificata per il metodo a cui fa riferimento il token specificato e ottiene un token per la definizione del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a>Parametri  
 `md`  
 in Token per il metodo di cui viene definito il parametro.  
  
 `ulParamSeq`  
 in Numero di sequenza del parametro.  
  
 `szName`  
 in Nome del parametro in formato Unicode.  
  
 `dwParamFlags`  
 in Flag per il parametro. Si tratta di una maschera di maschera dei valori `CorParamAttr`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** per il valore costante.  
  
 `pValue`  
 in Valore costante per il parametro.  
  
 `cchValue`  
 in Dimensione, in caratteri Unicode, di `pValue`.  
  
 `ppd`  
 out Token `mdParamDef` assegnato.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di sequenza in `ulParamSeq` iniziano con 1 per i parametri. Il numero di sequenza di un valore restituito è 0.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interfaccia IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
