---
title: Metodo ISymUnmanagedWriter::RemapToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 9e441d4ff39632d9381e445ee99249d04539ad87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427876"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="1d433-102">Metodo ISymUnmanagedWriter::RemapToken</span><span class="sxs-lookup"><span data-stu-id="1d433-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="1d433-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span><span class="sxs-lookup"><span data-stu-id="1d433-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="1d433-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span><span class="sxs-lookup"><span data-stu-id="1d433-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d433-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1d433-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d433-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="1d433-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="1d433-107">[in] The metadata token that was remapped.</span><span class="sxs-lookup"><span data-stu-id="1d433-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="1d433-108">[in] The new metadata token to which `oldToken` was remapped.</span><span class="sxs-lookup"><span data-stu-id="1d433-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d433-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="1d433-109">Return Value</span></span>  
 <span data-ttu-id="1d433-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="1d433-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d433-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1d433-111">Requirements</span></span>  
 <span data-ttu-id="1d433-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1d433-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d433-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d433-113">See also</span></span>

- [<span data-ttu-id="1d433-114">Interfaccia ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="1d433-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
