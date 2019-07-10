---
title: Funzione CreateAssemblyEnum
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778450"
---
# <a name="createassemblyenum-function"></a>Funzione CreateAssemblyEnum
Ottiene un puntatore a un [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) istanza che può enumerare gli oggetti nell'assembly con l'oggetto specificato [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametri  
 `pEnum`  
 [out] Puntatore a una posizione di memoria che contiene l'oggetto richiesto `IAssemblyEnum` puntatore.  
  
 `pUnkReserved`  
 [in] Riservato per un'estendibilità futura. `pUnkReserved` deve essere un riferimento null.  
  
 `pName`  
 [in] Il `IAssemblyName` dell'assembly richiesto. Questo nome viene usato per filtrare l'enumerazione. Può essere null per enumerare tutti gli assembly nella global assembly cache.  
  
 `dwFlags`  
 [in] Flag per la modifica del comportamento dell'enumeratore. Questo parametro contiene esattamente un bit di [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumerazione.  
  
 `pvReserved`  
 [in] Riservato per un'estendibilità futura. `pvReserved` deve essere un riferimento null.  
  
## <a name="remarks"></a>Note  
 Il `dwFlags` parametro contiene esattamente un bit di `ASM_CACHE_FLAGS` enumerazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Fusion. h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [Interfaccia IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Funzioni statiche globali Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
