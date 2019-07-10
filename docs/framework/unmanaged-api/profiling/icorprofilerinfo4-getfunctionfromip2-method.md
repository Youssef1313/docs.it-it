---
title: Metodo ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7281f1aa0da417eba618b748ac68ba1fefb4907d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780848"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>Metodo ICorProfilerInfo4::GetFunctionFromIP2
Un puntatore all'istruzione di codice gestito viene eseguito il mapping alla versione ricompilata in JIT della funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametri  
 `ip`  
 [in] Il puntatore dell'istruzione nel codice gestito.  
  
 `pFunctionId`  
 [out] L'ID di funzione.  
  
 `pReJitId`  
 [out] L'identità della versione ricompilata in JIT della funzione.  
  
## <a name="remarks"></a>Note  
 `GetFunctionFromIP2` è simile a `GetFunctionFromIP`, ad eccezione del fatto che ottiene l'ID ricompilata in JIT anziché l'ID di funzione della funzione che contiene l'indirizzo IP specificato.  
  
> [!NOTE]
>  `GetFunctionFromIP2` può attivare una garbage collection, mentre `GetFunctionFromIP` No.  Per altre informazioni, vedere [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
