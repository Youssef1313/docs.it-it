---
title: Metodo IDebuggerInfo::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133173"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="d467c-102">Metodo IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="d467c-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d467c-103">Ottiene un valore che indica se un debugger gestito è associato a questo processo.</span><span class="sxs-lookup"><span data-stu-id="d467c-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d467c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d467c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d467c-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d467c-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d467c-106">out Puntatore a un valore `true` se al processo è associato un debugger gestito; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="d467c-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d467c-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d467c-107">Requirements</span></span>  
 <span data-ttu-id="d467c-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d467c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d467c-109">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d467c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d467c-110">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d467c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d467c-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d467c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d467c-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d467c-112">See also</span></span>

- [<span data-ttu-id="d467c-113">Interfaccia IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="d467c-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
