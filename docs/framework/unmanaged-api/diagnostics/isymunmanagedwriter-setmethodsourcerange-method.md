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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e06695f5ba348315523c7414822ce87d594bdbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776598"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="7f95c-102">Metodo ISymUnmanagedWriter::SetMethodSourceRange</span><span class="sxs-lookup"><span data-stu-id="7f95c-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="7f95c-103">Specifica l'inizio e fine di un metodo all'interno di un file di origine.</span><span class="sxs-lookup"><span data-stu-id="7f95c-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="7f95c-104">Utilizzare questo metodo per specificare l'estensione di un metodo indipendentemente dal punti di sequenza che esiste all'interno del metodo.</span><span class="sxs-lookup"><span data-stu-id="7f95c-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f95c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7f95c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f95c-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="7f95c-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="7f95c-107">[in] Puntatore al documento che contiene la posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="7f95c-108">[in] Il numero di riga iniziale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="7f95c-109">[in] La colonna iniziale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="7f95c-110">[in] Puntatore al documento contenente la posizione finale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="7f95c-111">[in] Numero di riga finale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="7f95c-112">[in] Numero della colonna finale.</span><span class="sxs-lookup"><span data-stu-id="7f95c-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f95c-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="7f95c-113">Return Value</span></span>  
 <span data-ttu-id="7f95c-114">S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o qualche altro codice di errore.</span><span class="sxs-lookup"><span data-stu-id="7f95c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f95c-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7f95c-115">Requirements</span></span>  
 <span data-ttu-id="7f95c-116">**Intestazione:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f95c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f95c-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7f95c-117">See also</span></span>

- [<span data-ttu-id="7f95c-118">Interfaccia ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="7f95c-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
