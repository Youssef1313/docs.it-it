---
title: Funzione InheritsFrom (riferimenti alle API non gestite)
description: La funzione InheritsFrom determina se una classe o istanza deriva da una classe padre specifica.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c04a08c9712359453b9c5a9d136e22e1de8648a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746500"
---
# <a name="inheritsfrom-function"></a>InheritsFrom (funzione)
Determina se la classe o l'istanza corrente deriva da una classe padre specificata.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>Parametri

`vFunc`  
[in] Questo parametro è inutilizzato.

`ptr`  
[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.

`wszAncestor`  
[in] Il nome della classe. `wszAncestor` deve puntare a un valore valido `LPCWSTR`.

## <a name="return-value"></a>Valore restituito

I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:

|Costante  |Valore  |DESCRIZIONE  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | L'oggetto corrente eredita da `wszAncestor`.  |
| `WBEM_S_FALSE` | 1 | L'oggetto corrente non eredita da `wszAncestor`. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` è `null`. |
  
## <a name="remarks"></a>Note

Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) (metodo).

## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** WMINet_Utils.idl  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vedere anche

- [WMI e contatori delle prestazioni (riferimenti alle API non gestite)](index.md)
