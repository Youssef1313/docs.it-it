---
title: Metodo ICorDebug::DebugActiveProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe94203d315c32b62a191adf294a9c1310fe28e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738269"
---
# <a name="icordebugdebugactiveprocess-method"></a>Metodo ICorDebug::DebugActiveProcess
Collega il debugger a un processo esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `id`  
 [in] L'ID del processo a cui il debugger deve essere allegato.  
  
 `win32Attach`  
 [in] Valore booleano che è impostato su `true` se il debugger deve comportarsi come il debugger di Win32 per il processo e inviare il callback non gestite; in caso contrario, `false`.  
  
 `ppProcess`  
 [out] Un puntatore all'indirizzo di un oggetto "ICorDebugProcess" che rappresenta il processo a cui è stato connesso il debugger.  
  
## <a name="remarks"></a>Note  
 Debug di interoperabilità non è supportato nelle piattaforme Win9x e non x86, ad esempio le piattaforme basate su IA-64 e AMD64 basato.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
