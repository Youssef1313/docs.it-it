---
title: Funzione CoInitializeCor
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b2b7b89c73b59f4f735369659daabb6a8f88300
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779090"
---
# <a name="coinitializecor-function"></a>Funzione CoInitializeCor
`CoInitializeCor` è obsoleto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a>Note  
 Per inizializzare common language runtime, usare [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) oppure [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** Cor. h  
  
## <a name="see-also"></a>Vedere anche

- [Funzioni statiche globali dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
