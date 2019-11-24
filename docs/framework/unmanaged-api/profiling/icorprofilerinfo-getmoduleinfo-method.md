---
title: Metodo ICorProfilerInfo::GetModuleInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438899"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="31e03-102">Metodo ICorProfilerInfo::GetModuleInfo</span><span class="sxs-lookup"><span data-stu-id="31e03-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="31e03-103">Dato un ID modulo, restituisce il nome file del modulo e l'ID dell'assembly padre del modulo.</span><span class="sxs-lookup"><span data-stu-id="31e03-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e03-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="31e03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31e03-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="31e03-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="31e03-106">[in] ID del modulo per cui verranno recuperate informazioni.</span><span class="sxs-lookup"><span data-stu-id="31e03-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="31e03-107">[out] Indirizzo di base in cui viene caricato il modulo.</span><span class="sxs-lookup"><span data-stu-id="31e03-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="31e03-108">[in] Lunghezza, espressa in caratteri, del buffer restituito `szName`.</span><span class="sxs-lookup"><span data-stu-id="31e03-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="31e03-109">[out] Puntatore alla lunghezza totale in caratteri del nome file del modulo che viene restituito.</span><span class="sxs-lookup"><span data-stu-id="31e03-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="31e03-110">[out] Buffer per caratteri di tipo "wide" fornito dal chiamante.</span><span class="sxs-lookup"><span data-stu-id="31e03-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="31e03-111">Quando il metodo viene completato, questo buffer contiene il nome file del modulo.</span><span class="sxs-lookup"><span data-stu-id="31e03-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="31e03-112">[out] Puntatore all'ID dell'assembly padre del modulo.</span><span class="sxs-lookup"><span data-stu-id="31e03-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31e03-113">Note</span><span class="sxs-lookup"><span data-stu-id="31e03-113">Remarks</span></span>  
 <span data-ttu-id="31e03-114">Per i moduli dinamici, il parametro `szName` è una stringa vuota e l'indirizzo di base è 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="31e03-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="31e03-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="31e03-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="31e03-116">Dopo il completamento del metodo `GetModuleInfo`, è necessario verificare che il buffer `szName` sia abbastanza grande per contenere il nome file completo del modulo.</span><span class="sxs-lookup"><span data-stu-id="31e03-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="31e03-117">A tale scopo, confrontare il valore a cui punta `pcchName` con il valore del parametro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="31e03-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="31e03-118">Se `pcchName` punta a un valore maggiore di `cchName`, allocare un buffer `szName` più grande, aggiornare `cchName` con la nuova dimensione e chiamare nuovamente `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="31e03-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="31e03-119">In alternativa, è possibile chiamare innanzitutto `GetModuleInfo` con un buffer `szName` di lunghezza zero per ottenere le dimensioni del buffer corrette.</span><span class="sxs-lookup"><span data-stu-id="31e03-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="31e03-120">È quindi possibile impostare le dimensioni del buffer sul valore restituito nel parametro `pcchName` e chiamare nuovamente `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="31e03-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e03-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="31e03-121">Requirements</span></span>  
 <span data-ttu-id="31e03-122">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e03-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e03-123">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31e03-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31e03-124">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31e03-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31e03-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e03-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e03-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="31e03-126">See also</span></span>

- [<span data-ttu-id="31e03-127">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="31e03-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="31e03-128">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="31e03-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="31e03-129">Profilatura</span><span class="sxs-lookup"><span data-stu-id="31e03-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="31e03-130">Metodo GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="31e03-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
