---
title: Funzione CorBindToRuntime
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138306"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="50e5e-102">Funzione CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="50e5e-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="50e5e-103">Consente agli host non gestiti di caricare il Common Language Runtime (CLR) in un processo.</span><span class="sxs-lookup"><span data-stu-id="50e5e-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="50e5e-104">Questa funzione è stata deprecata nel .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="50e5e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e5e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="50e5e-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50e5e-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="50e5e-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="50e5e-107">in Stringa che descrive la versione di CLR che si desidera caricare.</span><span class="sxs-lookup"><span data-stu-id="50e5e-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="50e5e-108">Un numero di versione nel .NET Framework è costituito da quattro parti separate da punti: *Major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="50e5e-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="50e5e-109">La stringa passata come `pwszVersion` deve iniziare con il carattere "v" seguito dalle prime tre parti del numero di versione (ad esempio, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="50e5e-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="50e5e-110">Alcune versioni di CLR vengono installate con un'istruzione di criteri che specifica la compatibilità con le versioni precedenti di CLR.</span><span class="sxs-lookup"><span data-stu-id="50e5e-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="50e5e-111">Per impostazione predefinita, lo shim di avvio valuta `pwszVersion` rispetto alle istruzioni dei criteri e carica la versione più recente del runtime compatibile con la versione richiesta.</span><span class="sxs-lookup"><span data-stu-id="50e5e-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="50e5e-112">Un host può forzare lo shim a ignorare la valutazione dei criteri e caricare la versione esatta specificata in `pwszVersion` passando un valore `STARTUP_LOADER_SAFEMODE` per il parametro `flags`, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="50e5e-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="50e5e-113">Se il chiamante specifica null per `pwszVersion`, viene caricata la versione più recente del runtime.</span><span class="sxs-lookup"><span data-stu-id="50e5e-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="50e5e-114">Il passaggio di valori null consente all'host di non controllare la versione del runtime caricata.</span><span class="sxs-lookup"><span data-stu-id="50e5e-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="50e5e-115">Sebbene questo approccio possa essere appropriato in alcuni scenari, si consiglia vivamente all'host di fornire una versione specifica da caricare.</span><span class="sxs-lookup"><span data-stu-id="50e5e-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="50e5e-116">in Stringa che specifica se caricare il server o la build della workstation di CLR.</span><span class="sxs-lookup"><span data-stu-id="50e5e-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="50e5e-117">I valori validi sono `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="50e5e-118">La compilazione server è ottimizzata per sfruttare i vantaggi di più processori per le operazioni di Garbage Collection e la compilazione della workstation è ottimizzata per le applicazioni client in esecuzione su un computer a processore singolo.</span><span class="sxs-lookup"><span data-stu-id="50e5e-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="50e5e-119">Se `pwszBuildFlavor` è impostato su null, viene caricata la compilazione della workstation.</span><span class="sxs-lookup"><span data-stu-id="50e5e-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="50e5e-120">Quando è in esecuzione in un computer a processore singolo, la compilazione della workstation viene sempre caricata, anche se `pwszBuildFlavor` è impostata su `svr`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="50e5e-121">Tuttavia, se `pwszBuildFlavor` è impostato su `svr` e viene specificata la Garbage Collection simultanea (vedere la descrizione del parametro `flags`), viene caricata la build del server.</span><span class="sxs-lookup"><span data-stu-id="50e5e-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="50e5e-122">in `CLSID` della coclasse che implementa l'interfaccia [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="50e5e-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="50e5e-123">I valori supportati sono CLSID_CorRuntimeHost o CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="50e5e-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="50e5e-124">in `IID` dell'interfaccia richiesta da `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="50e5e-125">I valori supportati sono IID_ICorRuntimeHost o IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="50e5e-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="50e5e-126">out Puntatore a interfaccia restituito per `riid`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50e5e-127">Note</span><span class="sxs-lookup"><span data-stu-id="50e5e-127">Remarks</span></span>  
 <span data-ttu-id="50e5e-128">Se `pwszVersion` specifica una versione di Runtime inesistente, `CorBindToRuntimeEx` restituisce un valore HRESULT di CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="50e5e-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="50e5e-129">Contesto di esecuzione e flusso di identità Windows</span><span class="sxs-lookup"><span data-stu-id="50e5e-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="50e5e-130">Nella versione 1 di CLR, l'oggetto <xref:System.Security.Principal.WindowsIdentity> non viene propagato tra punti asincroni, ad esempio nuovi thread, pool di thread o callback del timer.</span><span class="sxs-lookup"><span data-stu-id="50e5e-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="50e5e-131">Nella versione 2,0 di CLR, un oggetto <xref:System.Threading.ExecutionContext> esegue il wrapping di alcune informazioni sul thread attualmente in esecuzione e lo trasmette attraverso qualsiasi punto asincrono, ma non tra i limiti del dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="50e5e-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="50e5e-132">Analogamente, anche l'oggetto <xref:System.Security.Principal.WindowsIdentity> scorre in qualsiasi punto asincrono.</span><span class="sxs-lookup"><span data-stu-id="50e5e-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="50e5e-133">Quindi, la rappresentazione corrente sul thread, se presente, scorre anche.</span><span class="sxs-lookup"><span data-stu-id="50e5e-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="50e5e-134">È possibile modificare il flusso in due modi:</span><span class="sxs-lookup"><span data-stu-id="50e5e-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="50e5e-135">Modificando le impostazioni di <xref:System.Threading.ExecutionContext> per disattivare il flusso in base ai singoli thread (vedere i metodi <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).</span><span class="sxs-lookup"><span data-stu-id="50e5e-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="50e5e-136">Modificando la modalità predefinita del processo con la modalità di compatibilità versione 1, in cui l'oggetto <xref:System.Security.Principal.WindowsIdentity> non viene propagato in alcun punto asincrono, indipendentemente dalle impostazioni <xref:System.Threading.ExecutionContext> sul thread corrente.</span><span class="sxs-lookup"><span data-stu-id="50e5e-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="50e5e-137">La modalità di modifica della modalità predefinita varia a seconda che si usi un eseguibile gestito o un'interfaccia di hosting non gestita per caricare il CLR:</span><span class="sxs-lookup"><span data-stu-id="50e5e-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="50e5e-138">Per i file eseguibili gestiti, è necessario impostare l'attributo `enabled` dell'elemento [\<> legacyImpersonationPolicy](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) su `true`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="50e5e-139">Per le interfacce di hosting non gestite, impostare il flag `STARTUP_LEGACY_IMPERSONATION` nel parametro `flags` quando si chiama la funzione `CorBindToRuntimeEx`.</span><span class="sxs-lookup"><span data-stu-id="50e5e-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="50e5e-140">La modalità di compatibilità versione 1 si applica all'intero processo e a tutti i domini applicazione nel processo.</span><span class="sxs-lookup"><span data-stu-id="50e5e-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50e5e-141">Note</span><span class="sxs-lookup"><span data-stu-id="50e5e-141">Remarks</span></span>  
 <span data-ttu-id="50e5e-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e `CorBindToRuntime` eseguono la stessa operazione, ma la funzione `CorBindToRuntimeEx` consente di impostare i flag per specificare il comportamento di CLR.</span><span class="sxs-lookup"><span data-stu-id="50e5e-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e5e-143">Requisiti</span><span class="sxs-lookup"><span data-stu-id="50e5e-143">Requirements</span></span>  
 <span data-ttu-id="50e5e-144">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e5e-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e5e-145">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50e5e-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50e5e-146">**Libreria:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="50e5e-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50e5e-147">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e5e-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e5e-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="50e5e-148">See also</span></span>

- [<span data-ttu-id="50e5e-149">Funzione CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="50e5e-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="50e5e-150">Funzione CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="50e5e-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="50e5e-151">Funzione CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="50e5e-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="50e5e-152">Funzione CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="50e5e-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="50e5e-153">Interfaccia ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="50e5e-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="50e5e-154">Funzioni di hosting CLR deprecate</span><span class="sxs-lookup"><span data-stu-id="50e5e-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
