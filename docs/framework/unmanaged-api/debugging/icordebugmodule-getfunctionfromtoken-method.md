---
title: Metodo ICorDebugModule::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 547986633172d6f5e6549ad2048833dc9fb0cef3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763475"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>Metodo ICorDebugModule::GetFunctionFromToken
Ottiene la funzione specificata dal token di metadati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `methodDef`  
 [in] Oggetto `mdMethodDef` token di metadati che fa riferimento ai metadati della funzione.  
  
 `ppFunction`  
 [out] Un puntatore all'indirizzo di un oggetto di interfaccia ICorDebugFunction che rappresenta la funzione.  
  
## <a name="remarks"></a>Note  
 Il `GetFunctionFromToken` metodo restituisce un HRESULT CORDBG_E_FUNCTION_NOT_IL se il valore passato in `methodDef` non fa riferimento a un metodo di Microsoft intermediate language (MSIL).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
