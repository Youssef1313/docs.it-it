---
title: Metodo ISymUnmanagedDocument::GetSourceLength
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: 0551e8b4f381f76e7bbac06ca7b5f6aea5bbb61f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449146"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a>Metodo ISymUnmanagedDocument::GetSourceLength
Recupera la lunghezza, in byte, dell'origine incorporata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] A pointer to a variable that indicates the length, in bytes, of the embedded source.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK if the method succeeds.  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
