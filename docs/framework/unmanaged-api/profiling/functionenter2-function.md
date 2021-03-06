---
title: Funzione FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440856"
---
# <a name="functionenter2-function"></a>Funzione FunctionEnter2
Notifica al profiler che il controllo viene passato a una funzione e fornisce informazioni sugli stack frame e sugli argomenti della funzione. Questa funzione sostituisce la funzione [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `funcId`  
 in Identificatore della funzione a cui viene passato il controllo.  
  
 `clientData`  
 in Identificatore della funzione di cui è stato eseguito il mapping, specificato in precedenza dal profiler tramite la funzione [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .  
  
 `func`  
 in Valore `COR_PRF_FRAME_INFO` che punta alle informazioni relative al stack frame.  
  
 Il profiler deve considerarlo come un handle opaco che può essere passato di nuovo al motore di esecuzione nel metodo [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
 `argumentInfo`  
 in Puntatore a una struttura [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) che specifica le posizioni in memoria degli argomenti della funzione.  
  
 Per accedere alle informazioni sugli argomenti, è necessario impostare il flag di `COR_PRF_ENABLE_FUNCTION_ARGS`. Il profiler può usare il metodo [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) per impostare i flag di evento.  
  
## <a name="remarks"></a>Osservazioni  
 I valori dei parametri `func` e `argumentInfo` non sono validi dopo che la funzione `FunctionEnter2` restituisce il risultato perché i valori possono essere modificati o eliminati.  
  
 La funzione `FunctionEnter2` è un callback. è necessario implementarla. L'implementazione deve usare l'attributo della classe di archiviazione `__declspec`(`naked`).  
  
 Il motore di esecuzione non salva i registri prima di chiamare questa funzione.  
  
- In ingresso è necessario salvare tutti i registri utilizzati, inclusi quelli nell'unità a virgola mobile (FPU).  
  
- All'uscita è necessario ripristinare lo stack scegliendo tutti i parametri di cui è stato eseguito il push dal chiamante.  
  
 L'implementazione di `FunctionEnter2` non deve bloccarsi perché ritarda Garbage Collection. L'implementazione non deve tentare un Garbage Collection perché lo stack potrebbe non essere in uno stato descrittivo Garbage Collection. Se viene effettuato un tentativo di Garbage Collection, il runtime si bloccherà fino a quando `FunctionEnter2` non restituisce.  
  
 Inoltre, la funzione `FunctionEnter2` non deve chiamare nel codice gestito o in alcun modo causare un'allocazione di managed memory.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf. idl  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Funzione FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [Funzione FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Metodo SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Funzioni statiche globali di profilatura](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
