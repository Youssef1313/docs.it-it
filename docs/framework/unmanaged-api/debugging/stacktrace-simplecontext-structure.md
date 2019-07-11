---
title: Struttura StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0fc18e31b89b22ffd30d99a8b079ed7b87fa1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752495"
---
# <a name="stacktracesimplecontext-structure"></a>Struttura StackTrace_SimpleContext
Fornisce un contesto semplice che può essere usato invece di una struttura `CONTEXT` completa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`StackOffset`|Il puntatore dello stack, o il puntatore dello stack invio (ESP) x86 piattaforme.|  
|`FrameOffset`|L'offset di frame, o il registro EBP x86 piattaforme.|  
|`InstructionOffset`|Il puntatore all'istruzione o il puntatore all'istruzione invio (EIP) x86 piattaforme.|  
  
## <a name="remarks"></a>Note  
 Poiché le funzioni di traccia dello stack in genere necessario restituire solo l'indirizzo di offset di frame e indirizzo dello stack, è possibile usare la `SimpleContext` struttura invece di un grande `CONTEXT` struttura.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** SOS_Stacktrace.h  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Strutture di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
