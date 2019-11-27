---
title: Metodo EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448729"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="4bf38-102">Metodo EnumImportTypes</span><span class="sxs-lookup"><span data-stu-id="4bf38-102">EnumImportTypes Method</span></span>

<span data-ttu-id="4bf38-103">Enumera ogni tipo in ogni ambito.</span><span class="sxs-lookup"><span data-stu-id="4bf38-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bf38-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4bf38-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="4bf38-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4bf38-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="4bf38-106">Handle per Enumerator.</span><span class="sxs-lookup"><span data-stu-id="4bf38-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="4bf38-107">Numero massimo di tipi da recuperare.</span><span class="sxs-lookup"><span data-stu-id="4bf38-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="4bf38-108">Riceve i token di tipo, per non superare `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="4bf38-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="4bf38-109">Riceve il numero effettivo di tipo in `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="4bf38-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4bf38-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4bf38-110">Return Value</span></span>

<span data-ttu-id="4bf38-111">Restituisce S_OK se il metodo ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="4bf38-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bf38-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4bf38-112">Requirements</span></span>

<span data-ttu-id="4bf38-113">Richiede ALink. h</span><span class="sxs-lookup"><span data-stu-id="4bf38-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf38-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4bf38-114">See also</span></span>

- [<span data-ttu-id="4bf38-115">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="4bf38-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4bf38-116">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="4bf38-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4bf38-117">Alink (API)</span><span class="sxs-lookup"><span data-stu-id="4bf38-117">ALink API</span></span>](index.md)
