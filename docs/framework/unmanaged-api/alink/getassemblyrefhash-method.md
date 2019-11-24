---
title: Metodo GetAssemblyRefHash
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433881"
---
# <a name="getassemblyrefhash-method"></a>Metodo GetAssemblyRefHash
Retrieves a hash blob for a given assembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a>Parametri  
 `FileToken`  
 ID of assembly to which the hash will refer.  
  
 `ppvHash`  
 Receives the resulting hash blob.  
  
 `pcbHash`  
 Receives size, in bytes, of hash blob.  
  
## <a name="return-value"></a>Valore restituito  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisiti  
 Requires alink.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IALink](ialink-interface.md)
- [Interfaccia IALink2](ialink2-interface.md)
- [API ALink](index.md)
