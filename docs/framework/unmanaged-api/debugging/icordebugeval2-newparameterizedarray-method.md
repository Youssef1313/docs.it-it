---
title: Metodo ICorDebugEval2::NewParameterizedArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973f975885bbbf5cbed74adef7b9f4f423c42583
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753661"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>Metodo ICorDebugEval2::NewParameterizedArray
Consente di allocare una nuova matrice del tipo di elemento specificato e le dimensioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pElementType`  
 [in] Un puntatore a un oggetto ICorDebugType che rappresenta il tipo di elemento memorizzato nella matrice.  
  
 `rank`  
 [in] Il numero di dimensioni della matrice. In .NET Framework versione 2.0, questo valore deve essere 1.  
  
 `dims`  
 [in] Le dimensioni, in byte, di ogni dimensione della matrice.  
  
 `lowBounds`  
 [in] Facoltativo. Il limite inferiore di ogni dimensione della matrice. Se questo valore viene omesso, per ogni dimensione viene utilizzato un limite inferiore pari a zero.  
  
## <a name="remarks"></a>Note  
 Gli elementi della matrice possono essere istanze di un tipo generico. La matrice viene sempre creata nel dominio dell'applicazione in cui è attualmente in esecuzione il thread. In .NET Framework 2.0, il valore di `rank` deve essere 1.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
