---
title: Metodo ICorProfilerCallback::ExceptionCLRCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cec06cd4c2fdef310126adc2921c858ca5687
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776023"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="45b9a-102">Metodo ICorProfilerCallback::ExceptionCLRCatcherFound</span><span class="sxs-lookup"><span data-stu-id="45b9a-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="45b9a-103">Chiamato quando un `catch` blocca per un'eccezione si trova all'interno di common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="45b9a-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="45b9a-104">Questo metodo è obsoleto in .NET Framework versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="45b9a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b9a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="45b9a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="45b9a-106">Requisiti</span><span class="sxs-lookup"><span data-stu-id="45b9a-106">Requirements</span></span>  
 <span data-ttu-id="45b9a-107">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45b9a-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45b9a-108">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45b9a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45b9a-109">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45b9a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45b9a-110">**Versione di .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="45b9a-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b9a-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45b9a-111">See also</span></span>

- [<span data-ttu-id="45b9a-112">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="45b9a-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="45b9a-113">Metodo ExceptionCLRCatcherExecute</span><span class="sxs-lookup"><span data-stu-id="45b9a-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
