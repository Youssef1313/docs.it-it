---
title: Metodo ISymUnmanagedConstant::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449262"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="0e535-102">Metodo ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="0e535-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="0e535-103">Gets the signature of the constant.</span><span class="sxs-lookup"><span data-stu-id="0e535-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e535-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0e535-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e535-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0e535-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="0e535-106">[in] The length of the buffer that the `pcSig` parameter points to.</span><span class="sxs-lookup"><span data-stu-id="0e535-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="0e535-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span><span class="sxs-lookup"><span data-stu-id="0e535-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="0e535-108">[out] The buffer that stores the signature.</span><span class="sxs-lookup"><span data-stu-id="0e535-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e535-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0e535-109">Return Value</span></span>  
 <span data-ttu-id="0e535-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="0e535-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e535-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0e535-111">Requirements</span></span>  
 <span data-ttu-id="0e535-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0e535-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e535-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e535-113">See also</span></span>

- [<span data-ttu-id="0e535-114">Interfaccia ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="0e535-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="0e535-115">Metodo GetName</span><span class="sxs-lookup"><span data-stu-id="0e535-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="0e535-116">Metodo GetValue</span><span class="sxs-lookup"><span data-stu-id="0e535-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
