---
title: Metodo ICorProfilerInfo3::GetStringLayout2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765401"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="69f76-102">Metodo ICorProfilerInfo3::GetStringLayout2</span><span class="sxs-lookup"><span data-stu-id="69f76-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="69f76-103">Ottiene informazioni sul layout di un oggetto stringa.</span><span class="sxs-lookup"><span data-stu-id="69f76-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="69f76-104">Questo metodo sostituisce le [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="69f76-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f76-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69f76-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f76-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="69f76-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="69f76-107">[out] Un puntatore all'offset della posizione relativa per il `ObjectID` puntatore, che archivia la lunghezza della stringa stessa.</span><span class="sxs-lookup"><span data-stu-id="69f76-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="69f76-108">La lunghezza viene archiviata come un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="69f76-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="69f76-109">[out] L'offset del buffer relativo a un puntatore di `ObjectID` puntatore, che archivia la stringa di caratteri "wide".</span><span class="sxs-lookup"><span data-stu-id="69f76-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69f76-110">Note</span><span class="sxs-lookup"><span data-stu-id="69f76-110">Remarks</span></span>  
 <span data-ttu-id="69f76-111">Le stringhe possono o potrebbero non essere con terminazione null.</span><span class="sxs-lookup"><span data-stu-id="69f76-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f76-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="69f76-112">Requirements</span></span>  
 <span data-ttu-id="69f76-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f76-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69f76-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69f76-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f76-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69f76-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f76-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69f76-117">See also</span></span>

- [<span data-ttu-id="69f76-118">Interfaccia ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="69f76-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="69f76-119">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="69f76-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
