---
title: Metodo ISymUnmanagedWriter::DefineSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f07685351425a4685ac4a0c8e1b8e3c198b14187
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777320"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Metodo ISymUnmanagedWriter::DefineSequencePoints
Definisce un gruppo di punti di sequenza nel metodo corrente. Ogni riga e colonna iniziale definiscono l'inizio di un'istruzione all'interno di un metodo. Ogni riga e colonna finale definiscono la fine di un'istruzione all'interno di un metodo. Le matrici devono essere disposti in ordine crescente di offset. L'offset viene sempre misurata dall'inizio del metodo, in byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `document`  
 [in] L'oggetto documento per cui vengono definiti punti di sequenza.  
  
 `spCount`  
 [in] Oggetto `ULONG32` che indica le dimensioni della ognuno dei `offsets`, `lines`, `columns`, `endLines`, e `endColumns` buffer.  
  
 `offsets`  
 [in] L'offset dei punti di sequenza misurati dall'inizio del metodo.  
  
 `lines`  
 [in] Numeri di riga iniziali dei punti di sequenza.  
  
 `columns`  
 [in] Numeri di colonna iniziali dei punti di sequenza.  
  
 `endLines`  
 [in] Numeri di riga finali dei punti di sequenza. Questo parametro è facoltativo.  
  
 `endColumns`  
 [in] Numeri di colonna finali dei punti di sequenza. Questo parametro è facoltativo.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
