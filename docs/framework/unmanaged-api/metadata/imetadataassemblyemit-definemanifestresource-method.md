---
title: Metodo IMetaDataAssemblyEmit::DefineManifestResource
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781953fe5bf209f195ef4887dff45e1902741f0c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775315"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>Metodo IMetaDataAssemblyEmit::DefineManifestResource
Crea una struttura `ManifestResource` che contiene i metadati per la risorsa di manifesto specificata e restituisce il token di metadati associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `szName`  
 [in] Il nome della risorsa.  
  
 `tkImplementation`  
 [in] Un token di metadati di tipo `mdtFile` o `mdtAssemblyRef` che esegue il mapping al provider di risorse. Un valore NULL indica che il file in cui sono incorporati i metadati sia il provider di risorse.  
  
 `dwOffset`  
 [in] L'offset all'inizio della risorsa all'interno del file. Per le risorse in file autonomi, questo valore sarà sempre zero. Se la risorsa è incorporata in un file di PE (eseguibile), questo è un offset pari a risorse BLOB, che inizia nella posizione specificata nel file di intestazione Cor. h.  
  
 `dwResourceFlags`  
 [in] Combinazione bit per bit dei valori di flag che specificano le impostazioni delle proprietà per la definizione di risorsa.  
  
 `pmdmr`  
 [out] Un puntatore al token di metadati restituiti.  
  
## <a name="remarks"></a>Note  
 Uno `ManifestResource` struttura dei metadati deve essere definita per ogni risorsa che viene implementata in ciascuno dei file dell'assembly.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforma:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
