---
title: Metodo IMetaDataAssemblyEmit::SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34335321207e98a518ff3e0fdb5ea1dc3ac68b75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776260"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>Metodo IMetaDataAssemblyEmit::SetAssemblyProps
Modifica la struttura dei metadati `Assembly` specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pma`  
 [in] Il token di metadati che specifica il `Assembly` modifica della struttura dei metadati.  
  
 `pbPublicKey`  
 [in] Puntatore alla chiave pubblica del server di pubblicazione dell'assembly.  
  
 `cbPublicKey`  
 [in] La dimensione in byte di `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] L'identificatore per l'algoritmo hash usato per eseguire l'hashing i file di assembly.  
  
 `szName`  
 [in] Il nome di testo leggibile dell'assembly.  
  
 `pMetaData`  
 [in] Puntatore a ASSEMBLYMETADATA che contiene le informazioni di versione, piattaforma e delle impostazioni locali per l'assembly.  
  
 `dwAssemblyFlags`  
 [in] Una combinazione bit per bit di [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) valori che specificano vari attributi dell'assembly.  
  
## <a name="remarks"></a>Note  
 Per creare un `Assembly` struttura dei metadati, usare il [DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforma:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
