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
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427992"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Metodo ISymUnmanagedWriter::DefineSequencePoints
Definisce un gruppo di punti di sequenza nel metodo corrente. Each starting line and starting column define the start of a statement within a method. Each ending line and ending column define the end of a statement within a method. The arrays should be sorted in increasing order of offsets. The offset is always measured from the start of the method, in bytes.  
  
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
 [in] The document object for which the sequence points are being defined.  
  
 `spCount`  
 [in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.  
  
 `offsets`  
 [in] The offset of the sequence points measured from the beginning of the method.  
  
 `lines`  
 [in] The starting line numbers of the sequence points.  
  
 `columns`  
 [in] The starting column numbers of the sequence points.  
  
 `endLines`  
 [in] The ending line numbers of the sequence points. Questo parametro è facoltativo.  
  
 `endColumns`  
 [in] The ending column numbers of the sequence points. Questo parametro è facoltativo.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisiti  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
