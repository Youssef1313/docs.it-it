---
title: Metodo ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c137a10d5da94d04509385fc97d71535d33fae93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758732"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>Metodo ICorDebugProcess::GetThreadContext
Ottiene il contesto per il thread specificato in questo processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `threadID`  
 [in] L'ID del thread per il quale recuperare il contesto.  
  
 `contextSize`  
 [in] Dimensione della matrice `context`.  
  
 `context`  
 [in, out] Matrice di byte che descrivono il contesto del thread.  
  
 Il contesto specifica l'architettura del processore in cui è in esecuzione il thread.  
  
## <a name="remarks"></a>Note  
 Il debugger deve chiamare questo metodo anziché Win32 `GetThreadContext` metodo, perché il thread effettivamente potrebbe trovarsi in uno stato "cui", in cui il contesto è stato modificato temporaneamente. Questo metodo deve essere utilizzato solo quando un thread in codice nativo. Uso [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) per i thread in codice gestito.  
  
 I dati restituiti sono una struttura scelta per la piattaforma corrente. Come avviene con Win32 `GetThreadContext` metodo, il chiamante deve inizializzare il `context` parametro prima di chiamare questo metodo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
