---
title: Metodo ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356678afb537ab5e5e1653c4f71140ce704e55ef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779678"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a>Metodo ICLRGCManager2::SetGCStartupLimitsEx
Imposta le dimensioni di un segmento di garbage collection e le dimensioni massime della generazione del sistema di garbage collection 0.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `SegmentSize`  
 [in] La dimensione specificata per un segmento di garbage collection.  
  
 Le dimensioni del segmento minimo sono 4 MB. Segmenti possono essere un aumento con incrementi di 1 MB o maggiori.  
  
 `MaxGen0Size`  
 [in] Le dimensioni massime specificata per la generazione 0.  
  
 La dimensione minima per la generazione 0 è 64 KB.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimitsEx` stato restituito correttamente.|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.|  
|HOST_E_TIMEOUT|Timeout della chiamata.|  
|HOST_E_NOT_OWNER|Il chiamante non possiede il blocco.|  
|HOST_E_ABANDONED|Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Dopo che un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo. Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Note  
 I valori che `SetGCStartupLimitsEx` set possono essere specificati solo prima dell'avvio dell'host. Le chiamate successive a `SetGCStartupLimitsEx` vengono ignorati.  
  
 Per impostare dei parametri senza influire su altro, specificare 0 (zero) per il parametro che non si vuole modificare.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE.h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Gestione automatica della memoria](../../../../docs/standard/automatic-memory-management.md)
- [Garbage Collection](../../../../docs/standard/garbage-collection/index.md)
- [Interfaccia ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interfaccia ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
