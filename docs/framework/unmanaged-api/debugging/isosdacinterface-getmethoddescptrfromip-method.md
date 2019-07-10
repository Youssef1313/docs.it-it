---
title: Metodo ISOSDacInterface::GetMethodDescPtrFromIP
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cd256250021436e611142de11c3625a21aeec814
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764749"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="225df-102">Metodo ISOSDacInterface::GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="225df-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="225df-103">Recupera il puntatore del MethodDesc corrispondente metodo contenente l'indirizzo dell'istruzione nativo specificato.</span><span class="sxs-lookup"><span data-stu-id="225df-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="225df-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="225df-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="225df-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="225df-105">Parameters</span></span>

`ip`\
<span data-ttu-id="225df-106">[in] Un indirizzo all'interno del metodo in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="225df-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="225df-107">[out] L'indirizzo del `MethodDesc` per il metodo specifico.</span><span class="sxs-lookup"><span data-stu-id="225df-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="225df-108">Note</span><span class="sxs-lookup"><span data-stu-id="225df-108">Remarks</span></span>

<span data-ttu-id="225df-109">Il metodo specificato fa parte di [ `ISOSDacInterface` interfaccia](isosdacinterface-interface.md) e corrisponde al 21 slot della tabella di metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="225df-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="225df-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="225df-110">Requirements</span></span>

<span data-ttu-id="225df-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="225df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="225df-112">**Intestazione:** nessuno</span><span class="sxs-lookup"><span data-stu-id="225df-112">**Header:** None</span></span>  
<span data-ttu-id="225df-113">**Libreria:** nessuno</span><span class="sxs-lookup"><span data-stu-id="225df-113">**Library:** None</span></span>  
<span data-ttu-id="225df-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="225df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="225df-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="225df-115">See also</span></span>

- [<span data-ttu-id="225df-116">Debug</span><span class="sxs-lookup"><span data-stu-id="225df-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="225df-117">Interfaccia ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="225df-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
