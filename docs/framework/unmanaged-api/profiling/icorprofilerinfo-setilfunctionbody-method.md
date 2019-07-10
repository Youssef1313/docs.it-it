---
title: Metodo ICorProfilerInfo::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abe0a0fc177c9ec89f4621e7defb5330c911034b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778613"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>Metodo ICorProfilerInfo::SetILFunctionBody
Sostituisce il corpo della funzione specificata nel modulo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametri  
 `moduleId`  
 [in] L'ID del modulo in cui risiede la funzione.  
  
 `methodid`  
 [in] Il token della funzione per cui si desidera sostituire il corpo.  
  
 `pbNewILMethodHeader`  
 [in] La nuova intestazione per la funzione.  
  
## <a name="remarks"></a>Note  
 Il `SetILFunctionBody` metodo sostituisce l'indirizzo virtuale relativo della funzione nei metadati in modo che punti al nuovo corpo della funzione e consente di regolare le strutture di dati interno in base alle esigenze.  
  
 Il `SetILFunctionBody` metodo può essere chiamato solo sulle funzioni che non sono stati compilati mai da un compilatore just-in-time (JIT).  
  
 Usare la [GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metodo per allocare spazio per il nuovo metodo per assicurarsi che il buffer è compatibile.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
