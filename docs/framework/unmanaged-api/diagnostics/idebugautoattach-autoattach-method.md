---
title: Metodo IDebugAutoAttach::AutoAttach
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e04a447c8562ff797ac98885bded150a3a167136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775792"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="0bd9e-102">Metodo IDebugAutoAttach::AutoAttach</span><span class="sxs-lookup"><span data-stu-id="0bd9e-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="0bd9e-103">Esegue automaticamente richiamato server debugger collegare.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd9e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0bd9e-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd9e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0bd9e-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="0bd9e-106">[in] Sempre impostato su `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="0bd9e-107">[in] ID processo, in genere recuperato con il `GetCurrentProcessId` (funzione).</span><span class="sxs-lookup"><span data-stu-id="0bd9e-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="0bd9e-108">[in] Tipo di programma: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, o `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="0bd9e-109">[in] ID programma.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="0bd9e-110">[in] Stringa passata per il verbo debug.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bd9e-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0bd9e-111">Return Value</span></span>  
 <span data-ttu-id="0bd9e-112">S_OK se il metodo ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="0bd9e-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd9e-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0bd9e-113">Requirements</span></span>  
 <span data-ttu-id="0bd9e-114">**Intestazione:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="0bd9e-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd9e-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0bd9e-115">See also</span></span>

- [<span data-ttu-id="0bd9e-116">Interfaccia IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="0bd9e-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
