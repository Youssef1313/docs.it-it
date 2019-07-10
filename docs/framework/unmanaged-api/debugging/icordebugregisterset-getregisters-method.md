---
title: Metodo ICorDebugRegisterSet::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: daee6c46c247bcd21073f779cada8c843947a949
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747244"
---
# <a name="icordebugregistersetgetregisters-method"></a>Metodo ICorDebugRegisterSet::GetRegisters
Ottiene il valore di ogni registro (nel computer che esegue codice) che viene specificato per la maschera di bit.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `mask`  
 [in] Maschera di bit che specifica quale registro e i valori devono essere recuperati. Ogni bit corrisponde a un registro. Se un bit è impostato su uno, viene recuperato il valore del Registro; in caso contrario, non è possibile recuperare il valore del registro.  
  
 `regCount`  
 [in] Il numero di valori di registro da recuperare.  
  
 `regBuffer`  
 [out] Matrice di `CORDB_REGISTER` oggetti, ognuno dei quali riceve un valore di un registro.  
  
## <a name="remarks"></a>Note  
 Le dimensioni della matrice devono essere uguale al numero di bit impostati su uno nella maschera di bit. Il `regCount` parametro specifica il numero di elementi nel buffer che riceverà i valori di registro. Se il `regCount` valore è troppo piccolo per il numero di registri indicati dalla maschera, i registri numerati più alto verranno troncati dal set. Se il `regCount` valore è troppo grande, inutilizzata `regBuffer` elementi saranno non modificati.  
  
 Se la maschera di bit specifica un registro che non è disponibile, `GetRegisters` restituisce un valore non definito per tale registro.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [Interfaccia ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
