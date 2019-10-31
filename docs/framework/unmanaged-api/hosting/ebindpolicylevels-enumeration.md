---
title: Enumerazione EBindPolicyLevels
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136559"
---
# <a name="ebindpolicylevels-enumeration"></a>Enumerazione EBindPolicyLevels
Fornisce i flag per specificare il livello al quale applicare o modificare i criteri di assembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Members  
  
|Member|Descrizione|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Specifica che i criteri devono essere applicati a livello di amministratore.|  
|`ePolicyLevelApp`|Specifica che i criteri devono essere applicati a livello di applicazione.|  
|`ePolicyLevelHost`|Specifica che i criteri devono essere applicati a livello di host.|  
|`ePolicyLevelNone`|Non specifica alcun flag a livello di criteri.|  
|`ePolicyLevelPublisher`|Specifica che i criteri devono essere applicati a livello di server di pubblicazione.|  
|`ePolicyLevelRetargetable`|Specifica che i criteri devono essere applicabili a livelli variabili.|  
|`ePolicyPortability`|Specifica che i criteri devono supportare la portabilità tra le implementazioni di un assembly .NET Framework. Vedere l'elemento del file di configurazione [\<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) .|  
|`ePolicyUnifiedToCLR`|Specifica che i criteri devono essere unificati a quello del Common Language Runtime (CLR).|  
  
## <a name="remarks"></a>Note  
 Questa enumerazione viene passata ai metodi dell'interfaccia [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) per specificare le modifiche nei criteri dell'applicazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE. h  
  
 **Libreria:** MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Enumerazioni di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
