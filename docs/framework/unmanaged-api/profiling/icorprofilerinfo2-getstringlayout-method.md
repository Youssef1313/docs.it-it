---
title: Metodo ICorProfilerInfo2::GetStringLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d4efa7cb3bc98c54be2889855c3b756fdbf2847
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782237"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="af89f-102">Metodo ICorProfilerInfo2::GetStringLayout</span><span class="sxs-lookup"><span data-stu-id="af89f-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="af89f-103">Ottiene informazioni sul layout di un oggetto stringa.</span><span class="sxs-lookup"><span data-stu-id="af89f-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="af89f-104">Questo metodo è deprecato in .NET Framework 4 ed è stato sostituito il [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="af89f-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af89f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="af89f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af89f-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="af89f-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="af89f-107">[out] Un puntatore all'offset della posizione relativa per il `ObjectID` puntatore, che archivia la lunghezza della stringa.</span><span class="sxs-lookup"><span data-stu-id="af89f-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="af89f-108">La lunghezza viene archiviata come un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="af89f-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af89f-109">Questo parametro restituisce la lunghezza della stringa, non la lunghezza del buffer.</span><span class="sxs-lookup"><span data-stu-id="af89f-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="af89f-110">La lunghezza del buffer non è più disponibile.</span><span class="sxs-lookup"><span data-stu-id="af89f-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="af89f-111">[out] Un puntatore all'offset della posizione relativa per il `ObjectID` puntatore, che archivia la lunghezza della stringa stessa.</span><span class="sxs-lookup"><span data-stu-id="af89f-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="af89f-112">La lunghezza viene archiviata come un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="af89f-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="af89f-113">[out] L'offset del buffer relativo a un puntatore di `ObjectID` puntatore, che archivia la stringa di caratteri "wide".</span><span class="sxs-lookup"><span data-stu-id="af89f-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af89f-114">Note</span><span class="sxs-lookup"><span data-stu-id="af89f-114">Remarks</span></span>  
 <span data-ttu-id="af89f-115">Il `GetStringLayout` metodo ottiene gli offset rispetto al `ObjectID` puntatore, delle posizioni in cui sono archiviati i seguenti:</span><span class="sxs-lookup"><span data-stu-id="af89f-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="af89f-116">Lunghezza del buffer della stringa.</span><span class="sxs-lookup"><span data-stu-id="af89f-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="af89f-117">La lunghezza della stringa stessa.</span><span class="sxs-lookup"><span data-stu-id="af89f-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="af89f-118">Buffer che contiene la stringa effettiva di caratteri "wide".</span><span class="sxs-lookup"><span data-stu-id="af89f-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="af89f-119">Le stringhe possono essere con terminazione null.</span><span class="sxs-lookup"><span data-stu-id="af89f-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af89f-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="af89f-120">Requirements</span></span>  
 <span data-ttu-id="af89f-121">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af89f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af89f-122">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af89f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af89f-123">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af89f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af89f-124">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af89f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af89f-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="af89f-125">See also</span></span>

- [<span data-ttu-id="af89f-126">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="af89f-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="af89f-127">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="af89f-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
