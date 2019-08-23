---
title: Enumerazione STARTUP_FLAGS
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f39608b39be7d5c25b916fb20877aa73d6e5a8bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916229"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="4aea8-102">Enumerazione STARTUP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4aea8-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="4aea8-103">Contiene valori che indicano il comportamento di avvio del Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4aea8-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="4aea8-104">Per impostazione predefinita, Garbage Collection non è simultanea e solo la libreria di classi di base viene caricata nell'area indipendente dal dominio.</span><span class="sxs-lookup"><span data-stu-id="4aea8-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aea8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4aea8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4aea8-106">Members</span><span class="sxs-lookup"><span data-stu-id="4aea8-106">Members</span></span>  
  
|<span data-ttu-id="4aea8-107">Member</span><span class="sxs-lookup"><span data-stu-id="4aea8-107">Member</span></span>|<span data-ttu-id="4aea8-108">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="4aea8-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="4aea8-109">Specifica che deve essere utilizzata la Garbage Collection simultanea.</span><span class="sxs-lookup"><span data-stu-id="4aea8-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="4aea8-110">Se il chiamante richiede la compilazione del server e la Garbage Collection simultanea in un computer a processore singolo, vengono eseguite invece le Garbage Collection di compilazione e non simultanee della workstation.</span><span class="sxs-lookup"><span data-stu-id="4aea8-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="4aea8-111">**Nota:**  La Garbage Collection simultanea non è supportata nelle applicazioni che eseguono l'emulatore WOW64 x86 nei sistemi a 64 bit che implementano l'architettura Intel Itanium (denominata in precedenza IA-64).</span><span class="sxs-lookup"><span data-stu-id="4aea8-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="4aea8-112">Per ulteriori informazioni sull'utilizzo di WOW64 in sistemi Windows a 64 bit, vedere [esecuzione di applicazioni a 32 bit](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="4aea8-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="4aea8-113">Specifica che deve essere eseguita l'ottimizzazione del caricatore.</span><span class="sxs-lookup"><span data-stu-id="4aea8-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="4aea8-114">Specifica che nessun assembly viene caricato come indipendente dal dominio.</span><span class="sxs-lookup"><span data-stu-id="4aea8-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="4aea8-115">Specifica che tutti gli assembly vengono caricati come indipendenti dal dominio.</span><span class="sxs-lookup"><span data-stu-id="4aea8-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="4aea8-116">Specifica che tutti gli assembly con nome sicuro vengono caricati come indipendenti dal dominio.</span><span class="sxs-lookup"><span data-stu-id="4aea8-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="4aea8-117">Specifica che i criteri della versione CLR non verranno applicati alla versione passata.</span><span class="sxs-lookup"><span data-stu-id="4aea8-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="4aea8-118">Verrà caricata la versione esatta specificata di CLR.</span><span class="sxs-lookup"><span data-stu-id="4aea8-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="4aea8-119">Lo shim non valuta i criteri per determinare la versione compatibile più recente.</span><span class="sxs-lookup"><span data-stu-id="4aea8-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="4aea8-120">Specifica che verrà impostato il runtime preferito, ma non effettivamente avviato.</span><span class="sxs-lookup"><span data-stu-id="4aea8-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="4aea8-121">Specifica che verrà utilizzato il server Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="4aea8-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="4aea8-122">Specifica che Garbage Collection manterrà l'indirizzo virtuale usato.</span><span class="sxs-lookup"><span data-stu-id="4aea8-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="4aea8-123">Specifica che la combinazione di un'interfaccia di hosting non sarà consentita.</span><span class="sxs-lookup"><span data-stu-id="4aea8-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="4aea8-124">Specifica che la rappresentazione non deve fluire tra i punti asincroni per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4aea8-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="4aea8-125">Specifica che non deve essere eseguito il commit dello stack di thread completo all'avvio dell'esecuzione del thread.</span><span class="sxs-lookup"><span data-stu-id="4aea8-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="4aea8-126">Specifica che le rappresentazioni gestite e le rappresentazioni realizzate tramite platform invoke propagano tra punti asincroni.</span><span class="sxs-lookup"><span data-stu-id="4aea8-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="4aea8-127">Per impostazione predefinita, solo le rappresentazioni gestite si propagano tra punti asincroni.</span><span class="sxs-lookup"><span data-stu-id="4aea8-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="4aea8-128">Specifica che Garbage Collection utilizzerà uno spazio meno vincolato quando la memoria di sistema è insufficiente.</span><span class="sxs-lookup"><span data-stu-id="4aea8-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="4aea8-129">Vedere `gcTrimCommitOnLowMemory` in [ottimizzazione per l'hosting Web condiviso](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="4aea8-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="4aea8-130">Specifica che traccia eventi per Windows (ETW) è abilitato per gli eventi Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4aea8-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="4aea8-131">A partire da Windows Vista, la traccia eventi è sempre abilitata, quindi questo flag non ha alcun effetto.</span><span class="sxs-lookup"><span data-stu-id="4aea8-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="4aea8-132">Vedere [controllo .NET Framework registrazione](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="4aea8-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="4aea8-133">Specifica che il monitoraggio delle risorse del dominio applicazione è abilitato.</span><span class="sxs-lookup"><span data-stu-id="4aea8-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="4aea8-134">Vedere l' <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> elemento Property e [ \<appDomainResourceMonitoring >](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="4aea8-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4aea8-135">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4aea8-135">Requirements</span></span>  
 <span data-ttu-id="4aea8-136">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aea8-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aea8-137">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4aea8-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4aea8-138">**Libreria** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4aea8-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aea8-139">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aea8-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aea8-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4aea8-140">See also</span></span>

- [<span data-ttu-id="4aea8-141">Enumerazioni di hosting</span><span class="sxs-lookup"><span data-stu-id="4aea8-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
