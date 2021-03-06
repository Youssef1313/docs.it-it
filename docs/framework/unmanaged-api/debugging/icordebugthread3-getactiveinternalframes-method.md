---
title: Metodo ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: b4f228d55c9ffd6b85ebd0b430a7f5db404320f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124342"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>Metodo ICorDebugThread3::GetActiveInternalFrames
Restituisce una matrice di frame interni (oggetti[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) nello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>Parametri  
 `cInternalFrames`  
 in Numero di frame interni previsti in `ppInternalFrames`.  
  
 `pcInternalFrames`  
 out Puntatore a un `ULONG32` che contiene il numero di frame interni nello stack.  
  
 `ppInternalFrames`  
 [in, out] Puntatore all'indirizzo di una matrice di frame interni nello stack.  
  
## <a name="return-value"></a>Valore restituito  
 Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Creazione dell'oggetto [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) completata.|  
|E_INVALIDARG|`cInternalFrames` non è zero e `ppInternalFrames` è `null`o `pcInternalFrames` è `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` è inferiore al numero di frame interni.|  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 I frame interni sono strutture di dati inserite nello stack dal runtime per archiviare i dati temporanei.  
  
 Quando si chiama per la prima volta `GetActiveInternalFrames`, è necessario impostare il parametro `cInternalFrames` su 0 (zero) e il parametro `ppInternalFrames` su null. Quando `GetActiveInternalFrames` viene restituito per la prima volta, `pcInternalFrames` contiene il conteggio dei frame interni nello stack.  
  
 `GetActiveInternalFrames` deve quindi essere chiamato una seconda volta. È necessario passare il conteggio appropriato (`pcInternalFrames`) nel parametro `cInternalFrames` e specificare un puntatore a una matrice di dimensioni appropriate in `ppInternalFrames`.  
  
 Usare il metodo [ICorDebugStackWalk:: GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) per restituire gli stack frame effettivi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
