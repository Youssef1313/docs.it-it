---
title: Metodo ICLRDebuggingLibraryProvider::ProvideLibrary
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 8fc2abd0728115edbbfae42958d8013029523ed1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111367"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>Metodo ICLRDebuggingLibraryProvider::ProvideLibrary

Ottiene un'interfaccia di callback del provider di librerie che consente di trovare e caricare su richiesta Common Language Runtime librerie di debug specifiche della versione di CLR.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a>Parametri

`pwszFilename` \
in Nome del modulo richiesto.

`dwTimestamp` \
in Indicatore di data e ora archiviato nell'intestazione del file COFF dei file PE.

`pLibraryProvider` \
in Il campo `SizeOfImage` archiviato nell'intestazione file facoltativa COFF dei file PE.

`hModule` \
out Handle per il modulo richiesto.

## <a name="return-value"></a>Valore restituito

Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.

|HRESULT|Descrizione|
|-------------|-----------------|
|S_OK|Metodo completato correttamente.|

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Note

`ProvideLibrary` consente al debugger di fornire i moduli necessari per il debug di file CLR specifici, ad esempio mscordbi. dll e mscordacwks. dll. Gli handle del modulo devono rimanere validi fino a quando una chiamata al metodo [ICLRDebugging:: CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) non indica che possono essere liberati, a quel punto è responsabilità del chiamante liberare gli handle.

Il debugger può utilizzare qualsiasi mezzo disponibile per individuare o procurare il modulo di debug.

> [!IMPORTANT]
> Questa funzionalità consente al chiamante dell'API di fornire moduli che contengono codice eseguibile e possibilmente dannoso. Per motivi di sicurezza, il chiamante non deve usare `ProvideLibrary` per distribuire il codice che non è disposto a eseguire se stesso.
>
> Se viene individuato un problema di sicurezza grave in una libreria già rilasciata, ad esempio mscordbi. dll o mscordacwks. dll, è possibile applicare una patch allo shim per riconoscere le versioni non valide dei file. Lo shim può quindi inviare richieste per le versioni con patch dei file e rifiutare le versioni non valide se vengono fornite in risposta a una richiesta. Questa situazione può verificarsi solo se l'utente ha eseguito la correzione a una nuova versione dello shim. Le versioni senza patch rimarranno vulnerabili.

## <a name="requirements"></a>Requisiti

**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).

**Intestazione:** CorDebug.idl, CorDebug.h

**Libreria:** CorGuids.lib

**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
