---
title: Struttura COR_PRF_FUNCTION_ARGUMENT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 658b88349bedcbcefd0b97226c7bd1fa34f656c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781917"
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="92c58-102">Struttura COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="92c58-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="92c58-103">Rappresenta gli argomenti di una funzione, in ordine da sinistra a destra.</span><span class="sxs-lookup"><span data-stu-id="92c58-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c58-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="92c58-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="92c58-105">Membri</span><span class="sxs-lookup"><span data-stu-id="92c58-105">Members</span></span>  
  
|<span data-ttu-id="92c58-106">Member</span><span class="sxs-lookup"><span data-stu-id="92c58-106">Member</span></span>|<span data-ttu-id="92c58-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="92c58-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="92c58-108">Il numero di blocchi di argomenti.</span><span class="sxs-lookup"><span data-stu-id="92c58-108">The number of blocks of arguments.</span></span> <span data-ttu-id="92c58-109">Vale a dire, questo valore è il numero di [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) le strutture nel `ranges` matrice.</span><span class="sxs-lookup"><span data-stu-id="92c58-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="92c58-110">Le dimensioni totali di tutti gli argomenti.</span><span class="sxs-lookup"><span data-stu-id="92c58-110">The total size of all arguments.</span></span> <span data-ttu-id="92c58-111">In altre parole, questo valore è la somma delle lunghezze degli argomenti.</span><span class="sxs-lookup"><span data-stu-id="92c58-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="92c58-112">Matrice di `COR_PRF_FUNCTION_ARGUMENT_RANGE` strutture, ognuno dei quali rappresenta un blocco di argomenti della funzione.</span><span class="sxs-lookup"><span data-stu-id="92c58-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c58-113">Note</span><span class="sxs-lookup"><span data-stu-id="92c58-113">Remarks</span></span>  
 <span data-ttu-id="92c58-114">Una funzione può avere un numero di argomenti.</span><span class="sxs-lookup"><span data-stu-id="92c58-114">A function may have many arguments.</span></span> <span data-ttu-id="92c58-115">Tali argomenti non possono essere archiviati in modo contiguo nella memoria.</span><span class="sxs-lookup"><span data-stu-id="92c58-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="92c58-116">Potrebbe essere un blocco di tre argomenti in un'unica posizione, un blocco di due argomenti in un'altra posizione e un blocco finale di un argomento in una posizione diversa.</span><span class="sxs-lookup"><span data-stu-id="92c58-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="92c58-117">Questi argomenti sono tutti della stessa funzione; sono semplicemente archiviati in posizioni diverse.</span><span class="sxs-lookup"><span data-stu-id="92c58-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="92c58-118">Il `COR_PRF_FUNCTION_ARGUMENT_INFO` struttura rappresenta tutti gli argomenti di una singola funzione.</span><span class="sxs-lookup"><span data-stu-id="92c58-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="92c58-119">Usa una matrice per fare riferimento a tutti i blocchi degli argomenti della funzione.</span><span class="sxs-lookup"><span data-stu-id="92c58-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="92c58-120">Per una singola funzione, non sarà pertanto necessario un unico `COR_PRF_FUNCTION_ARGUMENT_INFO` struttura, a cui fa riferimento a più `COR_PRF_FUNCTION_ARGUMENT_RANGE` strutture, ognuno dei quali punta a uno o più argomenti di funzione.</span><span class="sxs-lookup"><span data-stu-id="92c58-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="92c58-121">Gli argomenti che vengono archiviati nei registri sono stati distribuiti in memoria per compilare le strutture.</span><span class="sxs-lookup"><span data-stu-id="92c58-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c58-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="92c58-122">Requirements</span></span>  
 <span data-ttu-id="92c58-123">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c58-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c58-124">**Intestazione:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="92c58-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="92c58-125">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92c58-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c58-126">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c58-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c58-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="92c58-127">See also</span></span>

- [<span data-ttu-id="92c58-128">Strutture di profilatura</span><span class="sxs-lookup"><span data-stu-id="92c58-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
