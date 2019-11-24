---
title: Metodo ISymUnmanagedScope2::GetConstants
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: f7cd45a90a750c357706f720453ff23697875b58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446245"
---
# <a name="isymunmanagedscope2getconstants-method"></a>Metodo ISymUnmanagedScope2::GetConstants
Gets the local constants defined within this scope.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `cConstants`  
 [in] The length of the buffer that the `pcConstants` parameter points to.  
  
 `pcConstants`  
 [out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.  
  
 `constants`  
 [out] The buffer that stores the constants.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Requisiti  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedScope2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
