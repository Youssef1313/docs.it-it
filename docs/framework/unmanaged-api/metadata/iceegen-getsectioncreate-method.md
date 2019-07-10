---
title: Metodo ICeeGen::GetSectionCreate
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de3a9c152f3074339dba330b7827cf795a7e537
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745969"
---
# <a name="iceegengetsectioncreate-method"></a>Metodo ICeeGen::GetSectionCreate
Genera l'errore e ottiene una sezione di codice usando il nome specificato e i valori di flag.  
  
 Questo metodo è obsoleto e non deve essere utilizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `name`  
 [in] Un puntatore a una stringa che specifica il nome della sezione da creare.  
  
 `flags`  
 [in] Flag che specificano le opzioni.  
  
 `section`  
 [out] Puntatore alla sezione di codice appena creato.  
  
## <a name="remarks"></a>Note  
 Chiamare `GetSectionCreate` solo se si hanno requisiti di sezione speciale che non sono gestiti tramite altri metodi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
