---
title: Metodo IMetaDataImport::GetMemberRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fadc54d74ce6027bd021e148a14cb0c432eb41fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782348"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>Metodo IMetaDataImport::GetMemberRefProps
Ottiene i metadati associati al membro a cui fa riferimento il token specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a>Parametri  
 `mr`  
 [in] Il token MemberRef per restituire i metadati associati.  
  
 `ptk`  
 [out] Token TypeDef o TypeRef o TypeSpec che rappresenta la classe che dichiara il membro o un token ModuleRef che rappresenta la classe di modulo che dichiara il membro o un MethodDef che rappresenta il membro.  
  
 `szMember`  
 [out] Un buffer di stringa per il nome del membro.  
  
 `cchMember`  
 [in] Le dimensioni richieste in caratteri wide di `szMember`.  
  
 `pchMember`  
 [out] Le dimensioni restituite in caratteri wide di `szMember`.  
  
 `ppvSibBlob`  
 [out] Un puntatore per la firma binaria dei metadati per il membro.  
  
 `pbSig`  
 [out] La dimensione in byte di `ppvSigBlob`.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interfaccia IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
