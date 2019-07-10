---
title: Metodo ICorDebugAppDomain2::GetFunctionPointerType
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f0643ba9e750e7c64d2dae8eb5744df7bc26931
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737796"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a>Metodo ICorDebugAppDomain2::GetFunctionPointerType
Ottiene un puntatore a una funzione che dispone di una determinata firma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `nTypeArgs`  
 [in] Il numero di argomenti tipo per la funzione.  
  
 `ppTypeArgs`  
 [in] Una matrice di puntatori, ognuno dei quali punta a un oggetto ICorDebugType che rappresenta un argomento tipo della funzione. Il primo elemento è il tipo restituito; ognuno degli altri elementi è un tipo di parametro.  
  
 `ppType`  
 [out] Un puntatore all'indirizzo di un `ICorDebugType` oggetto che rappresenta il puntatore alla funzione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
