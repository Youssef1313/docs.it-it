---
title: Funzione CorBindToRuntimeEx
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84e4c70c973fb19be6800d2cbaf76ea137f58b28
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767949"
---
# <a name="corbindtoruntimeex-function"></a>Funzione CorBindToRuntimeEx
Consente l'host non gestiti di caricare common language runtime (CLR) in un processo. Il [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` funzioni eseguono la stessa operazione, ma il `CorBindToRuntimeEx` funzione consente di impostare i flag per specificare il comportamento di CLR.  
  
 Questa funzione è stata deprecata in .NET Framework 4.  
  
 Questa funzione accetta un set di parametri che consentono a un host eseguire le operazioni seguenti:  
  
- Specificare la versione del runtime che verrà caricato.  
  
- Indicare se la compilazione di server o workstation deve essere caricata.  
  
- Controllare se l'operazione garbage collection simultanea o non simultanea operazione di garbage collection viene eseguita.  
  
> [!NOTE]
>  Garbage collection simultanea non è supportata nelle applicazioni in esecuzione WOW64 x86 dell'emulatore su sistemi a 64 bit che implementino l'architettura Intel Itanium (in precedenza denominato IA-64). Per altre informazioni sull'utilizzo di WOW64 nei sistemi Windows a 64 bit, vedere [delle applicazioni in esecuzione a 32 bit](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Controllare se gli assembly vengono caricati come indipendenti dal dominio.  
  
- Ottenere un puntatore a interfaccia a un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) che può essere utilizzato per impostare opzioni aggiuntive per la configurazione di un'istanza di Common Language Runtime prima che venga avviato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pwszVersion`  
 [in] Stringa che descrive la versione di CLR a cui si desidera caricare.  
  
 Un numero di versione in .NET Framework è costituito da quattro parti separate da punti: *revisione*. La stringa passata come `pwszVersion` deve iniziare con il carattere "v" seguito dalle prime tre parti del numero di versione (ad esempio, "v 1.0.1529").  
  
 Alcune versioni di CLR installate con un'istruzione di criteri che specifica la compatibilità con le versioni precedenti di CLR. Per impostazione predefinita, valuta lo shim di avvio `pwszVersion` contro le istruzioni dei criteri e carichi la versione più recente del runtime che è compatibile con la versione richiesta. Un host può forzare lo shim per ignorare la valutazione dei criteri e caricare la versione esatta specificata nel `pwszVersion` passando un valore di `STARTUP_LOADER_SAFEMODE` per il `startupFlags` parametro, come descritto di seguito.  
  
 Se il chiamante specifica null per `pwszVersion`, `CorBindToRuntimeEx` identifica il set di runtime installati cui numeri di versione sono inferiori al runtime di .NET Framework 4 e carica la versione più recente del runtime da tale set. Non caricherà il .NET Framework 4 o versione successiva e non riesce se non è installata alcuna versione precedente. Si noti che il passaggio di null non consente all'host di alcun controllo sulla quale versione del runtime è caricata. Sebbene questo approccio potrebbe essere appropriato in alcuni scenari, è consigliabile che l'host di fornisca una versione specifica di caricare.  
  
 `pwszBuildFlavor`  
 [in] Stringa che specifica se caricare il server o la compilazione di workstation di CLR. I valori validi sono `svr` e `wks`. La compilazione di server è ottimizzata per sfruttare più processori per operazioni di garbage collection e la compilazione di workstation è ottimizzata per le applicazioni client in esecuzione in un computer a processore singolo.  
  
 Se `pwszBuildFlavor` è impostato su null, la compilazione di workstation viene caricata. Durante l'esecuzione in un computer a processore singolo, la compilazione di workstation viene sempre caricata, anche se `pwszBuildFlavor` è impostata su `svr`. Tuttavia, se `pwszBuildFlavor` è impostata su `svr` e garbage collection simultanea è specificata (vedere la descrizione del `startupFlags` parametro), viene caricata la compilazione di server.  
  
 `startupFlags`  
 [in] Una combinazione di valori del [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumerazione. Questi flag controllano il comportamento di garbage collection simultanea e il codice indipendente dal dominio la `pwszVersion` parametro. Se non è impostato alcun flag, il valore predefinito è singolo dominio. Di seguito vengono illustrati i valori validi.  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Per una descrizione di questi flag, vedere la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumerazione.  
  
 `rclsid`  
 [in] Il `CLSID` della coclasse che implementa il [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) o il [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfaccia. I valori supportati sono CLSID_CorRuntimeHost o CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] Il `IID` dell'interfaccia richiesta da `rclsid`. Valori supportati sono IID_ICorRuntimeHost o IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Il puntatore a interfaccia restituito `riid`.  
  
## <a name="remarks"></a>Note  
 Se `pwszVersion` specifica una versione di runtime che non esiste, `CorBindToRuntimeEx` restituisce un valore HRESULT di CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contesto di esecuzione e il flusso dell'identità di Windows  
 Nella versione 1 di CLR, il <xref:System.Security.Principal.WindowsIdentity> oggetto non passa attraverso punti asincroni, ad esempio nuovi thread, i pool di thread o i callback di timer. Nella versione 2.0 di CLR, un <xref:System.Threading.ExecutionContext> oggetto esegue il wrapping di alcune informazioni relative al thread attualmente in esecuzione e ne effettua attraverso punti asincroni qualsiasi, ma non tra i limiti del dominio applicazione. Analogamente, il <xref:System.Security.Principal.WindowsIdentity> oggetto anche passa attraverso punti asincroni qualsiasi. Pertanto, la rappresentazione corrente nel thread, se presente, flussi troppo.  
  
 È possibile modificare il flusso in due modi:  
  
1. Modificando la <xref:System.Threading.ExecutionContext> le impostazioni per sopprimere il flusso in un singolo thread (vedere la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metodi).  
  
2. Modificando la modalità predefinita del processo per la modalità di compatibilità di versione 1, in cui il <xref:System.Security.Principal.WindowsIdentity> oggetto non passa attraverso punti asincroni, qualsiasi indipendentemente il <xref:System.Threading.ExecutionContext> impostazioni sul thread corrente. Come si modifica la modalità predefinita varia a seconda se si usa un file eseguibile gestito o un'interfaccia di hosting non gestita per caricamento di CLR:  
  
    1. Per gli eseguibili gestiti, è necessario impostare il `enabled` attributo del [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento `true`.  
  
    2. Per non gestiti di interfacce di hosting, impostare il `STARTUP_LEGACY_IMPERSONATION` flag nel `startupFlags` parametro quando si chiama il `CorBindToRuntimeEx` (funzione).  
  
     La modalità di compatibilità di versione 1 si applica all'intero processo e per tutti i domini applicazione nel processo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE.h  
  
 **Libreria:** MSCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Funzione CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Funzione CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [Funzione CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Funzione CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interfaccia ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funzioni di hosting CLR deprecate](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
