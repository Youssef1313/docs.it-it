---
title: Metodo ICorDebugStackWalk::GetFrame
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131830"
---
# <a name="icordebugstackwalkgetframe-method"></a>Metodo ICorDebugStackWalk::GetFrame
Ottiene il frame corrente nell'oggetto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parametri  
 `pFrame`  
 in Puntatore all'indirizzo dell'oggetto frame creato che rappresenta il frame corrente nello stack.  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Il runtime ha restituito correttamente il frame corrente.|  
|E_FAIL|Il frame corrente non è stato restituito.|  
|S_FALSE|Il frame corrente è un stack frame nativo.|  
|E_INVALIDARG|`pFrame` è null.|  
|CORDBG_E_PAST_END_OF_STACK|Il puntatore al frame è già alla fine dello stack. non è pertanto possibile accedere a nessun frame aggiuntivo.|  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 `ICorDebugStackWalk` restituisce solo stack frame effettivi. Usare il metodo [ICorDebugThread3:: GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) per restituire frame interni. (I frame interni sono strutture di dati inserite nello stack dal runtime per archiviare i dati temporanei).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
