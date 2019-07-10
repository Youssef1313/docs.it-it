---
title: Metodo ICorDebugStackWalk::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6c96e64b1197b5762c0ad7dbed5458b5d71a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760902"
---
# <a name="icordebugstackwalknext-method"></a>Metodo ICorDebugStackWalk::Next
Sposta il [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) oggetto per il frame successivo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Il runtime è stato rimosso fino al fotogramma successivo (vedere la sezione Osservazioni).|  
|E_FAIL|Il `ICorDebugStackWalk` non è stato possibile avanzare l'oggetto.|  
|CORDBG_S_AT_END_OF_STACK|In seguito a questa rimozione è stata raggiunta la fine dello stack.|  
|CORDBG_E_PAST_END_OF_STACK|Puntatore ai frame è già alla fine dello stack. di conseguenza, nessun frame aggiuntivi sono accessibili.|  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 Il `Next` metodo progressi di `ICorDebugStackWalk` solo se il runtime può rimuovere il frame corrente dell'oggetto per il frame di chiamata. In caso contrario, l'oggetto sposta il frame successivo che il runtime è in grado di rimozione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
