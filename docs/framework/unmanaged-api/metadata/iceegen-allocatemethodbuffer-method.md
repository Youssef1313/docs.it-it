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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 080c16d3a7baceaa277b3418ac2e17391090f00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750604"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="7e845-102">Metodo ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="7e845-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="7e845-103">Crea un buffer della dimensione specificata per un metodo e ottiene l'indirizzo virtuale relativo del metodo.</span><span class="sxs-lookup"><span data-stu-id="7e845-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="7e845-104">Questo metodo è obsoleto e non deve essere utilizzato.</span><span class="sxs-lookup"><span data-stu-id="7e845-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e845-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7e845-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e845-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="7e845-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="7e845-107">[in] La lunghezza del buffer da creare.</span><span class="sxs-lookup"><span data-stu-id="7e845-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="7e845-108">[out] Il buffer restituito.</span><span class="sxs-lookup"><span data-stu-id="7e845-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="7e845-109">[out] L'indirizzo virtuale relativo del metodo.</span><span class="sxs-lookup"><span data-stu-id="7e845-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e845-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7e845-110">Requirements</span></span>  
 <span data-ttu-id="7e845-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e845-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e845-112">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7e845-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e845-113">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7e845-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e845-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e845-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e845-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7e845-115">See also</span></span>

- [<span data-ttu-id="7e845-116">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="7e845-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
