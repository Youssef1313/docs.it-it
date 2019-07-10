---
title: Metodo ISymUnmanagedVariable::GetAddressField1
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a035e8dd7bd880c4ead500eede5e1b095d701f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778066"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="2f3d3-102">Metodo ISymUnmanagedVariable::GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="2f3d3-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="2f3d3-103">Ottiene il primo campo dell'indirizzo di questa variabile.</span><span class="sxs-lookup"><span data-stu-id="2f3d3-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="2f3d3-104">Il significato dipende dal tipo di indirizzo.</span><span class="sxs-lookup"><span data-stu-id="2f3d3-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3d3-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2f3d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f3d3-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="2f3d3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2f3d3-107">[out] Un puntatore a un `ULONG32` che riceve il primo campo dell'indirizzo.</span><span class="sxs-lookup"><span data-stu-id="2f3d3-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f3d3-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2f3d3-108">Return Value</span></span>  
 <span data-ttu-id="2f3d3-109">S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.</span><span class="sxs-lookup"><span data-stu-id="2f3d3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f3d3-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2f3d3-110">Requirements</span></span>  
 <span data-ttu-id="2f3d3-111">**Intestazione:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f3d3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3d3-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f3d3-112">See also</span></span>

- [<span data-ttu-id="2f3d3-113">Interfaccia ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="2f3d3-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="2f3d3-114">Metodo GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="2f3d3-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="2f3d3-115">Metodo GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="2f3d3-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="2f3d3-116">Metodo GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="2f3d3-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
