---
title: Enumerazione CorDebugUserState
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d0394d511197c8d0aaa366ce7b791216a3d226bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120195"
---
# <a name="cordebuguserstate-enumeration"></a>Enumerazione CorDebugUserState
Indica lo stato utente di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Members  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|È stata richiesta una terminazione del thread.|  
|`USER_SUSPEND_REQUESTED`|È stata richiesta una sospensione del thread.|  
|`USER_BACKGROUND`|Il thread è in esecuzione in background.|  
|`USER_UNSTARTED`|L'esecuzione del thread non è stata avviata.|  
|`USER_STOPPED`|Il thread è stato terminato.|  
|`USER_WAIT_SLEEP_JOIN`|Il thread è in attesa del completamento di un'attività da parte di un altro thread.|  
|`USER_SUSPENDED`|Il thread è stato sospeso.|  
|`USER_UNSAFE_POINT`|Il thread si trova in un punto non sicuro. Ovvero, il thread si trova in un punto di esecuzione in cui può bloccare Garbage Collection.<br /><br /> Gli eventi di debug possono essere inviati da punti unsafe, ma la sospensione di un thread in un punto non sicuro provocherà molto probabilmente un deadlock finché il thread non verrà ripreso. I punti safe e unsafe sono determinati dall'implementazione JIT (just-in-Time) e Garbage Collection.|  
|`USER_THREADPOOL`|Il thread viene dal pool di thread.|  
  
## <a name="remarks"></a>Note  
 Lo stato utente di un thread è lo stato che il thread ha quando viene esaminato dal debugger. Un thread può avere una combinazione di stati utente.  
  
 Usare il metodo [ICorDebugThread:: GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) per recuperare lo stato utente di un thread.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazioni di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
