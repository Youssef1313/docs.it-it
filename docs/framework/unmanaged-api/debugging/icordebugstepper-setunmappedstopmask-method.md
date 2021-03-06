---
title: Metodo ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137561"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>Metodo ICorDebugStepper::SetUnmappedStopMask
Imposta un valore che specifica il tipo di codice non mappato in cui l'esecuzione si arresterà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `mask`  
 in Valore dell'enumerazione CorDebugUnmappedStop che specifica il tipo di codice di cui non è stato eseguito il mapping in cui l'esecuzione viene interrotta dal debugger.  
  
 Il valore predefinito è STOP_OTHER_UNMAPPED. Il valore STOP_UNMANAGED è valido solo con il debug di interoperabilità.  
  
## <a name="remarks"></a>Note  
 Quando il debugger trova una compilazione JIT (just-in-Time) che non dispone di un mapping corrispondente a MSIL (Microsoft Intermediate Language), l'esecuzione viene interrotta se il flag che specifica il tipo di codice non mappato è stato impostato. in caso contrario, l'esecuzione di un'istruzione continua in modo trasparente.  
  
 Se il debugger non usa un stepper per accedere a un metodo, non verrà necessariamente eseguito il codice non mappato.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
