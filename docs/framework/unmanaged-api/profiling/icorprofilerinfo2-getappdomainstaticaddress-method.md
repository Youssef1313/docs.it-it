---
title: Metodo ICorProfilerInfo2::GetAppDomainStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 12c9b30dc72d1ccf7bfa79ca0745ba3f2c2290c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435883"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>Metodo ICorProfilerInfo2::GetAppDomainStaticAddress
Gets the address of the specified application domain-static field that is in the scope of the specified application domain.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametri  
 `classId`  
 [in] The class ID of the class that contains the requested application domain-static field.  
  
 `fieldToken`  
 [in] The metadata token for the requested application domain-static field.  
  
 `appDomainId`  
 [in] The ID of the application domain that is the scope for the requested static field.  
  
 `ppAddress`  
 [out] A pointer to the address of the static field that is within the specified application domain.  
  
## <a name="remarks"></a>Note  
 The `GetAppDomainStaticAddress` method may return one of the following:  
  
- A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.  
  
- The addresses of objects that may be in the garbage collection heap. These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.  
  
 Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaccia ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
