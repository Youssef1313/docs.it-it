---
title: Metodo ISymUnmanagedMethod::GetRanges
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5a98d510eee8942a2cad0525b6902e3e4eaa52
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769380"
---
# <a name="isymunmanagedmethodgetranges-method"></a>Metodo ISymUnmanagedMethod::GetRanges
Data una posizione in un documento, restituisce una matrice di coppie di offset iniziale e finale che corrispondono agli intervalli di Microsoft intermediate language (MSIL) che la posizione all'interno del metodo. La matrice è una matrice di interi e ha il formato [inizio, fine, inizio, fine]. Il numero di coppie di intervallo è la lunghezza della matrice divisa per 2.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `document`  
 [in] Il documento per cui è richiesto l'offset.  
  
 `line`  
 [in] Riga del documento corrispondente agli intervalli.  
  
 `column`  
 [in] Colonna del documento corrispondente agli intervalli.  
  
 `cRanges`  
 [in] Dimensione della matrice `ranges`.  
  
 `pcRanges`  
 [out] Un puntatore a un `ULONG32` che riceve le dimensioni del buffer necessaria per contenere gli intervalli.  
  
 `ranges`  
 [out] Puntatore al buffer che riceve gli intervalli.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
