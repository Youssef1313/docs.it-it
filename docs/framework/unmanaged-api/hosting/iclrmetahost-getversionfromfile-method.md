---
title: Metodo ICLRMetaHost::GetVersionFromFile
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17b36f66a9b8b78b16057ec37d3ee5f484f7ae2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779757"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>Metodo ICLRMetaHost::GetVersionFromFile
Ottiene .NET Framework versione di compilazione originale un assembly (archiviato nei metadati), dato il percorso di file. Questo metodo sostituisce le [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) (funzione).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pwzFilePath`  
 [in] Il percorso del file completo dell'assembly.  
  
 `pwzbuffer`  
 [out] La versione di compilazione di .NET Framework archiviata nei metadati, nel formato "v*un'* . *B*[. *X*] ". *Oggetto*, *B*, e *X* sono numeri decimali che corrispondono alla versione principale, la versione secondaria e il numero di build. La lunghezza di questa stringa è limitata a MAX_PATH.  
  
> [!NOTE]
>  Questo output corrisponde al nome di directory per la versione di .NET Framework, così come appare sotto C:\Windows\Microsoft.NET\Framework.  
  
 I valori di esempio sono "v1.0.3705", "v1.1.4322", "v2.0.50727" e "v4.0. *X*", dove *X* dipende dal numero di build installato. Si noti che è necessario il prefisso "v".  
  
 `pcchBuffer`  
 [in, out] Le dimensioni di `pwzbuffer` per evitare i sovraccarichi del buffer.  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Metodo completato correttamente.|  
|E_POINTER|`pwzbuffer` o `pcchBuffer` è null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Il buffer è troppo piccolo.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MetaHost.h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
