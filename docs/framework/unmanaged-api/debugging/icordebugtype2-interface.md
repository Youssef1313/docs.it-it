---
title: Interfaccia ICorDebugType2
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e953fa129308527f63df8dd8c5061252f8be57b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772440"
---
# <a name="icordebugtype2-interface"></a>Interfaccia ICorDebugType2
Estende l'interfaccia ICorDebugType per recuperare l'identificatore del tipo di un tipo di base o complesso (tipo definito dall'utente).  
  
## <a name="methods"></a>Metodi  
  
|Metodo||  
|------------|-|  
|[Metodo GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Ottiene un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) per questo tipo.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è un'estensione logica dell'interfaccia ICorDebugType.  
  
> [!NOTE]
>  Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.  
  
## <a name="example"></a>Esempio  
 Il frammento di codice seguente viene illustrato l'utilizzo dei [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) (metodo).  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
