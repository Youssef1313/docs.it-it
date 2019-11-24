---
title: Metodo ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433218"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="765fc-102">Metodo ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="765fc-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="765fc-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span><span class="sxs-lookup"><span data-stu-id="765fc-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765fc-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="765fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="765fc-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="765fc-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="765fc-106">[in] The ID of the module in which the function resides.</span><span class="sxs-lookup"><span data-stu-id="765fc-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="765fc-107">[in] An `mdMethodDef` metadata token that references the function.</span><span class="sxs-lookup"><span data-stu-id="765fc-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="765fc-108">[in] The ID of the function's containing class.</span><span class="sxs-lookup"><span data-stu-id="765fc-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="765fc-109">[in] The number of type parameters for the given function.</span><span class="sxs-lookup"><span data-stu-id="765fc-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="765fc-110">This value must be zero for non-generic functions.</span><span class="sxs-lookup"><span data-stu-id="765fc-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="765fc-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span><span class="sxs-lookup"><span data-stu-id="765fc-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="765fc-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="765fc-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="765fc-113">[out] A pointer to the `FunctionID` of the specified function.</span><span class="sxs-lookup"><span data-stu-id="765fc-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="765fc-114">Note</span><span class="sxs-lookup"><span data-stu-id="765fc-114">Remarks</span></span>  
 <span data-ttu-id="765fc-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span><span class="sxs-lookup"><span data-stu-id="765fc-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="765fc-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span><span class="sxs-lookup"><span data-stu-id="765fc-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="765fc-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span><span class="sxs-lookup"><span data-stu-id="765fc-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="765fc-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span><span class="sxs-lookup"><span data-stu-id="765fc-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="765fc-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span><span class="sxs-lookup"><span data-stu-id="765fc-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="765fc-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span><span class="sxs-lookup"><span data-stu-id="765fc-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="765fc-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="765fc-121">Requirements</span></span>  
 <span data-ttu-id="765fc-122">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="765fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="765fc-123">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="765fc-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="765fc-124">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="765fc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="765fc-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="765fc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="765fc-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="765fc-126">See also</span></span>

- [<span data-ttu-id="765fc-127">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="765fc-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="765fc-128">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="765fc-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
