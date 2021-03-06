---
title: Metodo ICorDebugDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 278320391615eddaa8ba878ef87f802f30cddb95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122031"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>Metodo ICorDebugDataTarget::GetThreadContext
Restituisce il contesto del thread corrente per il thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametri  
 `dwThreadID`  
 in Identificatore del thread di cui è necessario recuperare il contesto. L'identificatore viene definito dal sistema operativo.  
  
 `contextFlags`  
 in Combinazione bit per bit di flag dipendenti dalla piattaforma che indicano quali parti del contesto devono essere lette.  
  
 `contextSize`  
 [in] Le dimensioni di `pContext`.  
  
 `pContext`  
 out Buffer in cui verrà archiviato il contesto del thread.  
  
## <a name="remarks"></a>Note  
 Nelle piattaforme Windows, `pContext` deve essere una struttura di `CONTEXT` (definita in WinNT. h) appropriata per il tipo di computer specificato dal metodo [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) . `contextFlags` deve avere gli stessi valori del campo `ContextFlags` della struttura `CONTEXT`. La struttura di `CONTEXT` è specifica del processore. per informazioni dettagliate, vedere il file WinNT. h.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
