---
title: Metodo ICorProfilerInfo4::GetCodeInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912707"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>Metodo ICorProfilerInfo4::GetCodeInfo3
Ottiene gli ambiti di codice nativo associati alla versione ricompilata in JIT della funzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `functionID`  
 [in] ID della funzione alla quale è associato il codice nativo.  
  
 `reJitId`  
 [in] Identità della funzione ricompilata in JIT.  
  
 `cCodeInfos`  
 [in] Dimensione della matrice `codeInfos`.  
  
 `pcCodeInfos`  
 out Puntatore al numero totale di strutture [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponibili.  
  
 `codeInfos`  
 [out] Buffer fornito dal chiamante. Una volta completato, il metodo contiene una matrice di strutture `COR_PRF_CODE_INFO`, ognuna delle quali descrive un blocco di codice nativo.  
  
## <a name="remarks"></a>Note  
 Il `GetCodeInfo3` metodo è simile a [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), ad eccezione del fatto che otterrà l'ID ricompilata in JIT della funzione che contiene l'indirizzo IP specificato.  
  
> [!NOTE]
> `GetCodeInfo3`può attivare una Garbage Collection, mentre [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) non lo è. Per ulteriori informazioni, vedere HRESULT [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) .  
  
 Gli ambiti vengono ordinati in sequenza crescente in base all'offset CIL (Common Intermediate Language).  
  
 Dopo `GetCodeInfo3` la restituzione di, è necessario `codeInfos` verificare che il buffer sia abbastanza grande per contenere tutte le strutture [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . A tale scopo, confrontare il valore di `cCodeInfos` con il valore del parametro `cchName`. Se `cCodeInfos` diviso per la dimensione di una struttura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) è inferiore a `pcCodeInfos`, allocare un `codeInfos` buffer più grande, aggiornare `cCodeInfos` con la nuova dimensione maggiore e chiamare `GetCodeInfo3` di nuovo.  
  
 In alternativa, è possibile chiamare innanzitutto `GetCodeInfo3` con un buffer `codeInfos` di lunghezza zero per ottenere le dimensioni del buffer corrette. È quindi possibile impostare le `codeInfos` dimensioni del buffer sul valore restituito in `pcCodeInfos`, moltiplicato per la dimensione di una struttura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) e chiamare `GetCodeInfo3` di nuovo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf. idl, CorProf. h  
  
 **Libreria** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [Interfaccia ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfacce di profilatura](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilatura](../../../../docs/framework/unmanaged-api/profiling/index.md)
