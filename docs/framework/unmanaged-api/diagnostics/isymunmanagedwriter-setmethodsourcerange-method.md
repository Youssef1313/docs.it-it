---
title: Metodo ISymUnmanagedWriter::SetMethodSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e06695f5ba348315523c7414822ce87d594bdbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776598"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>Metodo ISymUnmanagedWriter::SetMethodSourceRange
Specifica l'inizio e fine di un metodo all'interno di un file di origine. Utilizzare questo metodo per specificare l'estensione di un metodo indipendentemente dal punti di sequenza che esiste all'interno del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Parametri  
 `startDoc`  
 [in] Puntatore al documento che contiene la posizione iniziale.  
  
 `startLine`  
 [in] Il numero di riga iniziale.  
  
 `startColumn`  
 [in] La colonna iniziale.  
  
 `endDoc`  
 [in] Puntatore al documento contenente la posizione finale.  
  
 `endLine`  
 [in] Numero di riga finale.  
  
 `endColumn`  
 [in] Numero della colonna finale.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
