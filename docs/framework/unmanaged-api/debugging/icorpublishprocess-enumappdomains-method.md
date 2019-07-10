---
title: Metodo ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c614afee18824e1672b378dd468cb11c9c173d9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764952"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="4270f-102">Metodo ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="4270f-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="4270f-103">Ottiene un enumeratore per i domini applicazione nel processo di cui viene fatto riferimento da questo [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4270f-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4270f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4270f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4270f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4270f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="4270f-106">[out] Un puntatore all'indirizzo di un [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) istanza che consente l'iterazione nella raccolta di domini applicazione in questo processo.</span><span class="sxs-lookup"><span data-stu-id="4270f-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4270f-107">Note</span><span class="sxs-lookup"><span data-stu-id="4270f-107">Remarks</span></span>  
 <span data-ttu-id="4270f-108">L'elenco di domini applicazione si basa su uno snapshot dei domini applicazione che esiste quando il `EnumAppDomains` viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="4270f-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="4270f-109">Questo metodo può essere chiamato più volte per creare un nuovo elenco aggiornato.</span><span class="sxs-lookup"><span data-stu-id="4270f-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="4270f-110">Elenchi esistenti non essere interessati dalle chiamate successive di questo metodo.</span><span class="sxs-lookup"><span data-stu-id="4270f-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="4270f-111">Se il processo è stato terminato, `EnumAppDomains` avrà esito negativo con un valore HRESULT di CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="4270f-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4270f-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4270f-112">Requirements</span></span>  
 <span data-ttu-id="4270f-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4270f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4270f-114">**Intestazione:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4270f-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4270f-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4270f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4270f-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4270f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4270f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4270f-117">See also</span></span>

- [<span data-ttu-id="4270f-118">Interfaccia ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="4270f-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
