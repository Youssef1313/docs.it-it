---
title: Enumerazione CLRDataEnumMemoryFlags
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274235"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="68dbb-102">Enumerazione CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="68dbb-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="68dbb-103">Indica le aree di memoria che devono essere incluse in una chiamata al metodo [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="68dbb-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68dbb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="68dbb-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="68dbb-105">Membri</span><span class="sxs-lookup"><span data-stu-id="68dbb-105">Members</span></span>  
  
|<span data-ttu-id="68dbb-106">Member</span><span class="sxs-lookup"><span data-stu-id="68dbb-106">Member</span></span>|<span data-ttu-id="68dbb-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="68dbb-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="68dbb-108">Minidump, ovvero un dump di memoria sparse.</span><span class="sxs-lookup"><span data-stu-id="68dbb-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="68dbb-109">Dump completo dell'heap.</span><span class="sxs-lookup"><span data-stu-id="68dbb-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68dbb-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="68dbb-110">Requirements</span></span>  
 <span data-ttu-id="68dbb-111">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68dbb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68dbb-112">**Intestazione:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="68dbb-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="68dbb-113">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68dbb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68dbb-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68dbb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dbb-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68dbb-115">See also</span></span>

- [<span data-ttu-id="68dbb-116">Enumerazioni di debug</span><span class="sxs-lookup"><span data-stu-id="68dbb-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
