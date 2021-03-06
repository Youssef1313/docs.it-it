---
title: Funzione PutMethod (riferimenti alle API non gestite)
description: La funzione PutMethod crea un metodo.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127339"
---
# <a name="putmethod-function"></a>PutMethod (funzione)
Crea un metodo.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parametri

`vFunc`  
in Questo parametro è inutilizzato.

`ptr`  
in Puntatore a un'istanza di [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`  
in Nome del metodo da creare. 

`lFlags`  
[in] Riservato. Questo parametro deve essere 0.

`pSignatureIn`  
in Puntatore a una copia della classe di [sistema __Parameters](/windows/desktop/WmiSdk/--parameters) che contiene i parametri di `in` per il metodo. Questo parametro viene ignorato se impostato su `null`.  

`pSignatureOut`  
in  Puntatore a una copia della classe di [sistema __Parameters](/windows/desktop/WmiSdk/--parameters) che contiene i parametri di `out` per il metodo. Questo parametro viene ignorato se impostato su `null`.

## <a name="return-value"></a>Valore restituito

I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:

|Costante  |Value  |Descrizione  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Uno o più parametri non sono validi. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Il `[in, out]` parametro del metodo specificato negli oggetti *pInSignature* e *pOutSignature* ha qualificatori diversi.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Nel parametro di un metodo manca la specifica del qualificatore **ID** . |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | La serie di ID assegnata ai parametri del metodo non è consecutiva o non inizia da 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Il valore restituito per un metodo ha un qualificatore **ID** . |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | È stato effettuato un tentativo di riutilizzare un nome di metodo esistente da una classe padre e le firme non corrispondono. |
| `WBEM_S_NO_ERROR` | 0 | La chiamata di funzione è stata completata. |
  
## <a name="remarks"></a>Note

Questa funzione esegue il wrapping di una chiamata al metodo [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

Questa chiamata al metodo è supportata solo se `ptr` è una definizione di classe CIM. La manipolazione dei metodi non è disponibile dai puntatori [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) che puntano a istanze CIM.

Gli utenti non possono creare metodi con nomi che iniziano o terminano con un carattere di sottolineatura. Questa operazione è riservata per le classi e le proprietà di sistema.

Per un metodo, i parametri `in` e `out` sono descritti come proprietà negli oggetti [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Per definire un parametro di `[in/out]`, è possibile aggiungere la stessa proprietà a entrambi gli oggetti a cui puntano i parametri `pInSignature` e `pOutSignature`. In questo caso, le proprietà condividono lo stesso valore di qualificatore **ID** .

Ogni proprietà in un oggetto della classe [__Parameters](/windows/desktop/WmiSdk/--parameters) diverso da `ReturnValue` deve avere un qualificatore **ID** , un valore numerico in base zero che identifica l'ordine in cui vengono visualizzati i parametri. Due parametri non possono avere lo stesso valore **ID** e nessun valore **ID** può essere ignorato. Se si verifica una delle due condizioni, la funzione `PutMethod` restituisce `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Esempio

Per un esempio, vedere il metodo [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).  
  
 **Intestazione:** WMINet_Utils. idl  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vedere anche

- [WMI e contatori delle prestazioni (riferimenti alle API non gestite)](index.md)
