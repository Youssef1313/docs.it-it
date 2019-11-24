---
title: Metodo ISymUnmanagedWriter::SetMethodSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427874"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="dda75-102">Metodo ISymUnmanagedWriter::SetMethodSourceRange</span><span class="sxs-lookup"><span data-stu-id="dda75-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="dda75-103">Specifies the true start and end of a method within a source file.</span><span class="sxs-lookup"><span data-stu-id="dda75-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="dda75-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span><span class="sxs-lookup"><span data-stu-id="dda75-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda75-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dda75-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda75-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="dda75-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="dda75-107">[in] A pointer to the document containing the starting position.</span><span class="sxs-lookup"><span data-stu-id="dda75-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="dda75-108">[in] The starting line number.</span><span class="sxs-lookup"><span data-stu-id="dda75-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="dda75-109">[in] The starting column.</span><span class="sxs-lookup"><span data-stu-id="dda75-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="dda75-110">[in] A pointer to the document containing the ending position.</span><span class="sxs-lookup"><span data-stu-id="dda75-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="dda75-111">[in] The ending line number.</span><span class="sxs-lookup"><span data-stu-id="dda75-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="dda75-112">[in] The ending column number.</span><span class="sxs-lookup"><span data-stu-id="dda75-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda75-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="dda75-113">Return Value</span></span>  
 <span data-ttu-id="dda75-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="dda75-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda75-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dda75-115">Requirements</span></span>  
 <span data-ttu-id="dda75-116">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dda75-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda75-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dda75-117">See also</span></span>

- [<span data-ttu-id="dda75-118">Interfaccia ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="dda75-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
