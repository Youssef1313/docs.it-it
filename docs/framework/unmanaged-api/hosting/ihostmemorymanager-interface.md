---
title: Interfaccia IHostMemoryManager
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128653"
---
# <a name="ihostmemorymanager-interface"></a>Interfaccia IHostMemoryManager
Fornisce metodi che consentono all'Common Language Runtime (CLR) di effettuare richieste di memoria virtuale attraverso l'host, anziché utilizzare le funzioni di memoria virtuale Win32 standard.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo AcquiredVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Notifica all'host che la Common Language Runtime (CLR) ha acquisito la memoria specificata dal sistema operativo.|  
|[Metodo CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Ottiene un puntatore a interfaccia a un'istanza di [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) utilizzata per richiedere allocazioni di memoria da un heap creato dall'host.|  
|[Metodo GetMemoryLoad](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Ottiene la quantità di memoria fisica attualmente in uso, come segnalato dall'host.|  
|[Metodo NeedsVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Notifica all'host che CLR tenterà di utilizzare la memoria specificata.|  
|[Metodo RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Registra un puntatore a una funzione di callback richiamata dall'host per notificare a CLR il carico di memoria corrente nel computer.|  
|[Metodo ReleasedVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Notifica all'host che CLR ha terminato di utilizzare la memoria specificata.|  
|[Metodo VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Funge da wrapper logico per la funzione Win32 corrispondente, che consente di riservare o eseguire il commit di un'area di pagine nello spazio degli indirizzi virtuali del processo chiamante.|  
|[Metodo VirtualFree](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Funge da wrapper logico per la funzione Win32 corrispondente, che rilascia, decommit o rilascia un'area di pagine all'interno dello spazio degli indirizzi virtuali del processo chiamante.|  
|[Metodo VirtualProtect](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Funge da wrapper logico per la funzione Win32 corrispondente, che modifica la protezione in un'area di pagine di cui è stato eseguito il commit nello spazio degli indirizzi virtuali del processo chiamante.|  
|[Metodo VirtualQuery](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Funge da wrapper logico per la funzione Win32 corrispondente, che recupera informazioni su un intervallo di pagine nello spazio degli indirizzi virtuali del processo chiamante.|  
  
## <a name="remarks"></a>Note  
 `IHostMemoryManager` fornisce inoltre metodi che consentono a CLR di ottenere un puntatore tramite il quale eseguire richieste di memoria nell'heap e ottenere il livello di utilizzo di memoria nel processo, come riportato dall'host.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE. h  
  
 **Libreria:** Incluso come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Interfacce di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
