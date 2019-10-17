---
title: Metodo SqlStreamChars. Dispose (Boolean) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395758"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="ddbda-102">Metodo SqlStreamChars. Dispose (Boolean)</span><span class="sxs-lookup"><span data-stu-id="ddbda-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="ddbda-103">Quando sottoposto a override in una classe derivata, rilascia le risorse usate dal flusso.</span><span class="sxs-lookup"><span data-stu-id="ddbda-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="ddbda-104">L'assembly che contiene questo metodo ha una relazione friend con SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="ddbda-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ddbda-105">È destinato all'uso da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ddbda-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ddbda-106">Per gli altri database, utilizzare il meccanismo di hosting fornito da tale database.</span><span class="sxs-lookup"><span data-stu-id="ddbda-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="ddbda-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ddbda-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="ddbda-108">`true` per rilasciare sia le risorse gestite sia quelle non gestite; `false` per rilasciare solo le risorse non gestite.</span><span class="sxs-lookup"><span data-stu-id="ddbda-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="ddbda-109">Note</span><span class="sxs-lookup"><span data-stu-id="ddbda-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ddbda-110">Il metodo `SqlStreamChars.Dispose` è privato e non è destinato a essere usato direttamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="ddbda-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ddbda-111">Microsoft non supporta l'utilizzo di questo metodo in un'applicazione di produzione in qualsiasi circostanza.</span><span class="sxs-lookup"><span data-stu-id="ddbda-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ddbda-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ddbda-112">Requirements</span></span>

<span data-ttu-id="ddbda-113">**Spazio dei nomi:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ddbda-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ddbda-114">**Assembly:** System. Data (in System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="ddbda-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ddbda-115">**Versioni .NET Framework:** Disponibile a partire da 2,0.</span><span class="sxs-lookup"><span data-stu-id="ddbda-115">**.NET Framework versions:** Available since 2.0.</span></span>
