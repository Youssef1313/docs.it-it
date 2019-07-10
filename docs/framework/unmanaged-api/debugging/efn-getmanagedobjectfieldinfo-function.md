---
title: Funzione _EFN_GetManagedObjectFieldInfo
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739004"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>\_EFN\_GetManagedObjectFieldInfo (funzione)
Ottiene l'offset per un campo dall'inizio di un oggetto e il valore del campo, usando il puntatore all'oggetto e il nome di campo forniti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `Client`  
 [in] Puntatore al client di debug.  
  
 `objAddr`  
 [in] Un puntatore all'oggetto gestito.  
  
 szFieldName  
 [in] Un puntatore all'oggetto gestito per il nome del campo.  
  
 `pValue`  
 [out] Il valore del campo. Questo parametro può essere null.  
  
 `pOffset`  
 [out] L'offset dal `objAddr` al campo. Questo parametro può essere null.  
  
## <a name="remarks"></a>Note  
 Se l'offset è 0, non viene scritto alcun offset.  
  
 Se non vi è nessun codice gestito sul thread attualmente nel contesto, la funzione restituisce HRESULT SOS_E_NOMANAGEDCODE con un valore di impianto pari a 0xa0 e un codice di errore di 0x1000.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** SOS_Stacktrace.h  
  
 **Versione di .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Funzioni statiche globali di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
