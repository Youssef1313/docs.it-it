---
title: Enumerazione CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740380"
---
# <a name="cordebugblockingreason-enumeration"></a>Enumerazione CorDebugBlockingReason
Specifica i motivi che possono causare il blocco di un thread su un oggetto specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`BLOCKING_NONE`|Solo per uso interno.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Un thread sta tentando di acquisire la sezione critica che è associata il blocco del monitoraggio in un oggetto. In genere, ciò si verifica quando si chiama uno dei <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> o <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metodi.|  
|`BLOCKING_MONITOR_EVENT`|Un thread è in attesa dell'evento associato a un blocco di monitoraggio per un oggetto. In genere, ciò si verifica quando si chiama uno dei <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metodi.|  
  
## <a name="remarks"></a>Note  
 Quando la `BLOCKING_MONITOR_CRITICAL_SECTION` oppure `BLOCKING_MONITOR_EVENT` membro viene utilizzato un [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struttura, il `pBlockingObject` membro della struttura punta a un'interfaccia "ICorDebugValue" che rappresenta l'oggetto che viene viene immesso . È inoltre garantito per implementare il [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazioni di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
