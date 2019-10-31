---
title: Metodo IGCThreadControl::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134743"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="cc228-102">Metodo IGCThreadControl::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="cc228-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="cc228-103">Notifica all'host che il thread che sta effettuando la chiamata sta per essere bloccato, ad esempio per un Garbage Collection o un'altra sospensione.</span><span class="sxs-lookup"><span data-stu-id="cc228-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc228-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cc228-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc228-105">Note</span><span class="sxs-lookup"><span data-stu-id="cc228-105">Remarks</span></span>  
 <span data-ttu-id="cc228-106">L'host può scegliere all'interno del callback `ThreadIsBlockingForSuspension` se ripianificare un thread.</span><span class="sxs-lookup"><span data-stu-id="cc228-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc228-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cc228-107">Requirements</span></span>  
 <span data-ttu-id="cc228-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc228-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc228-109">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc228-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc228-110">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc228-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc228-111">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc228-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc228-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cc228-112">See also</span></span>

- [<span data-ttu-id="cc228-113">Interfaccia IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="cc228-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
