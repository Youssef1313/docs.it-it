---
title: Struttura COR_GC_THREAD_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f56ceca5269ebffb29908c63e698ce794027d8a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768054"
---
# <a name="corgcthreadstats-structure"></a>Struttura COR_GC_THREAD_STATS
Contiene le statistiche per ogni thread relative alla garbage collection.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`PerThreadAllocation`|Il numero di byte di memoria allocata nel thread in cui è associato all'oggetto corrente `COR_GC_THREAD_STATS` istanza. Questo numero viene impostato su zero ogni volta che si verifica una da zero la generazione di garbage collection.|  
|`Flags`|Il numero di byte promossi a una generazione superiore le più recenti di garbage collection.|  
  
## <a name="remarks"></a>Note  
 [ICLRTask:: GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) accetta un parametro di output di tipo `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** GCHost.idl  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Strutture di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Interfaccia IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
