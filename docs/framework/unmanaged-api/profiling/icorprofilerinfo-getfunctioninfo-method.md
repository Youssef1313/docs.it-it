---
title: Metodo ICorProfilerInfo::GetFunctionInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 0a3ec1a317fbeba2bf792378663e2fe940a8ec10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439109"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>Metodo ICorProfilerInfo::GetFunctionInfo
Ottiene la classe padre e il token di metadati per la funzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>Parametri  
 `functionId`  
 in ID della funzione per cui ottenere la classe padre e il token di metadati.  
  
 `pClassId`  
 [out] Puntatore alla classe padre della funzione.  
  
 `pModuleId`  
 [out] Puntatore al modulo in cui è definita la classe padre della funzione.  
  
 `pToken`  
 [out] Puntatore al token di metadati per la funzione.  
  
## <a name="remarks"></a>Osservazioni  
 Il codice del profiler può chiamare [ICorProfilerInfo:: GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) per ottenere un'interfaccia di metadati per un determinato modulo. Il token di metadati restituito nella posizione a cui fa riferimento `pToken` può quindi essere usato per accedere ai metadati per la funzione.  
  
 Il `ClassID` di una funzione in una classe generica potrebbe non essere ottenibile senza informazioni contestuali sull'uso della funzione. In questo caso, `pClassId` sarà 0. Il codice del profiler deve usare [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) con un valore COR_PRF_FRAME_INFO per fornire un contesto maggiore.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
