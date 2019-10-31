---
title: Metodo ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 2325e3034dbf00441e587017affa65b80821fbb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128760"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="256ee-102">Metodo ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="256ee-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="256ee-103">[Supportato in .NET Framework 4.5.2 e versioni successive]</span><span class="sxs-lookup"><span data-stu-id="256ee-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="256ee-104">Informa il Common Language Runtime (CLR) di un riferimento a un assembly che il Profiler prevede di aggiungere nel callback [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="256ee-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="256ee-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="256ee-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="256ee-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="256ee-106">Parameters</span></span>  
 <span data-ttu-id="256ee-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="256ee-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="256ee-108">Puntatore a una struttura [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) che fornisce a CLR informazioni su un riferimento a un assembly che deve considerare quando esegue un percorso di chiusura del riferimento all'assembly.</span><span class="sxs-lookup"><span data-stu-id="256ee-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="256ee-109">Note</span><span class="sxs-lookup"><span data-stu-id="256ee-109">Remarks</span></span>  
 <span data-ttu-id="256ee-110">Il profiler chiama questo metodo per ogni assembly di destinazione a cui fa riferimento l'assembly specificato nell'argomento `wszAssemblyPath` del callback [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="256ee-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="256ee-111">L'oggetto interfaccia [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) viene passato al callback [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) del profiler, insieme al percorso e al nome dell'assembly nell'argomento `wszAssemblyPath`.</span><span class="sxs-lookup"><span data-stu-id="256ee-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="256ee-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="256ee-112">Requirements</span></span>  
 <span data-ttu-id="256ee-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="256ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="256ee-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="256ee-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="256ee-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="256ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="256ee-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="256ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256ee-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="256ee-117">See also</span></span>

- [<span data-ttu-id="256ee-118">Interfaccia ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="256ee-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="256ee-119">Metodo GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="256ee-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="256ee-120">Metodo ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="256ee-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
