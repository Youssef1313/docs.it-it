---
title: Metodo StrongNameSignatureVerificationEx2
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: cf8d6b7e45c0012d223173c85a92fac4fb044c6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141405"
---
# <a name="strongnamesignatureverificationex2-method"></a>Metodo StrongNameSignatureVerificationEx2
Verifica la firma di un assembly con nome sicuro e fornisce un mapping dalla chiave ECMA a una chiave reale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `wszFilePath`  
 in Percorso del file eseguibile (exe o dll) portatile per l'assembly da verificare.  
  
 `fForceVerification`  
 [in] `true` per eseguire la verifica, anche se è necessario eseguire l'override delle impostazioni del registro di sistema; in caso contrario, `false`.  
  
 `pbEcmaPublicKey`  
 in Puntatore al mapping dalla chiave pubblica ECMA alla chiave reale utilizzata per la verifica.  
  
 `cbEcmaPublicKey`  
 in Lunghezza della chiave pubblica ECMA reale.  
  
 `pfWasVerified`  
 [out] `true` se la firma del nome sicuro è stata verificata. in caso contrario, `false`. Questo parametro viene impostato anche su `false` se la verifica ha avuto esito positivo a causa delle impostazioni del registro di sistema.  
  
## <a name="return-value"></a>Valore restituito  
 `S_OK` se la verifica ha avuto esito positivo; in caso contrario, valore HRESULT che indica l'esito negativo (vedere [valori HRESULT comuni](https://go.microsoft.com/fwlink/?LinkId=213878) per un elenco).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Metahost. h  
  
 **Libreria:** Incluso come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [Metodo StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [Interfaccia ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
