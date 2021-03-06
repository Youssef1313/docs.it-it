---
title: Metodo ISymUnmanagedWriter::DefineDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: 02b270677131d0960db67b0ac8db38cba2b5e2df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428051"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>Metodo ISymUnmanagedWriter::DefineDocument
Definisce un documento di origine. I GUID sono forniti per i linguaggi noti, i fornitori e i tipi di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametri  
 `url`  
 in Puntatore a un `WCHAR` che definisce l'URL (Uniform Resource Locator) che identifica il documento.  
  
 `language`  
 in Puntatore a un GUID che definisce la lingua del documento.  
  
 `languageVendor`  
 in Puntatore a un GUID che definisce l'identità del fornitore per la lingua del documento.  
  
 `documentType`  
 in Puntatore a un GUID che definisce il tipo del documento.  
  
 `pRetVal`  
 out Puntatore all'interfaccia [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) restituita.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o un altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
