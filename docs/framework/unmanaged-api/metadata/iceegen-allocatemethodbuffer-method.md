---
title: Metodo ICeeGen::AllocateMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 34636f1ca8e42c452aa41f6145d439a26f01b0a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436400"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="941b9-102">Metodo ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="941b9-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="941b9-103">Crea un buffer con la dimensione specificata per un metodo e ottiene l'indirizzo virtuale relativo del metodo.</span><span class="sxs-lookup"><span data-stu-id="941b9-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="941b9-104">Questo metodo è obsoleto e non deve essere utilizzato.</span><span class="sxs-lookup"><span data-stu-id="941b9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941b9-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="941b9-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="941b9-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="941b9-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="941b9-107">in Lunghezza del buffer da creare.</span><span class="sxs-lookup"><span data-stu-id="941b9-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="941b9-108">out Buffer restituito.</span><span class="sxs-lookup"><span data-stu-id="941b9-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="941b9-109">out Indirizzo virtuale relativo del metodo.</span><span class="sxs-lookup"><span data-stu-id="941b9-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941b9-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="941b9-110">Requirements</span></span>  
 <span data-ttu-id="941b9-111">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="941b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941b9-112">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="941b9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="941b9-113">**Libreria:** Usato come risorsa in MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="941b9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="941b9-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941b9-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="941b9-115">See also</span></span>

- [<span data-ttu-id="941b9-116">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="941b9-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
