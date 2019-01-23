---
title: Metodo SqlStreamChars.Dispose(Boolean) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 930a4a69c6c44269e728fbcef62e561ab165ea22
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222363"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="6cb3f-102">Metodo SqlStreamChars.Dispose(Boolean)</span><span class="sxs-lookup"><span data-stu-id="6cb3f-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="6cb3f-103">Quando sottoposto a override in una classe derivata, rilascia le risorse usate dal flusso.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="6cb3f-104">L'assembly contenente questo metodo ha una relazione di tipo friend SQLAccess.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="6cb3f-105">Si tratta per l'uso da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="6cb3f-106">Per altri database, usare il meccanismo di hosting fornito da tale database.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="6cb3f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="6cb3f-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="6cb3f-108">`true` per rilasciare sia le risorse gestite sia quelle non gestite; `false` per rilasciare solo le risorse non gestite.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cb3f-109">Note</span><span class="sxs-lookup"><span data-stu-id="6cb3f-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6cb3f-110">Il `SqlStreamChars.Dispose` metodo è privato e non deve essere utilizzato direttamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6cb3f-111">Microsoft non supporta l'uso di questo campo in un'applicazione di produzione in alcuna circostanza.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6cb3f-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6cb3f-112">Requirements</span></span>

<span data-ttu-id="6cb3f-113">**Spazio dei nomi:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="6cb3f-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="6cb3f-114">**Assembly:** System. Data (in System)</span><span class="sxs-lookup"><span data-stu-id="6cb3f-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="6cb3f-115">**Versioni di .NET framework:** Disponibile dalla 2.0.</span><span class="sxs-lookup"><span data-stu-id="6cb3f-115">**.NET Framework versions:** Available since 2.0.</span></span>