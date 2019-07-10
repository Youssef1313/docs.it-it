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
ms.openlocfilehash: d7c395e68ad5d8042f9850f25757a5aa445e5c40
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752680"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="405dd-102">Metodo IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="405dd-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="405dd-103">Fornisce un handle per enumerare le istanze di metodo di `AppDomain` iniziando in corrispondenza di un determinato indirizzo.</span><span class="sxs-lookup"><span data-stu-id="405dd-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="405dd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="405dd-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="405dd-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="405dd-105">Parameters</span></span>

`address`\
<span data-ttu-id="405dd-106">[in] L'indirizzo dell'istanza del primo metodo.</span><span class="sxs-lookup"><span data-stu-id="405dd-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="405dd-107">[in] Il dominio di applicazione delle istanze del metodo.</span><span class="sxs-lookup"><span data-stu-id="405dd-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="405dd-108">[out] Handle per l'enumerazione delle istanze di metodo.</span><span class="sxs-lookup"><span data-stu-id="405dd-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="405dd-109">Note</span><span class="sxs-lookup"><span data-stu-id="405dd-109">Remarks</span></span>

<span data-ttu-id="405dd-110">Il metodo specificato fa parte di `IXCLRDataProcess` interfaccia e corrisponde al 27 slot della tabella di metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="405dd-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="405dd-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="405dd-111">Requirements</span></span>

<span data-ttu-id="405dd-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="405dd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="405dd-113">**Intestazione:** nessuno</span><span class="sxs-lookup"><span data-stu-id="405dd-113">**Header:** None</span></span>  
<span data-ttu-id="405dd-114">**Libreria:** nessuno</span><span class="sxs-lookup"><span data-stu-id="405dd-114">**Library:** None</span></span>  
<span data-ttu-id="405dd-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="405dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="405dd-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="405dd-116">See also</span></span>

- [<span data-ttu-id="405dd-117">Enumerazione CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="405dd-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="405dd-118">Debug</span><span class="sxs-lookup"><span data-stu-id="405dd-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="405dd-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="405dd-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
