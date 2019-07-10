---
title: Metodo ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c91a813a80af5cf09914ca134ac9935ed787c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750066"
---
# <a name="icordebugcontrollerterminate-method"></a>Metodo ICorDebugController::Terminate
Termina il processo con il codice di uscita specificato.  
  
> [!NOTE]
>  Questo metodo è un wrapper per Win32 `TerminateProcess` (funzione). Pertanto `Terminate` Usa il codice di uscita nello stesso modo in cui Win32 `TerminateProcess` funzione lo usa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `exitCode`  
 [in] Valore numerico che rappresenta il codice di uscita. I valori numerici validi sono definiti in winbase. h.  
  
## <a name="remarks"></a>Note  
 Se il processo viene arrestato quando `Terminate` viene chiamato, il processo deve essere continuata usando il [ICorDebugController](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metodo in modo che il debugger riceve conferma della terminazione tramite il [ ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) oppure [ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.  
  
> [!NOTE]
>  Questo metodo non è implementato da un dominio dell'applicazione. Vale a dire, non viene implementato nel <xref:System.AppDomain> livello.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche
