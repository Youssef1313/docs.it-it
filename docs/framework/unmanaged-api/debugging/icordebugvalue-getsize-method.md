---
title: Metodo ICorDebugValue::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137087"
---
# <a name="icordebugvaluegetsize-method"></a>Metodo ICorDebugValue::GetSize
Ottiene le dimensioni in byte di questo oggetto "ICorDebugValue".  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pSize`  
 out Dimensione, in byte, di questo oggetto valore.  
  
## <a name="remarks"></a>Note  
 Se il tipo del valore è un tipo di riferimento, questo metodo restituisce le dimensioni del puntatore anziché le dimensioni dell'oggetto.  
  
 Il metodo `ICorDebugValue::GetSize` restituisce `COR_E_OVERFLOW` per oggetti con dimensioni maggiori di 4 GB su piattaforme a 64 bit. Usare invece il metodo [ICorDebugValue3:: GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) per gli oggetti con dimensioni maggiori di 4 GB.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
