---
title: Metodo IXCLRDataProcess::StartEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 88ce9dd928871d71058fe28c243a9fb51b729778
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416690"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="526e1-102">Metodo IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="526e1-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="526e1-103">Fornisce un handle per enumerare le istanze di metodo di `AppDomain` iniziando in corrispondenza di un determinato indirizzo.</span><span class="sxs-lookup"><span data-stu-id="526e1-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="526e1-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="526e1-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="526e1-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="526e1-105">Parameters</span></span>

<span data-ttu-id="526e1-106">`address` [in] L'indirizzo dell'istanza del primo metodo.</span><span class="sxs-lookup"><span data-stu-id="526e1-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="526e1-107">`appDomain` [in] Il dominio di applicazione delle istanze del metodo.</span><span class="sxs-lookup"><span data-stu-id="526e1-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="526e1-108">`handle` [out] Handle per l'enumerazione delle istanze di metodo.</span><span class="sxs-lookup"><span data-stu-id="526e1-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="526e1-109">Note</span><span class="sxs-lookup"><span data-stu-id="526e1-109">Remarks</span></span>

<span data-ttu-id="526e1-110">Il metodo specificato fa parte di `IXCLRDataProcess` interfaccia e corrisponde al 27 slot della tabella di metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="526e1-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="526e1-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="526e1-111">Requirements</span></span>

<span data-ttu-id="526e1-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="526e1-113">**Intestazione:** nessuno</span><span class="sxs-lookup"><span data-stu-id="526e1-113">**Header:** None</span></span>  
<span data-ttu-id="526e1-114">**Libreria:** nessuno</span><span class="sxs-lookup"><span data-stu-id="526e1-114">**Library:** None</span></span>  
<span data-ttu-id="526e1-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="526e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="526e1-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="526e1-116">See Also</span></span>

- [<span data-ttu-id="526e1-117">Enumerazione CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="526e1-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="526e1-118">Debug</span><span class="sxs-lookup"><span data-stu-id="526e1-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="526e1-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="526e1-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)