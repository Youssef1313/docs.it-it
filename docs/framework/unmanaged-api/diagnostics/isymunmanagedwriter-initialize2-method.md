---
title: Metodo ISymUnmanagedWriter::Initialize2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427951"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>Metodo ISymUnmanagedWriter::Initialize2
Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written. This method also lets you set the final location of the program database (PDB) file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametri  
 `emitter`  
 [in] A pointer to the metadata emitter interface.  
  
 `tempfilename`  
 [in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written. Se specificato per un writer che non usa i nomi file, il parametro sarà ignorato.  
  
 `pIStream`  
 [in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter. Il parametro `pIStream` è facoltativo.  
  
 `fFullBuild`  
 [in] `true` if this is a full rebuild; `false` if this is an incremental compilation.  
  
 `finalfilename`  
 [in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisiti  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Metodo Initialize](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
