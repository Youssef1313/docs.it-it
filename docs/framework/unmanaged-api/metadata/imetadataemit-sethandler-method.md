---
title: Metodo IMetaDataEmit::SetHandler
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d50198cc6156d5bec8b8302a4624b0b7411a9c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751100"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="68662-102">Metodo IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="68662-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="68662-103">Imposta il metodo specificato fa riferimento `IUnknown` puntatore come un callback di notifica per riassegnazioni di token.</span><span class="sxs-lookup"><span data-stu-id="68662-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68662-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="68662-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68662-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="68662-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="68662-106">[in] Il gestore da registrare.</span><span class="sxs-lookup"><span data-stu-id="68662-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68662-107">Note</span><span class="sxs-lookup"><span data-stu-id="68662-107">Remarks</span></span>  
 <span data-ttu-id="68662-108">Il motore di metadati invia notifica tramite il metodo che viene fornito da `SetHandler`, per i compilatori che non generano record in modo ottimizzato e che desiderano ottimizzare registra salvato.</span><span class="sxs-lookup"><span data-stu-id="68662-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="68662-109">Se il metodo di callback non viene fornito attraverso `SetHandler`, verrà eseguita alcuna ottimizzazione nel salvataggio tranne diversi in cui importare gli ambiti sono stati uniti usando `IMapToken` merge per ogni ambito.</span><span class="sxs-lookup"><span data-stu-id="68662-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68662-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="68662-110">Requirements</span></span>  
 <span data-ttu-id="68662-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68662-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68662-112">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="68662-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68662-113">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="68662-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68662-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68662-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68662-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68662-115">See also</span></span>

- [<span data-ttu-id="68662-116">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="68662-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="68662-117">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="68662-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
