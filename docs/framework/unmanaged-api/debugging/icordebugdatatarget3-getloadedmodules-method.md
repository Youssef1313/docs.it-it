---
title: Metodo ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120b839b2b11c85f42bb1a0ae4701de0dea33879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912828"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>Metodo ICorDebugDataTarget3::GetLoadedModules
Ottiene un elenco dei moduli caricati fino a questo momento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `cRequestedModules`  
 [in] Numero di moduli per i quali sono richieste informazioni.  
  
 `pcFetchedModules`  
 [out] Puntatore al numero di moduli sui quali sono state restituite informazioni.  
  
 `pLoadedModules`  
 out Puntatore a una matrice di oggetti [Metodo icordebugloadedmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) che forniscono informazioni sui moduli caricati.  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
> Questo metodo è disponibile solo con .NET Native.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug. idl, CorDebug. h  
  
 **Libreria** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugDataTarget3](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
