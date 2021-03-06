---
title: Metodo ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: f4f5871bdd7adf11fcc811fd40c62e3027b8e607
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426182"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>Metodo ICorProfilerCallback::ManagedToUnmanagedTransition
Notifica al profiler che è stata eseguita una transizione dal codice gestito al codice non gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametri  
 `functionId`  
 in ID della funzione chiamata.  
  
 `reason`  
 in Valore dell'enumerazione [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) che indica se la transizione è stata eseguita a causa di una chiamata al codice non gestito dal codice gestito o a causa di un ritorno da una funzione gestita chiamata da una funzione non gestita.  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore di `reason` è COR_PRF_TRANSITION_CALL, l'ID funzione è quello della funzione non gestita, che non sarà mai stata compilata con il compilatore just-in-time. Alle funzioni non gestite sono associate informazioni di base, ad esempio un nome e alcuni metadati. Se la funzione non gestita è stata chiamata utilizzando Implicit platform invoke (PInvoke), il runtime non è in grado di determinare la destinazione della chiamata e il valore di `functionId` sarà null. Per ulteriori informazioni su PInvoke implicito, [vedere C++ utilizzo dell'interoperabilità (PInvoke implicito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Metodo UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Uso esplicito di PInvoke in C++ (attributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
