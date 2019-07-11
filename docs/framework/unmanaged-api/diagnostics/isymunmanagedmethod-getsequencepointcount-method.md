---
title: Metodo ISymUnmanagedMethod::GetSequencePointCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22c45ff77c030dcbe87e5aa53284b2cace9849ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759474"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="3b516-102">Metodo ISymUnmanagedMethod::GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="3b516-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="3b516-103">Ottiene il conteggio dei punti di sequenza all'interno di questo metodo.</span><span class="sxs-lookup"><span data-stu-id="3b516-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b516-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3b516-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b516-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3b516-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3b516-106">[out] Un puntatore a un `ULONG32` che riceve le dimensioni del buffer necessaria per contenere i punti di sequenza.</span><span class="sxs-lookup"><span data-stu-id="3b516-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b516-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3b516-107">Return Value</span></span>  
 <span data-ttu-id="3b516-108">S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.</span><span class="sxs-lookup"><span data-stu-id="3b516-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b516-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3b516-109">Requirements</span></span>  
 <span data-ttu-id="3b516-110">**Intestazione:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3b516-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b516-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b516-111">See also</span></span>

- [<span data-ttu-id="3b516-112">Interfaccia ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="3b516-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
