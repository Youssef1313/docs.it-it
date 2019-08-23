---
title: Interfaccia ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd7a5f630bcf97277a4f98f2408ecaf04883fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916982"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>Interfaccia ICorDebugMergedAssemblyRecord
Fornisce informazioni su un assembly unito.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo GetCulture](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|Ottiene la stringa del nome delle impostazioni cultura dell'assembly.|  
|[Metodo GetIndex](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|Ottiene l'indice del prefisso dell'assembly.|  
|[Metodo GetPublicKey](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|Ottiene la chiave pubblica dell'assembly.|  
|[Metodo GetPublicKeyToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Ottiene il token di chiave pubblica dell'assembly.|  
|[Metodo GetSimpleName](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|Ottiene il nome semplice dell'assembly.|  
|[Metodo GetVersion](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|Ottiene le informazioni sulla versione dell'assembly.|  
  
## <a name="remarks"></a>Note  
  
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
