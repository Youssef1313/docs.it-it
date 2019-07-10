---
title: Metodo IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 840a3779ca5692787c2c352db60a29d6a4d4ba4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768596"
---
# <a name="ivalidatorvalidate-method"></a>Metodo IValidator::Validate
Convalida lo specificata eseguibile portabile (PE) o il file Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `veh`  
 [in] Un puntatore a un `IVEHandler` istanza che gestisce gli errori di convalida.  
  
 `pAppDomain`  
 [in] Puntatore al dominio dell'applicazione in cui viene caricato il file.  
  
 `ulFlags`  
 [in] Una combinazione bit per bit di [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valori, che indica le convalide da eseguire.  
  
 `ulMaxError`  
 [in] Il numero massimo di errori consentiti prima di disattivare la convalida.  
  
 `token`  
 [in] Non utilizzato.  
  
 `fileName`  
 [in] Stringa che specifica il nome del file da convalidare.  
  
 `pe`  
 [in] Puntatore al buffer di memoria in cui è archiviato il file.  
  
 `ulSize`  
 [in] Le dimensioni, in byte, del file da convalidare.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** IValidator. idl, IValidator. H  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
