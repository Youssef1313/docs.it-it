---
title: Metodo ICorProfilerCallback::AppDomainShutdownFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e214af178972623bad3536565aa9bc51edc97260
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763105"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>Metodo ICorProfilerCallback::AppDomainShutdownFinished
Notifica al profiler che un dominio dell'applicazione è stato scaricato da un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametri  
 `appDomainId`  
 [in] Identifica il dominio in cui sono archiviati gli assembly dell'applicazione.  
  
 `hrStatus`  
 [in] HRESULT che indica se il dominio dell'applicazione è stato scaricato correttamente.  
  
## <a name="remarks"></a>Note  
 Il valore di `appDomainId` non è valido per una richiesta di informazioni dopo che il [AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) restituzione del metodo.  
  
 Alcune parti dello scaricamento del dominio dell'applicazione potrebbero continuare dopo il `AppDomainCreationFinished` callback. Un HRESULT di errore in `hrStatus` indica un errore. Tuttavia, un HRESULT di esito positivo in `hrStatus` indica solo che la prima parte dello scaricamento del dominio applicazione ha avuto esito positivo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
