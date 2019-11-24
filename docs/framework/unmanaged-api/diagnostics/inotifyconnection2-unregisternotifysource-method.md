---
title: Metodo INotifyConnection2::UnregisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: cf399d0c7dec7528f02988ddfe6ca5c0b1f0c4c3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440991"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="e8ef3-102">Metodo INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="e8ef3-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="e8ef3-103">Removes a specified notification source object from the connection.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ef3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8ef3-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8ef3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e8ef3-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="e8ef3-106">[in] Notification object to be unregistered.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8ef3-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e8ef3-107">Return Value</span></span>  
 <span data-ttu-id="e8ef3-108">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ef3-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e8ef3-109">Requirements</span></span>  
 <span data-ttu-id="e8ef3-110">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e8ef3-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ef3-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8ef3-111">See also</span></span>

- [<span data-ttu-id="e8ef3-112">Interfaccia INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="e8ef3-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="e8ef3-113">Interfaccia INotifySource2</span><span class="sxs-lookup"><span data-stu-id="e8ef3-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="e8ef3-114">Interfaccia INotifySink2</span><span class="sxs-lookup"><span data-stu-id="e8ef3-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="e8ef3-115">Metodo RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="e8ef3-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
