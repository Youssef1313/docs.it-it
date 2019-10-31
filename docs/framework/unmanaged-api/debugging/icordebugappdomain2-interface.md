---
title: Interfaccia ICorDebugAppDomain2
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: bff270ff774692d058a36c7f47ab474b08bceb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088955"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="24b1a-102">Interfaccia ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="24b1a-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="24b1a-103">Fornisce metodi per lavorare con matrici, puntatori, puntatori a funzione e tipi di riferimento.</span><span class="sxs-lookup"><span data-stu-id="24b1a-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="24b1a-104">Questa interfaccia è un'estensione dell'interfaccia ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="24b1a-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24b1a-105">Metodi</span><span class="sxs-lookup"><span data-stu-id="24b1a-105">Methods</span></span>  
  
|<span data-ttu-id="24b1a-106">Metodo</span><span class="sxs-lookup"><span data-stu-id="24b1a-106">Method</span></span>|<span data-ttu-id="24b1a-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="24b1a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24b1a-108">Metodo GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="24b1a-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="24b1a-109">Ottiene una matrice del tipo specificato o un puntatore o un riferimento al tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="24b1a-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="24b1a-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="24b1a-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="24b1a-111">Ottiene un puntatore a una funzione con una firma specificata.</span><span class="sxs-lookup"><span data-stu-id="24b1a-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24b1a-112">Note</span><span class="sxs-lookup"><span data-stu-id="24b1a-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24b1a-113">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="24b1a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b1a-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="24b1a-114">Requirements</span></span>  
 <span data-ttu-id="24b1a-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b1a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b1a-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24b1a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24b1a-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24b1a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24b1a-118">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b1a-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24b1a-119">See also</span></span>

- [<span data-ttu-id="24b1a-120">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="24b1a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
