---
title: Metodo ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e00e7f39bc2f8c14db0676102a52089c7710bd6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772259"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>Metodo ICorProfilerInfo::IsArrayClass
Determina se la classe specificata è una classe di matrici.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parametri  
 `classId`  
 [in] L'ID della classe da esaminare.  
  
 `pBaseElemType`  
 [out] Puntatore a un valore dell'enumerazione CorElementType che indica il tipo degli elementi della matrice.  
  
 `pBaseClassId`  
 [out] Un puntatore all'ID di classe degli elementi della matrice, se disponibile.  
  
 `pcRank`  
 [out] Puntatore a un intero che indica il numero di dimensioni (vale a dire, numero di dimensioni) della matrice.  
  
## <a name="remarks"></a>Note  
 Se la classe specificata è una classe di matrici, il `IsArrayClass` metodo viene restituito un HRESULT S_OK e i valori per parametri di output diverso da null. In caso contrario, restituisce S_FALSE.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
