---
title: Interfaccia ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f78417d613023bb4fb7325560c0c06abe0874aba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967934"
---
# <a name="icordebugvirtualunwinder-interface"></a>Interfaccia ICorDebugVirtualUnwinder
Fornisce metodi che facilitano lo svuotamento dello stack.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Name|  
|------------|----------|  
|[Metodo GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Ottiene il contesto corrente di questo agente di rimozione.|  
|[Metodo Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Avanza fino al contesto del chiamante.|  
  
## <a name="remarks"></a>Note  
 I membri dell'interfaccia `ICorDebugVirtualUnwinder` sono implementati dal debugger per agevolare lo svuotamento dello stack.  
  
> [!NOTE]
> Questa interfaccia è disponibile solo con .NET Native. Se questa interfaccia viene implementata per scenari ICorDebug al di fuori di .NET Native, sarà ignorata da Common Language Runtime.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug. idl, CorDebug. h  
  
 **Libreria** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
