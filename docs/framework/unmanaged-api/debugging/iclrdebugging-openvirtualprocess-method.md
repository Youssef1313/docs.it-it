---
title: Metodo ICLRDebugging::OpenVirtualProcess
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: cd43dce995c2bc9a45a0c8134a91b20cb1dec26e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111421"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>Metodo ICLRDebugging::OpenVirtualProcess
Ottiene l'interfaccia ICorDebugProcess che corrisponde a un modulo Common Language Runtime (CLR) caricato nel processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>Parametri  
 `moduleBaseAddress`  
 in Indirizzo di base di un modulo nel processo di destinazione. Se il modulo specificato non è un modulo CLR, verrà restituito COR_E_NOT_CLR.  
  
 `pDataTarget`  
 in Astrazione di destinazione dati che consente al debugger gestito di ispezionare lo stato del processo. Il debugger deve implementare l'interfaccia [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) . È necessario implementare l'interfaccia [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) per supportare scenari in cui il CLR di cui è in corso il debug non è installato localmente nel computer.  
  
 `pLibraryProvider`  
 in Interfaccia di callback del provider di librerie che consente di posizionare e caricare su richiesta librerie di debug specifiche della versione. Questo parametro è obbligatorio solo se `ppProcess` o `pFlags` non è `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 in Versione più recente di CLR di cui questo debugger è in grado di eseguire il debug. È necessario specificare le versioni principale, secondaria e di build dalla versione CLR più recente supportata da questo debugger, quindi impostare il numero di revisione su 65535 per supportare le future versioni di manutenzione CLR sul posto.  
  
 `riidProcess`  
 in ID dell'interfaccia ICorDebugProcess da recuperare. Attualmente, gli unici valori accettati sono IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 e IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 out Puntatore all'interfaccia COM identificata da `riidProcess`.  
  
 `pVersion`  
 [in, out] Versione di CLR. In input, questo valore può essere `null`. Può anche puntare a una struttura [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) , nel qual caso il campo `wStructVersion` della struttura deve essere inizializzato su 0 (zero).  
  
 Nell'output, la struttura di `CLR_DEBUGGING_VERSION` restituita verrà compilata con le informazioni sulla versione per CLR.  
  
 `pdwFlags`  
 out Flag informativi sul runtime specificato. Per una descrizione dei flag, vedere l'argomento [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Metodo completato correttamente.|  
|E_POINTER|`pDataTarget` è `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Il callback [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) restituisce un errore o non fornisce un handle valido.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` non implementa le interfacce di destinazione dati richieste per questa versione del runtime.|  
|CORDBG_E_NOT_CLR|Il modulo indicato non è un modulo CLR. Questo HRESULT viene restituito anche quando non è possibile rilevare un modulo CLR perché la memoria è stata danneggiata, il modulo non è disponibile o la versione di CLR è successiva alla versione shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Questa versione di runtime non supporta questo modello di debug. Attualmente, il modello di debug non è supportato dalle versioni CLR prima del .NET Framework 4. Il parametro di output `pwszVersion` è ancora impostato sul valore corretto dopo l'errore.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|La versione di CLR è maggiore della versione che questo debugger dichiara di supportare. Il parametro di output `pwszVersion` è ancora impostato sul valore corretto dopo l'errore.|  
|E_NO_INTERFACE|L'interfaccia `riidProcess` non è disponibile.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|La struttura `CLR_DEBUGGING_VERSION` non dispone di un valore riconosciuto per `wStructVersion`. L'unico valore accettato in questa fase è 0.|  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
