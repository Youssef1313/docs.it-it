---
title: Metodo ICorDebugRemote::CreateProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744781"
---
# <a name="icordebugremotecreateprocessex-method"></a>Metodo ICorDebugRemote::CreateProcessEx
Avvia un processo in un computer remoto all'interno del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pRemoteTarget`  
 [in] Puntatore a un [interfaccia ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Utilizzato per determinare il computer remoto in cui verrà avviato il processo.  
  
 `lpApplicationName`  
 [in] Puntatore a una stringa con terminazione null che specifica il modulo deve essere eseguito dal processo avviato. Il modulo viene eseguito nel contesto di sicurezza del processo chiamante.  
  
 `lpCommandLine`  
 [in] Puntatore a una stringa con terminazione null che specifica la riga di comando deve essere eseguito dal processo avviato.  
  
 `lpProcessAttributes`  
 [in] Non utilizzato per il debug remoto.  
  
 `lpThreadAttributes`  
 [in] Non utilizzato per il debug remoto.  
  
 `bInheritHandles`  
 [in] Non utilizzato per il debug remoto.  
  
 `dwCreationFlags`  
 [in] Non utilizzato per il debug remoto.  
  
 `lpEnvironment`  
 [in] Puntatore a un blocco di ambiente per il nuovo processo.  
  
 `lpCurrentDirectory`  
 [in] Puntatore a una stringa con terminazione null che specifica il percorso completo per directory corrente per il processo. Se questo parametro è null, il nuovo processo avrà la stessa unità e directory corrente del processo chiamante.  
  
 `lpStartupInfo`  
 [in] Non utilizzato per il debug remoto.  
  
 `lpProcessInformation`  
 [in] Non utilizzato per il debug remoto.  
  
 `debuggingFlags`  
 [in] Non utilizzato per il debug remoto.  
  
 `ppProcess`  
 [out] Un puntatore all'indirizzo di un oggetto "ICorDebugProcess (interfaccia)" che rappresenta il processo.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK  
 È stato avviato il processo nel computer remoto e restituita un' "interfaccia ICorDebugProcess" per il debug.  
  
 E_FAIL (o altri codici E_ restituiti)  
 Impossibile avviare il processo nel computer remoto e restituire un' "interfaccia ICorDebugProcess" per il debug.  
  
## <a name="remarks"></a>Note  
 Debug in modalità mista non è supportato in Silverlight.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [Interfaccia ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
