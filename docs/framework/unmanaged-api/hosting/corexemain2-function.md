---
title: Funzione _CorExeMain2
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46dab35c44e59a149822005575c83c13e9350455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758541"
---
# <a name="corexemain2-function"></a><span data-ttu-id="64d83-102">Funzione _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="64d83-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="64d83-103">Esegue il punto di ingresso nel codice mappato alla memoria specificato.</span><span class="sxs-lookup"><span data-stu-id="64d83-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="64d83-104">Questa funzione viene chiamata dal caricatore del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="64d83-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d83-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="64d83-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d83-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="64d83-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="64d83-107">[in] Puntatore al codice mappato alla memoria.</span><span class="sxs-lookup"><span data-stu-id="64d83-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="64d83-108">[in] Il numero di elementi `pUnmappedPE` può contenere.</span><span class="sxs-lookup"><span data-stu-id="64d83-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="64d83-109">[in] Un puntatore al nome dell'immagine eseguibile.</span><span class="sxs-lookup"><span data-stu-id="64d83-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="64d83-110">[in] Il nome del file di caricatore.</span><span class="sxs-lookup"><span data-stu-id="64d83-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="64d83-111">[in] Parametri della riga di comando, se presente.</span><span class="sxs-lookup"><span data-stu-id="64d83-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d83-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="64d83-112">Requirements</span></span>  
 <span data-ttu-id="64d83-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d83-114">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64d83-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d83-115">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="64d83-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64d83-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d83-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="64d83-117">See also</span></span>

- [<span data-ttu-id="64d83-118">Funzioni statiche globali dei metadati</span><span class="sxs-lookup"><span data-stu-id="64d83-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
