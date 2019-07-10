---
title: Metodo IInstallReferenceEnum::GetNextInstallReferenceItem
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dd96b10b5ee2880e0f9ee18048ec8ba2ee0b5ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779052"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="67619-102">Metodo IInstallReferenceEnum::GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="67619-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="67619-103">Ottiene un puntatore al successivo [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) contenuto nell'oggetto [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) oggetto.</span><span class="sxs-lookup"><span data-stu-id="67619-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67619-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="67619-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67619-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="67619-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="67619-106">[out] L'oggetto restituito `IInstallReferenceItem` puntatore.</span><span class="sxs-lookup"><span data-stu-id="67619-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="67619-107">[in] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="67619-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="67619-108">`dwFlags` deve essere 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="67619-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="67619-109">[in] Riservato per un'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="67619-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="67619-110">`pvReserved` deve essere un riferimento null.</span><span class="sxs-lookup"><span data-stu-id="67619-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67619-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="67619-111">Requirements</span></span>  
 <span data-ttu-id="67619-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67619-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67619-113">**Intestazione:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="67619-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="67619-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67619-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67619-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67619-115">See also</span></span>

- [<span data-ttu-id="67619-116">Interfaccia IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="67619-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="67619-117">Interfaccia IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="67619-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
