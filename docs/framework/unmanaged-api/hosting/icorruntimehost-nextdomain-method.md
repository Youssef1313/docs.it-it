---
title: Metodo ICorRuntimeHost::NextDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf19d322d8e4d0d05993d22b2aa7e46bda7b5a1d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780071"
---
# <a name="icorruntimehostnextdomain-method"></a>Metodo ICorRuntimeHost::NextDomain
Ottiene un puntatore di interfaccia al dominio successivo nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `hEnum`  
 [in] Enumeratore che è stata ottenuta tramite una chiamata a [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).  
  
 `pAppDomain`  
 [out] Un puntatore a interfaccia per il <xref:System._AppDomain?displayProperty=nameWithType> tipo che rappresenta il dominio successivo nell'enumerazione oppure null se non esistono altri domini.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|L'operazione è riuscita.|  
|S_FALSE|L'operazione non è stato completato o non sono presenti più domini nell'enumerazione.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Se un metodo viene restituito E_FAIL, common language runtime (CLR) non è più utilizzabile nel processo. Le chiamate successive a qualsiasi API di hosting restituiranno HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE.h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Vedere anche

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [Interfaccia ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
