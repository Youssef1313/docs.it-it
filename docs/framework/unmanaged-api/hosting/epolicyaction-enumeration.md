---
title: Enumerazione EPolicyAction
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404cd5513a1cbd353faed41030a80ec2abef235f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774204"
---
# <a name="epolicyaction-enumeration"></a>Enumerazione EPolicyAction
Descrive le azioni dei criteri dell'host è possibile impostare per le operazioni specificate da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e gli errori indicati dal [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`eAbortThread`|Specifica che common language runtime (CLR) deve interrompere il thread in modo regolare. Interruzione di una normale include i tentativi di eseguire tutti i `finally` consente di bloccare, qualsiasi `catch` i blocchi correlati alle interruzioni di thread e i finalizzatori.|  
|`eDisableRuntime`|Specifica che Common Language Runtime deve essere stato disabilitato. Alcuna ulteriore codice gestito può essere eseguito nel processo interessato e i thread sono bloccati di accedere a CLR.|  
|`eExitProcess`|Specifica che Common Language Runtime deve cercare una chiusura normale del processo, inclusi l'esecuzione dei finalizzatori e di pulitura e operazioni di registrazione.|  
|`eFastExitProcess`|Specifica che Common Language Runtime deve uscire dal processo immediatamente, senza eseguire i finalizzatori o pulizia e operazioni di registrazione. Tuttavia, notifica viene inviata al debugger.|  
|`eNoAction`|Specifica che deve essere eseguita alcuna azione.|  
|`eRudeAbortThread`|Specifica che Common Language Runtime deve eseguire un'interruzione del thread in modo irregolare. Solo a quelli `catch` e `finally` blocchi contrassegnati con <xref:System.EnterpriseServices.MustRunInClientContextAttribute> vengono eseguite.|  
|`eRudeExitProcess`|Specifica che Common Language Runtime deve uscire dal processo senza esecuzione dei finalizzatori o la registrazione delle operazioni.|  
|`eRudeUnloadAppDomain`|Specifica che Common Language Runtime deve eseguire uno scaricamento non regolare del <xref:System.AppDomain>. Solo i finalizzatori contrassegnati con <xref:System.EnterpriseServices.MustRunInClientContextAttribute> vengono eseguite. Allo stesso modo, tutti i thread con questo <xref:System.AppDomain> nei relativi stack ricevere un' `ThreadAbortException`, ma solo quelle `catch` e `finally` i blocchi contrassegnati con <xref:System.EnterpriseServices.MustRunInClientContextAttribute> vengono eseguite.|  
|`eThrowException`|Specifica che deve essere generata un'eccezione appropriata per la condizione, ad esempio di memoria insufficiente, un sovraccarico del buffer e così via.|  
|`eUnloadAppDomain`|Specifica che il <xref:System.AppDomain> deve essere scaricato. Common Language Runtime prova a eseguire i finalizzatori.|  
  
## <a name="remarks"></a>Note  
 L'host imposta le azioni dei criteri chiamando i metodi del [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfaccia. Per informazioni sulle interruzioni regolari e irregolari, vedere la [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumerazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE.h  
  
 **Libreria:** MSCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazione EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [Interfaccia ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Interfaccia IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Enumerazioni di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
