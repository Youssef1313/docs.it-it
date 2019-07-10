---
title: Funzione NextMethod (riferimenti alle API non gestite)
description: La funzione NextMethod recupera il prossimo metodo in un'enumerazione.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a730947b0c962d801975917cdf752136e7221c4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746484"
---
# <a name="nextmethod-function"></a>NextMethod (funzione)
Recupera il prossimo metodo in un'enumerazione che inizia con una chiamata a [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>Parametri

`vFunc`  
[in] Questo parametro è inutilizzato.

`ptr`  
[in] Un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) istanza.

`lFlags`  
[in] Riservato. Questo parametro deve essere 0.

`pName`  
[out] Un puntatore che punta a `null` prima della chiamata. Quando la funzione restituisce, l'indirizzo di un nuovo `BSTR` che contiene il nome del metodo. 

`ppSignatureIn`  
[out] Un puntatore che riceve un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) che contiene il `in` parametri del metodo. 

`ppSignatureOut`  
[out] Un puntatore che riceve un puntatore a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) che contiene il `out` parametri del metodo. 

## <a name="return-value"></a>Valore restituito

I seguenti valori restituiti da questa funzione sono definiti nel *WbemCli.h* file di intestazione, oppure è possibile definirle come costanti nel codice:

|Costante  |Value  |Descrizione  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Si è verificato alcun chiamata per il [ `BeginEnumeration` ](beginenumeration.md) (funzione). |
| `WBEM_S_NO_ERROR` | 0 | La chiamata di funzione è riuscita.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Non esistono altre proprietà dell'enumerazione. |
  
## <a name="remarks"></a>Note

Questa funzione esegue il wrapping di una chiamata per il [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) (metodo).

Il chiamante avvia la sequenza di enumerazione chiamando il [BeginMethodEnumeration](beginmethodenumeration.md) funzione e quindi chiama la funzione [NextMethod] fino a quando la funzione restituisce `WBEM_S_NO_MORE_DATA`. Facoltativamente, il chiamante termina la sequenza chiamando [EndMethodEnumeration](endmethodenumeration.md). Il chiamante può terminare l'enumerazione all'inizio chiamando [EndMethodEnumeration](endmethodenumeration.md) in qualsiasi momento.

## <a name="example"></a>Esempio

Per un esempio di C++, vedere la [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) (metodo).

## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** WMINet_Utils.idl  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vedere anche

- [WMI e contatori delle prestazioni (riferimenti alle API non gestite)](index.md)
