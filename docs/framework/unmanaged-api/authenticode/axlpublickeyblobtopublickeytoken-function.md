---
title: Funzione _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e2459b4f91e7e189990b65fa4d7ca860ff73c51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741321"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>\_Funzione AxlPublicKeyBlobToPublicKeyToken
Calcola il token di chiave pubblica con nome sicuro da un formato CSP PUBLICKEYBLOB.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pCspPublicKeyBlob`  
 [in] BLOB a chiave pubblica CSP.  
  
 `ppwszPublicKeyHash`  
 [out] Puntatore a WCHAR * per ricevere l'hash di chiave pubblica con codifica esadecimale.  
  
## <a name="return-value"></a>Valore restituito  
 `S_OK` se la funzione ha esito positivo; in caso contrario, `S_FALSE`.  
  
## <a name="see-also"></a>Vedere anche

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
