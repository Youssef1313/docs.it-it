---
title: Metodo IMetaDataAssemblyImport::EnumManifestResources
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449548"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>Metodo IMetaDataAssemblyImport::EnumManifestResources
Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a>Parametri  
 `phEnum`  
 [in, out] A pointer to the enumerator. This must be a null value when the `EnumManifestResources` method is called for the first time.  
  
 `rManifestResources`  
 [out] The array used to store the `mdManifestResource` metadata tokens.  
  
 `cMax`  
 [in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.  
  
 `pcTokens`  
 [out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources` returned successfully.|  
|`S_FALSE`|There are no tokens to enumerate. In this case, `pcTokens` is set to zero.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
