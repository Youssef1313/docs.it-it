---
title: Metodo IMetaDataEmit::SetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 271ecd7e757340becccb7bf52362487a2b277299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737190"
---
# <a name="imetadataemitseteventprops-method"></a>Metodo IMetaDataEmit::SetEventProps
Imposta o aggiorna la funzionalità specificata di un evento definito da una chiamata precedente a [DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametri  
 `ev`  
 [in] Il token di evento.  
  
 `dwEventFlags`  
 [in] Flag dell'evento. Si tratta di una maschera di bit delle `CorEventAttr` valori.  
  
 `tkEventType`  
 [in] Il token per la classe di evento. Questo è un `mdTypeDef` o un `mdTypeRef` token.  
  
 `mdAddOn`  
 [in] Il metodo utilizzato per sottoscrivere l'evento, o null.  
  
 `mdRemoveOn`  
 [in] Il metodo utilizzato per annullare la sottoscrizione per l'evento, o null.  
  
 `mdFire`  
 [in] Il metodo utilizzato (da una classe derivata) per generare l'evento.  
  
 `rmdOtherMethods[]`  
 [in] Matrice dei token per gli altri metodi associati all'evento. L'ultimo elemento della matrice deve essere `mdMethodDefNil`.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interfaccia IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
