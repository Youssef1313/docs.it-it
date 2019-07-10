---
title: Metodo ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aabc5783e66893d13aed60e04d7ea5f6547c68
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773577"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>Metodo ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
Ottiene l'identità dell'assembly data binding per l'assembly nel percorso del file specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pwzFilePath`  
 [in] Il percorso del file da valutare.  
  
 `dwFlags`  
 [in] Valore di [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumerazione che indica il tipo di identità di un assembly. Fornito per un'estendibilità futura. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT è l'unico valore che supporta common language runtime (CLR) versione 2.0.  
  
 `pwzBuffer`  
 [out] Un buffer contenente i dati di identità di assembly opaco.  
  
 `pcchBufferSize`  
 [in, out] Un puntatore alla dimensione del `pwzBuffer`.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Il metodo è stato restituito correttamente.|  
|E_INVALIDARG|Il parametro fornito `pwzFilePath` è null.|  
|ERROR_INSUFFICIENT_BUFFER|Le dimensioni di `pwzBuffer` è troppo piccolo.|  
|HOST_E_CLRNOTAVAILABLE|CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.|  
|HOST_E_TIMEOUT|Timeout della chiamata.|  
|HOST_E_NOT_OWNER|Il chiamante non possiede il blocco.|  
|HOST_E_ABANDONED|Un evento è stato annullato durante un thread bloccato o fiber è rimasta in attesa su di esso.|  
|E_FAIL|Si è verificato un errore irreversibile sconosciuto. Se un metodo viene restituito E_FAIL, CLR non è più utilizzabile all'interno del processo. Le chiamate successive ai metodi di hosting restituiranno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Note  
 `GetBindingIdentityFromFile` viene in genere chiamato due volte. La prima chiamata fornisce un valore null per `pwzBuffer`, e il metodo restituisce le dimensioni appropriate in `pcchBufferSize`. La seconda chiamata fornisce un buffer allocato in modo appropriato e il metodo viene restituito con i dati effettivi del buffer al completamento.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE.h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Interfaccia ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interfaccia ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
