---
title: Funzione CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741079"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="051c2-102">Funzione CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="051c2-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="051c2-103">Chiude tutti validi common language runtime (CLR) continuano l'avvio gli eventi che si trova in una matrice di handle restituita dal [funzione EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera la memoria per le matrici del percorso stringa e di handle.</span><span class="sxs-lookup"><span data-stu-id="051c2-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051c2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="051c2-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="051c2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="051c2-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="051c2-106">[in] Puntatore alla matrice di handle dell'evento restituito dal [funzione EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="051c2-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="051c2-107">[in] Puntatore alla matrice di percorsi di stringa CLR restituiti dai [funzione EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="051c2-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="051c2-108">[in] DWORD contenente la dimensione (lunghezza) di `pHandleArray` o `pStringArray` (sono uguali).</span><span class="sxs-lookup"><span data-stu-id="051c2-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="051c2-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="051c2-109">Return Value</span></span>  
 <span data-ttu-id="051c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="051c2-110">S_OK</span></span>  
 <span data-ttu-id="051c2-111">Gli handle aperti per la [funzione EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) vengono chiuse, e viene liberata la memoria allocata per le matrici di tipo stringa e di handle.</span><span class="sxs-lookup"><span data-stu-id="051c2-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="051c2-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="051c2-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="051c2-113">La lunghezza di `pHandleArray` non corrisponde alla lunghezza passata in `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="051c2-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="051c2-114">E_FAIL (o altri codici E_ restituiti)</span><span class="sxs-lookup"><span data-stu-id="051c2-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="051c2-115">La funzione non è in grado di liberare la memoria per `pHandleArray` ed `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="051c2-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051c2-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="051c2-116">Requirements</span></span>  
 <span data-ttu-id="051c2-117">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="051c2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="051c2-118">**Intestazione:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="051c2-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="051c2-119">**Libreria:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="051c2-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="051c2-120">**Versioni di .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="051c2-120">**.NET Framework Versions:** 3.5 SP1</span></span>
