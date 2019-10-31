---
title: Funzione ClrCreateManagedInstance
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131992"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="316b2-102">Funzione ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="316b2-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="316b2-103">Crea un'istanza del tipo gestito specificato.</span><span class="sxs-lookup"><span data-stu-id="316b2-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="316b2-104">Questa funzione è stata deprecata nel .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="316b2-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="316b2-105">Utilizzare l'attivazione COM per creare un'istanza del tipo gestito oppure utilizzare l'hosting (vedere [le interfacce di hosting CLR aggiunte in .NET Framework 4 e 4,5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="316b2-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316b2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="316b2-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="316b2-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="316b2-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="316b2-108">in Puntatore al nome del tipo di istanza richiesto.</span><span class="sxs-lookup"><span data-stu-id="316b2-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="316b2-109">in `IID` del tipo di istanza richiesta.</span><span class="sxs-lookup"><span data-stu-id="316b2-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="316b2-110">out Puntatore a un puntatore a un'istanza del tipo gestito richiesta dal chiamante.</span><span class="sxs-lookup"><span data-stu-id="316b2-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="316b2-111">Note</span><span class="sxs-lookup"><span data-stu-id="316b2-111">Remarks</span></span>  
 <span data-ttu-id="316b2-112">Il Common Language Runtime deve essere già caricato in un processo.</span><span class="sxs-lookup"><span data-stu-id="316b2-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="316b2-113">Ad esempio, può essere caricata utilizzando una chiamata alla funzione [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) prima che venga chiamata la funzione `ClrCreateManagedInstance`.</span><span class="sxs-lookup"><span data-stu-id="316b2-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="316b2-114">Se il runtime non è caricato, `ClrCreateManagedInstance` tenta innanzitutto di caricare v 1.0.3705 del runtime.</span><span class="sxs-lookup"><span data-stu-id="316b2-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="316b2-115">Se l'operazione ha esito negativo, tenta di caricare la versione più recente del runtime.</span><span class="sxs-lookup"><span data-stu-id="316b2-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="316b2-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="316b2-116">Requirements</span></span>  
 <span data-ttu-id="316b2-117">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="316b2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316b2-118">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="316b2-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="316b2-119">**Libreria:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="316b2-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="316b2-120">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316b2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316b2-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="316b2-121">See also</span></span>

- [<span data-ttu-id="316b2-122">Funzioni di hosting CLR deprecate</span><span class="sxs-lookup"><span data-stu-id="316b2-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="316b2-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="316b2-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
