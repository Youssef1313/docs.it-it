---
title: Metodo IXCLRDataMethodInstance::GetILAddressMap
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 66e4768acff7ab735c6ac9e8f8f51a9511f7e371
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744691"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="02240-102">Metodo IXCLRDataMethodInstance::GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="02240-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="02240-103">Ottiene il livello di integrità per le informazioni di mapping di indirizzi.</span><span class="sxs-lookup"><span data-stu-id="02240-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="02240-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="02240-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="02240-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="02240-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="02240-106">[in] La lunghezza della matrice di mappe fornito.</span><span class="sxs-lookup"><span data-stu-id="02240-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="02240-107">[out] Il numero di voci della mappa che desideri nel metodo.</span><span class="sxs-lookup"><span data-stu-id="02240-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="02240-108">[out, size_is(mapLen)] La matrice per archiviare le voci della mappa.</span><span class="sxs-lookup"><span data-stu-id="02240-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="02240-109">Note</span><span class="sxs-lookup"><span data-stu-id="02240-109">Remarks</span></span>

<span data-ttu-id="02240-110">Il metodo specificato fa parte di `IXCLRDataMethodInstance` interfaccia e corrisponde al 14 slot della tabella di metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="02240-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="02240-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="02240-111">Requirements</span></span>

<span data-ttu-id="02240-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02240-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="02240-113">**Intestazione:** Nessuna</span><span class="sxs-lookup"><span data-stu-id="02240-113">**Header:** None</span></span>  
<span data-ttu-id="02240-114">**Libreria:** Nessuna</span><span class="sxs-lookup"><span data-stu-id="02240-114">**Library:** None</span></span>  
<span data-ttu-id="02240-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02240-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="02240-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="02240-116">See also</span></span>

- [<span data-ttu-id="02240-117">Debug</span><span class="sxs-lookup"><span data-stu-id="02240-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="02240-118">Interfaccia IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="02240-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
