---
title: Metodo ICorDebugModule3::CreateReaderForInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137309"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>Metodo ICorDebugModule3::CreateReaderForInMemorySymbols
Crea un lettore di simboli di debug per un modulo dinamico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parametri  
 riid  
 in IID dell'interfaccia COM da restituire. Si tratta in genere di un' [interfaccia ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 out Puntatore a un puntatore all'interfaccia restituita.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK  
 Creazione del Reader completata.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Il modulo non è un modulo in memoria o dinamico.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 I simboli non sono stati forniti dall'applicazione o non sono ancora disponibili.  
  
 E_FAIL (o altri codici E_ restituiti)  
 Impossibile creare il lettore.  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere usato anche per creare un oggetto lettore di simboli per i moduli in memoria (non dinamici), ma solo dopo che i simboli sono disponibili per la prima volta (indicati dal callback del [Metodo UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).  
  
 Questo metodo restituisce una nuova istanza di Reader ogni volta che viene chiamata (ad esempio [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Pertanto, il debugger deve memorizzare nella cache il risultato e richiedere una nuova istanza solo quando è possibile che i dati sottostanti siano stati modificati, ovvero quando viene ricevuto un callback del [metodo loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) .  
  
 I moduli dinamici non hanno alcun simbolo disponibile fino a quando non è stato caricato il primo tipo (come indicato dal callback del [metodo loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [Interfaccia ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
