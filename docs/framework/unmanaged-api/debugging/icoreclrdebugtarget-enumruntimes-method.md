---
title: Metodo ICoreClrDebugTarget::EnumRuntimes
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121827"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>Metodo ICoreClrDebugTarget::EnumRuntimes
Enumera i Common Language Runtime (CLR) nel processo specificato in cui è in esecuzione in un computer remoto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parametri  
 `dwInternalProcessID`  
 [in] ID del processo interno per il quale si vogliono enumerare i runtime. Questa operazione verrà `m_dwInternalID` dal [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)corrispondente.  
  
 `pcRuntimes`  
 [out] Numero di runtime restituiti in `ppRuntimes`. Il valore può essere 0 (zero).  
  
 `ppRuntimes`  
 out Matrice di strutture [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) che rappresentano i runtime caricati nel processo di destinazione remoto.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK  
 Operazione completata.  
  
 S_FALSE  
 `dwInternalProcessID` non corrisponde a nessun processo in esecuzione nel computer, probabilmente perché il processo è stato terminato. `pcRuntimes` e `ppRuntimes` saranno null.  
  
 E_OUTOFMEMORY  
 Non è possibile allocare memoria sufficiente per `ppRuntimes`.  
  
 E_FAIL (o altri codici E_ restituiti)  
 Altri errori.  
  
## <a name="remarks"></a>Note  
 Per liberare la memoria allocata da questo metodo, chiamare il metodo [ICoreClrDebugTarget:: FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Libreria:** mscordbi_macx86. dll  
  
 **Versioni .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
