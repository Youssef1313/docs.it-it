---
title: Metodo SetAssemblyFile
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445599"
---
# <a name="setassemblyfile-method"></a>Metodo SetAssemblyFile
Assigns the name of the assembly to be built. Not for use when producing unbound modules.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametri  
 `pszFilename`  
 Fully qualified name of the manifest file.  
  
 `pEmitter`  
 Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.  
  
 `afFlags`  
 Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Pointer to ID of resulting assembly.  
  
## <a name="return-value"></a>Valore restituito  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisiti  
 Requires alink.h.  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IALink](ialink-interface.md)
- [Interfaccia IALink2](ialink2-interface.md)
- [API ALink](index.md)
