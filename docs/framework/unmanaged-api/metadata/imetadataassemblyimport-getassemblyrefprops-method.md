---
title: Metodo IMetaDataAssemblyImport::GetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa633d554652050af51065e11221f898b34d5c63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772678"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>Metodo IMetaDataAssemblyImport::GetAssemblyRefProps
Ottiene il set di proprietà per il riferimento all'assembly con la firma dei metadati specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `mdar`  
 [in] Il `mdAssemblyRef` token di metadati che rappresenta il riferimento all'assembly per cui ottenere le proprietà.  
  
 `ppbPublicKeyOrToken`  
 [out] Puntatore alla chiave pubblica o token di metadati.  
  
 `pcbPublicKeyOrToken`  
 [out] Il numero di byte restituito pubblico o un token.  
  
 `szName`  
 [out] Il nome semplice dell'assembly.  
  
 `cchName`  
 [in] Le dimensioni, in caratteri wide, di `szName`.  
  
 `pchName`  
 [out] Un puntatore al numero di caratteri wide effettivamente restituiti nella `szName`.  
  
 `pMetaData`  
 [out] Un puntatore a una struttura ASSEMBLYMETADATA che contiene i metadati dell'assembly.  
  
 `ppbHashValue`  
 [out] Puntatore al valore hash. Questo è l'hash, usando l'algoritmo SHA-1, del `PublicKey` proprietà dell'assembly a cui viene fatto riferimento, a meno che il flag arfFullOriginator del [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumerazione è impostato.  
  
 `pcbHashValue`  
 [out] Il numero di caratteri wide nel valore restituito di hash.  
  
 `pdwAssemblyRefFlags`  
 [out] Puntatore al flag che descrivono i metadati applicati a un assembly. Il valore dei flag è una combinazione di uno o più [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valori.  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce S_OK se riesce; in caso contrario, restituisce uno dei codici di errore definiti nel file di intestazione file Winerror. h.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
