---
title: Interfaccia ICorPublish
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121773"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="4e0c8-102">Interfaccia ICorPublish</span><span class="sxs-lookup"><span data-stu-id="4e0c8-102">ICorPublish Interface</span></span>
<span data-ttu-id="4e0c8-103">Funge da interfaccia generale per la pubblicazione di informazioni sui processi e sulle informazioni sui domini applicazione in tali processi.</span><span class="sxs-lookup"><span data-stu-id="4e0c8-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e0c8-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="4e0c8-104">Methods</span></span>  
  
|<span data-ttu-id="4e0c8-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="4e0c8-105">Method</span></span>|<span data-ttu-id="4e0c8-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4e0c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e0c8-107">Metodo EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="4e0c8-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="4e0c8-108">Ottiene un'istanza di [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) che contiene i processi gestiti in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="4e0c8-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="4e0c8-109">Metodo GetProcess</span><span class="sxs-lookup"><span data-stu-id="4e0c8-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="4e0c8-110">Ottiene un'istanza di [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) che rappresenta il processo con l'identificatore specificato.</span><span class="sxs-lookup"><span data-stu-id="4e0c8-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e0c8-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4e0c8-111">Requirements</span></span>  
 <span data-ttu-id="4e0c8-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e0c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e0c8-113">**Intestazione:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="4e0c8-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4e0c8-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e0c8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e0c8-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0c8-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4e0c8-116">See also</span></span>

- [<span data-ttu-id="4e0c8-117">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="4e0c8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4e0c8-118">Coclasse CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="4e0c8-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
