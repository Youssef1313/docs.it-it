---
title: Struttura DacpMethodDescData
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739138"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="cd3e7-102">Struttura DacpMethodDescData</span><span class="sxs-lookup"><span data-stu-id="cd3e7-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="cd3e7-103">Definisce un buffer di trasporto per le informazioni di runtime del metodo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cd3e7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cd3e7-104">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="cd3e7-105">Membri</span><span class="sxs-lookup"><span data-stu-id="cd3e7-105">Members</span></span>

| <span data-ttu-id="cd3e7-106">Member</span><span class="sxs-lookup"><span data-stu-id="cd3e7-106">Member</span></span>                       | <span data-ttu-id="cd3e7-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cd3e7-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="cd3e7-108">Indica se il runtime dispone di codice nativo disponibile per la creazione dell'istanza specificata del metodo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="cd3e7-109">Indica se il metodo viene generato in modo dinamico tramite la generazione di codice leggero.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="cd3e7-110">Numero di slot del metodo nella tabella di metodo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="cd3e7-111">Indirizzo nativo iniziale del metodo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="cd3e7-112">Puntatore a un buffer utilizzato internamente dal runtime.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="cd3e7-113">Puntatore al `MethodDesc` in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="cd3e7-114">Puntatore a un buffer utilizzato internamente dal runtime per tenere traccia di metodi.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="cd3e7-115">Puntatore a un buffer utilizzato internamente dal runtime per informazioni sul modulo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="cd3e7-116">Token associato al metodo specificato.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="cd3e7-117">Puntatore a un buffer di raccolta garbage utilizzato internamente dal runtime.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="cd3e7-118">Puntatore a un buffer di raccolta garbage utilizzato internamente dal runtime.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="cd3e7-119">Se il metodo dinamico, il runtime Usa internamente il buffer per le informazioni di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="cd3e7-120">Utilizzato per popolare la struttura per ogni richiesta quando viene specificato un indirizzo di codice nativo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="cd3e7-121">Informazioni sull'ultima versione instrumentata del metodo.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="cd3e7-122">ReJIT informazioni per l'indirizzo native richiesto.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="cd3e7-123">Numero di volte in cui che il metodo è stato rejitted tramite la strumentazione.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="cd3e7-124">Note</span><span class="sxs-lookup"><span data-stu-id="cd3e7-124">Remarks</span></span>

<span data-ttu-id="cd3e7-125">Questa struttura si trova all'interno del runtime e non viene esposto tramite le intestazioni o i file di libreria.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cd3e7-126">Per usarlo, definire la struttura come specificato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="cd3e7-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd3e7-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cd3e7-127">Requirements</span></span>
<span data-ttu-id="cd3e7-128">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd3e7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cd3e7-129">**Intestazione:** nessuno</span><span class="sxs-lookup"><span data-stu-id="cd3e7-129">**Header:** None</span></span>  
<span data-ttu-id="cd3e7-130">**Libreria:** nessuno</span><span class="sxs-lookup"><span data-stu-id="cd3e7-130">**Library:** None</span></span>  
<span data-ttu-id="cd3e7-131">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd3e7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cd3e7-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cd3e7-132">See also</span></span>

- [<span data-ttu-id="cd3e7-133">Debug</span><span class="sxs-lookup"><span data-stu-id="cd3e7-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cd3e7-134">Strutture di debug</span><span class="sxs-lookup"><span data-stu-id="cd3e7-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="cd3e7-135">Tipi di dati comuni</span><span class="sxs-lookup"><span data-stu-id="cd3e7-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
