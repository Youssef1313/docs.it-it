---
title: Interfaccia ICorDebugReferenceValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137715"
---
# <a name="icordebugreferencevalue-interface"></a>Interfaccia ICorDebugReferenceValue
Fornisce metodi che gestiscono un valore che è un riferimento a un oggetto. (Ovvero, questa interfaccia fornisce metodi per la gestione di un puntatore). Questa interfaccia implementa "ICorDebugValue".  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo Dereference](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Ottiene l'oggetto a cui si fa riferimento.|  
|[Metodo DereferenceStrong](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Non implementato. Non chiamare questo metodo.|  
|[Metodo GetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Ottiene l'indirizzo di memoria corrente dell'oggetto a cui si fa riferimento.|  
|[Metodo IsNull](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Ottiene un valore che indica se questo `ICorDebugReferenceValue` è un valore null, nel qual caso l'`ICorDebugReferenceValue` non punta a un oggetto.|  
|[Metodo SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Imposta l'indirizzo di memoria corrente. Questo metodo imposta questa `ICorDebugReferenceValue` in modo che punti a un oggetto.|  
  
## <a name="remarks"></a>Note  
 Il Common Language Runtime (CLR) può eseguire una Garbage Collection sugli oggetti quando il processo sottoposto a debug viene continuato. Il Garbage Collection può spostare gli oggetti in memoria. Un `ICorDebugReferenceValue` collaborerà con l'Garbage Collection in modo che le informazioni vengano aggiornate dopo l'Garbage Collection o verranno invalidate in modo implicito prima del Garbage Collection.  
  
 L'oggetto `ICorDebugReferenceValue` può essere invalidato in modo implicito dopo che è stato proseguito il processo sottoposto a debug. Il "ICorDebugHandleValue" derivato non viene invalidato fino a quando non viene rilasciato o esposto in modo esplicito.  
  
> [!NOTE]
> Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
