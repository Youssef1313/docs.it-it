---
title: Metodo ISymUnmanagedReader::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 458faedea418e626a6494ca2afcdbf0e034472e8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447737"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="8451f-102">Metodo ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="8451f-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="8451f-103">Gets the namespaces defined at global scope within this symbol store.</span><span class="sxs-lookup"><span data-stu-id="8451f-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8451f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8451f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8451f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="8451f-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="8451f-106">[in] The size of the namespaces array.</span><span class="sxs-lookup"><span data-stu-id="8451f-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="8451f-107">[out] A pointer to a variable that receives the length of the namespace list.</span><span class="sxs-lookup"><span data-stu-id="8451f-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="8451f-108">[out] A pointer to a variable that receives the namespace list.</span><span class="sxs-lookup"><span data-stu-id="8451f-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8451f-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8451f-109">Return Value</span></span>  
 <span data-ttu-id="8451f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="8451f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8451f-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8451f-111">Requirements</span></span>  
 <span data-ttu-id="8451f-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8451f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8451f-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8451f-113">See also</span></span>

- [<span data-ttu-id="8451f-114">Interfaccia ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="8451f-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
