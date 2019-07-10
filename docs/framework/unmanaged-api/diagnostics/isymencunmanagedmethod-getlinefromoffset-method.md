---
title: Metodo ISymENCUnmanagedMethod::GetLineFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b669921bf8d27283ba99f4ca1d97b6abc00e15db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776889"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="0ab4e-102">Metodo ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="0ab4e-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="0ab4e-103">Ottiene le informazioni della riga associate a un offset.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="0ab4e-104">Se il parametro offset (`dwOffset`) non è un punto di sequenza, questo metodo ottiene le informazioni della riga associate all'offset precedente.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab4e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0ab4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab4e-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="0ab4e-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="0ab4e-107">[in] Oggetto `ULONG32` che contiene l'offset.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="0ab4e-108">[out] Un puntatore a un `ULONG32` che riceve la riga.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="0ab4e-109">[out] Un puntatore a un `ULONG32` che riceve la colonna.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="0ab4e-110">[out] Un puntatore a un `ULONG32` che riceve la riga finale.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="0ab4e-111">[out] Un puntatore a un `ULONG32` che riceve la colonna finale.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="0ab4e-112">[out] Un puntatore a un `ULONG32` che riceve il punto di sequenza associata.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ab4e-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0ab4e-113">Return Value</span></span>  
 <span data-ttu-id="0ab4e-114">S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.</span><span class="sxs-lookup"><span data-stu-id="0ab4e-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ab4e-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0ab4e-115">Requirements</span></span>  
 <span data-ttu-id="0ab4e-116">**Intestazione:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0ab4e-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab4e-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ab4e-117">See also</span></span>

- [<span data-ttu-id="0ab4e-118">Interfaccia ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="0ab4e-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
