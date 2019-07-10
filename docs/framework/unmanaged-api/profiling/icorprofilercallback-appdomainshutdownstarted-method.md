---
title: Metodo ICorProfilerCallback::AppDomainShutdownStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9d1cf182eaf6f245baa5d898bac3ca7d3190234
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763088"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="e0915-102">Metodo ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="e0915-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="e0915-103">Notifica al profiler che un dominio dell'applicazione è in corso lo scaricamento da un processo.</span><span class="sxs-lookup"><span data-stu-id="e0915-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0915-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e0915-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0915-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e0915-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e0915-106">[in] Identifica il dominio in cui sono archiviati gli assembly dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e0915-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0915-107">Note</span><span class="sxs-lookup"><span data-stu-id="e0915-107">Remarks</span></span>  
 <span data-ttu-id="e0915-108">Il valore di `appDomainId` non è valida per qualsiasi richiesta di informazioni dopo il `AppDomainShutdownStarted` restituzione del metodo, ovvero si tratta di completamento per ottenere informazioni sul dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="e0915-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0915-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e0915-109">Requirements</span></span>  
 <span data-ttu-id="e0915-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0915-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0915-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0915-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0915-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0915-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0915-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0915-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0915-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0915-114">See also</span></span>

- [<span data-ttu-id="e0915-115">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e0915-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
