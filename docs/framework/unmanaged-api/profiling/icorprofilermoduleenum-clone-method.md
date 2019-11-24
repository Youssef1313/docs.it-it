---
title: Metodo ICorProfilerModuleEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 395340d497294c89c59216ab5f294070690b74a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444664"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="2f4df-102">Metodo ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="2f4df-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="2f4df-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2f4df-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f4df-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2f4df-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f4df-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="2f4df-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2f4df-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2f4df-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="2f4df-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span><span class="sxs-lookup"><span data-stu-id="2f4df-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="2f4df-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span><span class="sxs-lookup"><span data-stu-id="2f4df-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f4df-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2f4df-109">Requirements</span></span>  
 <span data-ttu-id="2f4df-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f4df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4df-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f4df-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f4df-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f4df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f4df-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4df-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f4df-114">See also</span></span>

- [<span data-ttu-id="2f4df-115">Interfaccia ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="2f4df-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="2f4df-116">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="2f4df-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
