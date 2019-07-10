---
title: Metodo ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38ff08fa7e7db986006c4e0e09b1ac9cf1be801e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767144"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>Metodo ICorDebugProcess5::EnableNGENPolicy
Imposta un valore che determina la modalità di caricamento delle immagini native durante l'esecuzione con un debugger gestito in un'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `ePolicy`  
 [in] Oggetto [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) costante che determina la modalità di caricamento delle immagini native durante l'esecuzione con un debugger gestito in un'applicazione.  
  
## <a name="remarks"></a>Note  
 Se i criteri sono impostati correttamente, il metodo restituisce `S_OK`. Se `ePolicy` è compreso nell'intervallo dei valori enumerati definito da [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), il metodo restituisce `E_INVALIDARG` e la chiamata al metodo non ha alcun effetto. Se non è possibile aggiornare i criteri del generatore di immagini Native (Ngen.exe), il metodo restituisce `E_FAIL`.  
  
 Il `ICorDebugProcess5::EnableNGenPolicy` metodo può essere chiamato in qualsiasi momento durante il ciclo di vita del processo. È in vigore per tutti i moduli caricati dopo che il criterio è impostato il criterio.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
