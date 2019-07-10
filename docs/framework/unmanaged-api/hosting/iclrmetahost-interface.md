---
title: Interfaccia ICLRMetaHost
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45089d1b64264e000c07603808f0c5fb1263b042
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776579"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="ea13f-102">Interfaccia ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="ea13f-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="ea13f-103">Fornisce metodi che restituiscono una versione specifica di common language runtime (CLR) in base al relativo numero di versione, elencano tutti i runtime installati, elencare tutti i runtime caricati in un processo specifico, individuano la versione CLR usata per compilare un assembly, uscire da un processo con un arresto del runtime pulita e associazione di query legacy API.</span><span class="sxs-lookup"><span data-stu-id="ea13f-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea13f-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="ea13f-104">Methods</span></span>  
  
|<span data-ttu-id="ea13f-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="ea13f-105">Method</span></span>|<span data-ttu-id="ea13f-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ea13f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea13f-107">Metodo EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="ea13f-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="ea13f-108">Restituisce un'enumerazione che contiene un valore valido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) puntatore a interfaccia per ogni versione CLR installata in un computer.</span><span class="sxs-lookup"><span data-stu-id="ea13f-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="ea13f-109">Metodo EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="ea13f-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="ea13f-110">Restituisce un'enumerazione che contiene un valore valido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) puntatore a interfaccia per ogni CLR che viene caricato in un determinato processo.</span><span class="sxs-lookup"><span data-stu-id="ea13f-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="ea13f-111">Questo metodo sostituisce [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="ea13f-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="ea13f-112">Metodo ExitProcess</span><span class="sxs-lookup"><span data-stu-id="ea13f-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="ea13f-113">Tenta di arresto normale runtime caricati tutti e quindi termina il processo.</span><span class="sxs-lookup"><span data-stu-id="ea13f-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="ea13f-114">Sostituisce il [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) (funzione).</span><span class="sxs-lookup"><span data-stu-id="ea13f-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="ea13f-115">Metodo GetRuntime</span><span class="sxs-lookup"><span data-stu-id="ea13f-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="ea13f-116">Ottiene il [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaccia che corrisponde a una particolare versione CLR.</span><span class="sxs-lookup"><span data-stu-id="ea13f-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="ea13f-117">Questo metodo sostituisce le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funzione usato con la [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span><span class="sxs-lookup"><span data-stu-id="ea13f-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="ea13f-118">Metodo GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="ea13f-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="ea13f-119">Ottiene la versione dell'assembly originale .NET Framework la compilazione (archiviata nei metadati), data il percorso di file.</span><span class="sxs-lookup"><span data-stu-id="ea13f-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="ea13f-120">Questo metodo sostituisce [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="ea13f-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="ea13f-121">Metodo QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="ea13f-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="ea13f-122">Restituisce un'interfaccia che rappresenta un runtime a cui sono stati associati i criteri dell'attivazione legacy, ad esempio usando il `useLegacyV2RuntimeActivationPolicy` attributo la [ \<avvio > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) voce file di configurazione mediante l'utilizzo diretto dell'API di attivazione legacy o chiamando il [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="ea13f-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="ea13f-123">Metodo RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="ea13f-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="ea13f-124">Garantisce un callback per il puntatore di funzione specificata quando viene caricata inizialmente una versione di CLR, ma non ancora iniziata.</span><span class="sxs-lookup"><span data-stu-id="ea13f-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="ea13f-125">Questo metodo sostituisce [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="ea13f-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea13f-126">Note</span><span class="sxs-lookup"><span data-stu-id="ea13f-126">Remarks</span></span>  
 <span data-ttu-id="ea13f-127">L'unico modo per ottenere un'istanza di questa interfaccia è chiamando il [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funzionare nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="ea13f-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ea13f-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ea13f-128">Requirements</span></span>  
 <span data-ttu-id="ea13f-129">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea13f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea13f-130">**Intestazione:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ea13f-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ea13f-131">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ea13f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea13f-132">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea13f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea13f-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea13f-133">See also</span></span>

- [<span data-ttu-id="ea13f-134">Interfacce di hosting</span><span class="sxs-lookup"><span data-stu-id="ea13f-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ea13f-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="ea13f-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
