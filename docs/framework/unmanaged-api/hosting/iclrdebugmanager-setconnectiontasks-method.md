---
title: Metodo ICLRDebugManager::SetConnectionTasks
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: d6092f16804fae39dd9496e8572edd64e1b7e9bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129378"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>Metodo ICLRDebugManager::SetConnectionTasks
Associa un elenco di istanze di [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) a un identificatore e a un nome descrittivo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `id`  
 in Identificatore specifico dell'host per la connessione a cui associare la matrice di `ppCLRTask`.  
  
 `dwCount`  
 in Numero di membri di `ppCLRTask`. Questo numero deve essere maggiore di zero.  
  
 `ppCLRTask`  
 in Matrice di puntatori `ICLRTask` da associare alla connessione identificata da `id`. Questa matrice deve contenere almeno un membro.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` ha restituito un esito positivo.|  
|HOST_E_CLRNOTAVAILABLE|Il Common Language Runtime (CLR) non è stato caricato in un processo oppure CLR si trova in uno stato in cui non è possibile eseguire codice gestito o elaborare la chiamata correttamente.|  
|HOST_E_TIMEOUT|Timeout della chiamata.|  
|HOST_E_NOT_OWNER|Il chiamante non è il proprietario del blocco.|  
|HOST_E_ABANDONED|Un evento è stato annullato mentre un thread bloccato o Fiber era in attesa su di esso.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Dopo che un metodo restituisce E_FAIL, CLR non è più utilizzabile all'interno del processo. Le chiamate successive ai metodi di hosting restituiscono HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) non è stato chiamato utilizzando questo valore di `id`oppure `dwCount` o `id` è zero oppure uno degli elementi di `ppCLRTask` è null.|  
  
## <a name="remarks"></a>Note  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fornisce tre metodi, `BeginConnection`, `SetConnectionTasks`e [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), per l'associazione di elenchi di attività con identificatori e nomi descrittivi.  
  
> [!IMPORTANT]
> Questi tre metodi devono essere chiamati in un ordine specifico per ogni set di attività. `BeginConnection` viene chiamato per primo per stabilire una nuova connessione. `SetConnectionTasks` viene chiamato Next per fornire il set di attività da associare a tale connessione. `EndConnection` viene chiamato per ultimo per rimuovere l'associazione tra l'elenco attività e l'identificatore e il nome descrittivo. Tuttavia, le chiamate per connessioni diverse possono essere nidificate.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE. h  
  
 **Libreria:** Incluso come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interfaccia ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [Metodo BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [Metodo EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [Interfaccia IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
