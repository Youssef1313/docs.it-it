---
title: Metodo ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c614afee18824e1672b378dd468cb11c9c173d9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764952"
---
# <a name="icorpublishprocessenumappdomains-method"></a>Metodo ICorPublishProcess::EnumAppDomains
Ottiene un enumeratore per i domini applicazione nel processo di cui viene fatto riferimento da questo [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Un puntatore all'indirizzo di un [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) istanza che consente l'iterazione nella raccolta di domini applicazione in questo processo.  
  
## <a name="remarks"></a>Note  
 L'elenco di domini applicazione si basa su uno snapshot dei domini applicazione che esiste quando il `EnumAppDomains` viene chiamato il metodo. Questo metodo può essere chiamato più volte per creare un nuovo elenco aggiornato. Elenchi esistenti non essere interessati dalle chiamate successive di questo metodo.  
  
 Se il processo è stato terminato, `EnumAppDomains` avrà esito negativo con un valore HRESULT di CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorPub.idl, CorPub.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
