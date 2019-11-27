---
title: Metodo ISymUnmanagedScope::GetChildren
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c7e9d2fe94c33127d8b105333ad6dac9d6cc5af6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446367"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="6093a-102">Metodo ISymUnmanagedScope::GetChildren</span><span class="sxs-lookup"><span data-stu-id="6093a-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="6093a-103">Ottiene gli elementi figlio di questo ambito.</span><span class="sxs-lookup"><span data-stu-id="6093a-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6093a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6093a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6093a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="6093a-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="6093a-106">in `ULONG32` che indica le dimensioni della matrice di `children`.</span><span class="sxs-lookup"><span data-stu-id="6093a-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="6093a-107">out Puntatore a un `ULONG32` che riceve la dimensione del buffer necessario per contenere gli elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="6093a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="6093a-108">out Matrice di elementi figlio restituita.</span><span class="sxs-lookup"><span data-stu-id="6093a-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6093a-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6093a-109">Return Value</span></span>  
 <span data-ttu-id="6093a-110">S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o un altro codice di errore.</span><span class="sxs-lookup"><span data-stu-id="6093a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6093a-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6093a-111">Requirements</span></span>  
 <span data-ttu-id="6093a-112">**Intestazione:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6093a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6093a-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6093a-113">See also</span></span>

- [<span data-ttu-id="6093a-114">Interfaccia ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="6093a-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="6093a-115">Metodo GetParent</span><span class="sxs-lookup"><span data-stu-id="6093a-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
