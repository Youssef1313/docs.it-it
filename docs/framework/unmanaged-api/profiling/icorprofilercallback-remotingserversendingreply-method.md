---
title: Metodo ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c73889a6daaa50d1694e786c78f50d0e87644967
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750437"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>Metodo ICorProfilerCallback::RemotingServerSendingReply
Notifica al profiler che il processo ha terminato l'elaborazione di una richiesta di chiamata al metodo remote e sta per trasmettere la risposta tramite un canale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametri  
 `pCookie`  
 [in] Un puntatore a un GUID che corrisponde al valore fornito [RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) in queste condizioni:  
  
- I cookie GUID di .NET Remoting sono attivi.  
  
- Il canale ha esito positivo la trasmissione del messaggio.  
  
- I cookie GUID sono attivi nel processo del lato client.  
  
 Ciò consente l'associazione semplice delle chiamate remote e la creazione di uno stack di chiamate logici.  
  
 `fIsAsync`  
 [in] Valore che rappresenta `true` se la chiamata è asincrona; in caso contrario, `false`.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
