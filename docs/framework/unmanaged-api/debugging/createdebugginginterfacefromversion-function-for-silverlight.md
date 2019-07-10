---
title: Funzione di Silverlight CreateDebuggingInterfaceFromVersion
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968956b513e1ae80a25f5fb4afea48bf888876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739260"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Funzione di Silverlight CreateDebuggingInterfaceFromVersion
Common language runtime (CLR) versione stringa che viene restituita da accetta il [funzione CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)e restituisce un'interfaccia del debugger corrispondente (in genere [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `szDebuggeeVersion`  
 [in] Stringa di versione di CLR nell'oggetto del debug di destinazione, che viene restituito per il [funzione CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Puntatore a un puntatore a un oggetto COM (`IUnknown`). Questo oggetto sarà possibile eseguire il cast a un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) dell'oggetto prima che venga restituito.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK  
 `ppCordb` fa riferimento a un oggetto valido che implementa il [interfaccia ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfaccia.  
  
 E_INVALIDARG  
 `szDebuggeeVersion` o `ppCordb` è null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Impossibile trovare un componente necessario per il debug CLR. Ciò significa che non è stato possibile trovare mscordaccore.dll o mscordbi.dll nella stessa directory del file CoreCLR.dll di destinazione.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Significa che la versione di mscordaccore.dll o mscordbi.dll non corrisponde a quella del file CoreCLR.dll di destinazione.  
  
 E_FAIL (o altri codici E_ restituiti)  
 Non è possibile restituire un [interfaccia ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Note  
 L'interfaccia restituita fornisce funzionalità per connettersi a un CLR nel processo di destinazione ed eseguire il debug del codice gestito eseguito da CLR.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** dbgshim. h  
  
 **Libreria:** dbgshim. dll  
  
 **Versioni di .NET framework:** 3.5 SP1
