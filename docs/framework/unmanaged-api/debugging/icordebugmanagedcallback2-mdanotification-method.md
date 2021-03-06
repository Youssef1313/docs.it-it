---
title: Metodo ICorDebugManagedCallback2::MDANotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131453"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>Metodo ICorDebugManagedCallback2::MDANotification
Fornisce la notifica che l'esecuzione del codice ha rilevato un assistente al debug gestito (MDA) nell'applicazione di cui è in corso il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pController`  
 in Puntatore a un'interfaccia ICorDebugController che espone il processo o il dominio dell'applicazione in cui si è verificato l'assistente al debug gestito.  
  
 Un debugger non deve prevedere se il controller è un processo o un dominio dell'applicazione, anche se può sempre eseguire una query sull'interfaccia per eseguire una determinazione.  
  
 `pThread`  
 in Puntatore a un'interfaccia ICorDebugThread che espone il thread gestito in cui si è verificato l'evento di debug.  
  
 Se l'assistente al debug gestito è stato eseguito in un thread non gestito, il valore di `pThread` sarà null.  
  
 È necessario ottenere l'ID del thread del sistema operativo dall'oggetto MDA stesso.  
  
 `pMDA`  
 in Puntatore a un'interfaccia [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) che espone le informazioni dell'assistente al debug gestito.  
  
## <a name="remarks"></a>Note  
 Un assistente al debug gestito è un avviso euristico e non richiede alcuna azione esplicita del debugger ad eccezione della chiamata a [ICorDebugController:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) per riprendere l'esecuzione dell'applicazione di cui è in corso il debug.  
  
 Il Common Language Runtime (CLR) può determinare quali MDA vengono attivati e quali dati si trovano in un determinato MDA in qualsiasi momento. Pertanto, i debugger non devono compilare funzionalità che richiedono modelli di assistente al debug gestito specifici.  
  
 MDA può essere accodato e generato poco dopo che è stato rilevato l'assistente al debug gestito. Questo problema può verificarsi se il runtime deve attendere fino a quando non raggiunge un punto sicuro per l'attivazione dell'assistente al debug gestito, anziché eseguire l'assistente al debug gestito quando lo rileva. Significa anche che il runtime può generare un certo numero di MDA in un unico set di callback in coda (analogamente a un'operazione di "associazione").  
  
 Un debugger deve rilasciare il riferimento a un'istanza di `ICorDebugMDA` immediatamente dopo la restituzione dal callback `MDANotification`, per consentire a CLR di riciclare la memoria utilizzata da un assistente al debug gestito. Il rilascio dell'istanza può migliorare le prestazioni in caso di generazione di molti MDA.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Diagnostica degli errori tramite gli assistenti al debug gestito](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interfaccia ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interfaccia ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
