---
title: Metodo ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196330"
---
# <a name="icordebugchaingetcallee-method"></a>Metodo ICorDebugChain::GetCallee
Ottiene la catena chiamata dalla catena.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `ppChain`  
 out Puntatore all'indirizzo di un oggetto ICorDebugChain che rappresenta la catena chiamata. Se questa catena è attualmente in esecuzione (ovvero se questa catena non è in attesa della restituzione di una catena chiamata), `ppChain` sarà null.  
  
## <a name="remarks"></a>Note  
 Questa catena attende che la catena chiamata restituisca prima di riprendere l'esecuzione. La catena chiamata può trovarsi in un altro thread nel caso di chiamate con marshalling tra thread.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
