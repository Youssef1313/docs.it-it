---
title: Metodo ISymUnmanagedScope2::GetConstantCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: f795147bdcd822db90106c7f2171eb1771b1126f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446246"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="d574c-102">Metodo ISymUnmanagedScope2::GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="d574c-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="d574c-103">Gets a count of the constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="d574c-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d574c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d574c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d574c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d574c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d574c-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span><span class="sxs-lookup"><span data-stu-id="d574c-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d574c-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d574c-107">Return Value</span></span>  
 <span data-ttu-id="d574c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="d574c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d574c-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d574c-109">Requirements</span></span>  
 <span data-ttu-id="d574c-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d574c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d574c-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d574c-111">See also</span></span>

- [<span data-ttu-id="d574c-112">Interfaccia ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="d574c-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
