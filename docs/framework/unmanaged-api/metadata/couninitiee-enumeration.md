---
title: Enumerazione COUNINITIEE
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 57054bdb7e3b991bc81985c02ec72a4110f31d60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436441"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="67df4-102">Enumerazione COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="67df4-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="67df4-103">Specifica le costanti usate da [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) durante l'inizializzazione del Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="67df4-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67df4-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="67df4-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="67df4-105">Membri</span><span class="sxs-lookup"><span data-stu-id="67df4-105">Members</span></span>  
  
|<span data-ttu-id="67df4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="67df4-106">Member</span></span>|<span data-ttu-id="67df4-107">description</span><span class="sxs-lookup"><span data-stu-id="67df4-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="67df4-108">Indica la modalità di inizializzazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="67df4-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="67df4-109">Indica la modalità di non inizializzazione per lo scaricamento di un assembly.</span><span class="sxs-lookup"><span data-stu-id="67df4-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67df4-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="67df4-110">Requirements</span></span>  
 <span data-ttu-id="67df4-111">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67df4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67df4-112">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="67df4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67df4-113">**Libreria:** Incluso come risorsa in MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="67df4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67df4-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67df4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67df4-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67df4-115">See also</span></span>

- [<span data-ttu-id="67df4-116">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="67df4-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
