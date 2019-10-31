---
title: Struttura COR_DEBUG_IL_TO_NATIVE_MAP
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: 2a36c9808f29c038e3185157078c235959baf13c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132369"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="3c81f-102">Struttura COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="3c81f-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="3c81f-103">Contiene gli offset usati per mappare il codice MSIL (Microsoft Intermediate Language) al codice nativo.</span><span class="sxs-lookup"><span data-stu-id="3c81f-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c81f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3c81f-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="3c81f-105">Members</span><span class="sxs-lookup"><span data-stu-id="3c81f-105">Members</span></span>  
  
|<span data-ttu-id="3c81f-106">Member</span><span class="sxs-lookup"><span data-stu-id="3c81f-106">Member</span></span>|<span data-ttu-id="3c81f-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3c81f-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="3c81f-108">Offset del codice MSIL.</span><span class="sxs-lookup"><span data-stu-id="3c81f-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="3c81f-109">Offset dell'inizio del codice nativo.</span><span class="sxs-lookup"><span data-stu-id="3c81f-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="3c81f-110">Offset della fine del codice nativo.</span><span class="sxs-lookup"><span data-stu-id="3c81f-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c81f-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3c81f-111">Requirements</span></span>  
 <span data-ttu-id="3c81f-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c81f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c81f-113">**Intestazione:** CorProf. idl, CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="3c81f-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="3c81f-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c81f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c81f-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c81f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c81f-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3c81f-116">See also</span></span>

- [<span data-ttu-id="3c81f-117">Metodo GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="3c81f-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="3c81f-118">Metodo GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="3c81f-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="3c81f-119">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="3c81f-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3c81f-120">Debug</span><span class="sxs-lookup"><span data-stu-id="3c81f-120">Debugging</span></span>](index.md)
