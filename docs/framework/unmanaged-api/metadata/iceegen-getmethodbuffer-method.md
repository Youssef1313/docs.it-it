---
title: Metodo ICeeGen::GetMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 8c8ecab9d957e72bb6c0817af07c863fcff97cde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436332"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="3a704-102">Metodo ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="3a704-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="3a704-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="3a704-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="3a704-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="3a704-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a704-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3a704-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a704-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3a704-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="3a704-107">[in] The relative virtual address of the method for which to return a buffer.</span><span class="sxs-lookup"><span data-stu-id="3a704-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="3a704-108">[out] A pointer to the returned buffer.</span><span class="sxs-lookup"><span data-stu-id="3a704-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a704-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3a704-109">Requirements</span></span>  
 <span data-ttu-id="3a704-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a704-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a704-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a704-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a704-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a704-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a704-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a704-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a704-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3a704-114">See also</span></span>

- [<span data-ttu-id="3a704-115">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="3a704-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
