---
title: Metodo IMetaDataError::OnError
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: f10c55abcc044b5bbdbb940001a25f530a4688e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431229"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="05524-102">Metodo IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="05524-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="05524-103">Provides notification of errors that occur during the metadata merge.</span><span class="sxs-lookup"><span data-stu-id="05524-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05524-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="05524-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05524-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="05524-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="05524-106">[in] The HRESULT error value returned to the calling method.</span><span class="sxs-lookup"><span data-stu-id="05524-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="05524-107">[in] The metadata token of the code object that was being merged when the error occurred.</span><span class="sxs-lookup"><span data-stu-id="05524-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05524-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="05524-108">Requirements</span></span>  
 <span data-ttu-id="05524-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05524-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05524-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05524-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05524-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05524-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05524-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05524-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05524-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="05524-113">See also</span></span>

- [<span data-ttu-id="05524-114">Interfaccia IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="05524-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
