---
title: Metodo IMetaDataImport::EnumEvents
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f3d74830de0541ec789081c47352beca8d81d74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780703"
---
# <a name="imetadataimportenumevents-method"></a>Metodo IMetaDataImport::EnumEvents
Enumera i token di definizione di evento per il token TypeDef specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `phEnum`  
 [in, out] Un puntatore all'enumeratore.  
  
 `td`  
 [in] Il token TypeDef le cui definizioni di evento devono essere enumerati.  
  
 `rEvents`  
 [out] Matrice di eventi restituiti.  
  
 `cMax`  
 [in] Dimensione massima della matrice `rEvents`.  
  
 `pcEvents`  
 [out] Il numero effettivo di eventi restituiti `rEvents`.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|DESCRIZIONE|  
|-------------|-----------------|  
|`S_OK`|`EnumEvents` stato restituito correttamente.|  
|`S_FALSE`|Non sono presenti eventi da enumerare. In tal caso, `pcEvents` è uguale a zero.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interfaccia IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
