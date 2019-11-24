---
title: Metodo ISymUnmanagedDocument::GetURL
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: 134a89d62a0fc455a9579de1e577103f1fe6abcf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449131"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="3ce46-102">Metodo ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="3ce46-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="3ce46-103">Returns the uniform resource locator (URL) for this document.</span><span class="sxs-lookup"><span data-stu-id="3ce46-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce46-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3ce46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ce46-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3ce46-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="3ce46-106">[in] The size, in characters, of the `szURL` buffer.</span><span class="sxs-lookup"><span data-stu-id="3ce46-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="3ce46-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span><span class="sxs-lookup"><span data-stu-id="3ce46-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="3ce46-108">[out] The buffer containing the URL.</span><span class="sxs-lookup"><span data-stu-id="3ce46-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ce46-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3ce46-109">Return Value</span></span>  
 <span data-ttu-id="3ce46-110">S_OK if the method succeeds; otherwise, an error code.</span><span class="sxs-lookup"><span data-stu-id="3ce46-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce46-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3ce46-111">See also</span></span>

- [<span data-ttu-id="3ce46-112">Interfaccia ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="3ce46-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
