---
title: Metodo ICorProfilerInfo2::GetStaticFieldInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36cb8d5865cdc4c1c8e34671010ede25d531bacf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782260"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="6df14-102">Metodo ICorProfilerInfo2::GetStaticFieldInfo</span><span class="sxs-lookup"><span data-stu-id="6df14-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="6df14-103">Ottiene un valore che indica il tipo di statico che si applica al campo specificato.</span><span class="sxs-lookup"><span data-stu-id="6df14-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df14-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6df14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df14-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="6df14-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="6df14-106">[in] L'ID della classe in cui è definito il campo statico.</span><span class="sxs-lookup"><span data-stu-id="6df14-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="6df14-107">[in] Il token di metadati per il campo statico.</span><span class="sxs-lookup"><span data-stu-id="6df14-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="6df14-108">[out] Un puntatore a un valore di [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumerazione che indica se il campo specificato è statico e, se così, il tipo di statico che viene applicato al campo.</span><span class="sxs-lookup"><span data-stu-id="6df14-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df14-109">Note</span><span class="sxs-lookup"><span data-stu-id="6df14-109">Remarks</span></span>  
 <span data-ttu-id="6df14-110">Queste informazioni sono utilizzabile per determinare quale funzione da chiamare per ottenere l'indirizzo del campo statico.</span><span class="sxs-lookup"><span data-stu-id="6df14-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="6df14-111">Il codice del profiler deve comunque in grado di verificare i metadati per un campo statico per verificare che possa effettivamente un indirizzo.</span><span class="sxs-lookup"><span data-stu-id="6df14-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="6df14-112">Valori letterali statici (vale a dire, costanti) esistono solo nei metadati e non è un indirizzo.</span><span class="sxs-lookup"><span data-stu-id="6df14-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df14-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6df14-113">Requirements</span></span>  
 <span data-ttu-id="6df14-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df14-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df14-115">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6df14-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6df14-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6df14-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df14-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df14-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df14-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6df14-118">See also</span></span>

- [<span data-ttu-id="6df14-119">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="6df14-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="6df14-120">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="6df14-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
