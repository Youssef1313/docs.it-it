---
title: Funzione GetObjectText (riferimenti alle API non gestite)
description: La funzione GetObjectText restituisce un testo per il rendering di un oggetto in sintassi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746491"
---
# <a name="getobjecttext-function"></a>Funzione GetObjectText
Restituisce un testo per il rendering dell'oggetto nella sintassi del formato MOF (Managed Object).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametri

`vFunc`  
[in] Questo parametro è inutilizzato.

`ptr`  
[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.

`lFlags`  
[in] In genere 0. Se `WBEM_FLAG_NO_FLAVORS` (o 0x1) viene specificato, i qualificatori sono inclusi senza informazioni di propagazione o una versione.

`pstrObjectText`   
[out] Un puntatore a un `null` in ingresso. Restituzione, appena allocato `BSTR` che contiene informazioni sul rendering sintassi MOF dell'oggetto.  

## <a name="return-value"></a>Valore restituito

I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:

|Costante  |Value  |Descrizione  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Si è verificato un errore generale. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un parametro non è valido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Memoria insufficiente è disponibile per completare l'operazione. |
|`WBEM_S_NO_ERROR` | 0 | La chiamata di funzione è riuscita.  |
  
## <a name="remarks"></a>Note

Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) (metodo).

Il testo MOF restituito non contiene tutte le informazioni sull'oggetto, ma solo le informazioni sufficienti per il file MOF essere in grado di ricreare l'oggetto originale. Ad esempio, non i qualificatori propagati o proprietà della classe padre sono incluse.

Per ricostruire il testo dei parametri di un metodo viene usato l'algoritmo seguente:

1. I parametri sono resequenced nell'ordine dei relativi valori di identificatore.
1. I parametri specificati come `[in]` e `[out]` vengono combinati in un singolo parametro.
 
`pstrObjectText` deve essere un puntatore a un `null` quando viene chiamata la funzione; non deve puntare a una stringa valida prima della chiamata al metodo, perché verrà deallocato non il puntatore del mouse.

## <a name="requirements"></a>Requisiti  
**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** WMINet_Utils.idl  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vedere anche

- [WMI e contatori delle prestazioni (riferimenti alle API non gestite)](index.md)
