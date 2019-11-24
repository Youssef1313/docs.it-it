---
title: Metodo ICeeGen::GetSectionBlock
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: 0731053fb37c775d25052a5fd99a479a44ff5862
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434871"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="b0090-102">Metodo ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="b0090-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="b0090-103">Gets a section block of the code base.</span><span class="sxs-lookup"><span data-stu-id="b0090-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="b0090-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="b0090-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0090-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b0090-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b0090-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="b0090-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="b0090-107">[in] The section from which to retrieve a block of the code base.</span><span class="sxs-lookup"><span data-stu-id="b0090-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="b0090-108">[in] The length of the block to be retrieved.</span><span class="sxs-lookup"><span data-stu-id="b0090-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="b0090-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span><span class="sxs-lookup"><span data-stu-id="b0090-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="b0090-110">This is the position of the block within the section.</span><span class="sxs-lookup"><span data-stu-id="b0090-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="b0090-111">[out] A pointer to a location that receives the address of the retrieved block.</span><span class="sxs-lookup"><span data-stu-id="b0090-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0090-112">Note</span><span class="sxs-lookup"><span data-stu-id="b0090-112">Remarks</span></span>  
 <span data-ttu-id="b0090-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span><span class="sxs-lookup"><span data-stu-id="b0090-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0090-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b0090-114">Requirements</span></span>  
 <span data-ttu-id="b0090-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0090-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0090-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0090-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0090-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0090-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0090-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0090-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0090-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b0090-119">See also</span></span>

- [<span data-ttu-id="b0090-120">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="b0090-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
