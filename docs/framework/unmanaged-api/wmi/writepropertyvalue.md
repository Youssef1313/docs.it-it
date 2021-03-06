---
title: Funzione WritePropertyValue (riferimenti alle API non gestite)
description: La funzione WritePropertyValue scrive byte in una proprietà.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107297"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue (funzione)
Scrive un numero specificato di byte in una proprietà identificata da un handle di proprietà.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Parametri

`vFunc`  
in Questo parametro è inutilizzato.

`ptr`  
in Puntatore a un'istanza di [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`lHandle`  
in Intero contenente l'handle che identifica questa proprietà. È possibile recuperare l'handle chiamando la funzione [GetPropertyHandle](getpropertyhandle.md) .   

`lNumBytes`  
in Numero di byte scritti nella proprietà. Per ulteriori informazioni, vedere la sezione [osservazioni](#remarks) .

`pHandle`   
out Puntatore alla matrice di byte che contiene i dati.

## <a name="return-value"></a>Valore restituito

I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:

|Costante  |Value  |Descrizione  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametro non valido. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Si è verificata una mancata corrispondenza del tipo. |
|`WBEM_S_NO_ERROR` | 0 | La chiamata di funzione è stata completata.  |
  
## <a name="remarks"></a>Note

Questa funzione esegue il wrapping di una chiamata al metodo [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .

Usare questa funzione per impostare la stringa e tutti gli altri dati non`DWORD` o non`QWORD`.

Per i valori di proprietà non stringa, `lNumBytes` deve essere la dimensione dei dati corretta del tipo di proprietà specificato. Per i valori delle proprietà di stringa, `lNumBytes` deve essere la lunghezza della stringa specificata in byte e la stringa stessa deve avere una lunghezza pari in byte e essere seguita da un carattere di terminazione null.

## <a name="requirements"></a>Requisiti  
**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).  
  
 **Intestazione:** WMINet_Utils. idl  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vedere anche

- [WMI e contatori delle prestazioni (riferimenti alle API non gestite)](index.md)
