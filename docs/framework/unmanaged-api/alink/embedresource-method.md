---
title: Metodo EmbedResource
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446542"
---
# <a name="embedresource-method"></a>Metodo EmbedResource
Dichiara una risorsa incorporata. Questo metodo non incorpora effettivamente la risorsa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametri  
 `AssemblyID`  
 ID dell'assembly.  
  
 `FileToken`  
 Token file o ID assembly del file che contiene la risorsa.  
  
 `pszResourceName`  
 Nome della risorsa.  
  
 `dwOffset`  
 Offset della risorsa da RVA.  
  
 `dwFlags`  
 Flag di accessibilità, ad esempio `mrPublic` e `mrPrivate`. Questi flag possono essere passati al [Metodo DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce S_OK se il metodo ha esito positivo.  
  
## <a name="requirements"></a>Requisiti  
 Richiede ALink. h.  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IALink](ialink-interface.md)
- [Interfaccia IALink2](ialink2-interface.md)
- [Alink (API)](index.md)
