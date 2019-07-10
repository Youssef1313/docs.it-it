---
title: Metodo ICorProfilerCallback::AppDomainCreationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 910f8b7f78b6348ace9036d35c0844f2a64cf433
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763151"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="882d4-102">Metodo ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="882d4-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="882d4-103">Notifica al profiler che un dominio dell'applicazione sia stato creato.</span><span class="sxs-lookup"><span data-stu-id="882d4-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882d4-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="882d4-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="882d4-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="882d4-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="882d4-106">[in] Identifica il dominio di cui è stato creato.</span><span class="sxs-lookup"><span data-stu-id="882d4-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="882d4-107">[in] HRESULT che indica se la creazione del dominio dell'applicazione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="882d4-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="882d4-108">Note</span><span class="sxs-lookup"><span data-stu-id="882d4-108">Remarks</span></span>  
 <span data-ttu-id="882d4-109">L'ID dell'applicazione non è valido per qualsiasi richiesta di informazioni finché il `AppDomainCreationFinished` viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="882d4-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="882d4-110">Alcune parti del caricamento del dominio dell'applicazione potrebbero continuare dopo il `AppDomainCreationFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="882d4-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="882d4-111">Un HRESULT di errore in `hrStatus` indica un errore.</span><span class="sxs-lookup"><span data-stu-id="882d4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="882d4-112">Tuttavia, un HRESULT di esito positivo in `hrStatus` indica solo che la prima parte della creazione del dominio applicazione ha avuto esito positivo.</span><span class="sxs-lookup"><span data-stu-id="882d4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="882d4-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="882d4-113">Requirements</span></span>  
 <span data-ttu-id="882d4-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="882d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="882d4-115">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="882d4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="882d4-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="882d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="882d4-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="882d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882d4-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="882d4-118">See also</span></span>

- [<span data-ttu-id="882d4-119">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="882d4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
