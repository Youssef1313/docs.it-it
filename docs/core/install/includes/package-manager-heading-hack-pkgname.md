---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450884"
---

<span data-ttu-id="63513-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="63513-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="63513-102">**product**</span><span class="sxs-lookup"><span data-stu-id="63513-102">**product**</span></span>\
<span data-ttu-id="63513-103">The type of .NET product to install.</span><span class="sxs-lookup"><span data-stu-id="63513-103">The type of .NET product to install.</span></span> <span data-ttu-id="63513-104">Le opzioni valide sono:</span><span class="sxs-lookup"><span data-stu-id="63513-104">Valid options are:</span></span>

  - <span data-ttu-id="63513-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="63513-105">dotnet</span></span>
  - <span data-ttu-id="63513-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="63513-106">aspnetcore</span></span>

- <span data-ttu-id="63513-107">**type**</span><span class="sxs-lookup"><span data-stu-id="63513-107">**type**</span></span>\
<span data-ttu-id="63513-108">Chooses the SDK or the runtime.</span><span class="sxs-lookup"><span data-stu-id="63513-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="63513-109">Le opzioni valide sono:</span><span class="sxs-lookup"><span data-stu-id="63513-109">Valid options are:</span></span>

  - <span data-ttu-id="63513-110">SDK</span><span class="sxs-lookup"><span data-stu-id="63513-110">sdk</span></span>
  - <span data-ttu-id="63513-111">runtime</span><span class="sxs-lookup"><span data-stu-id="63513-111">runtime</span></span>

- <span data-ttu-id="63513-112">**version**</span><span class="sxs-lookup"><span data-stu-id="63513-112">**version**</span></span>\
<span data-ttu-id="63513-113">The version of the SDK or runtime to install.</span><span class="sxs-lookup"><span data-stu-id="63513-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="63513-114">This article will always give the instructions for the latest supported version.</span><span class="sxs-lookup"><span data-stu-id="63513-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="63513-115">Valid options are any released version, such as:</span><span class="sxs-lookup"><span data-stu-id="63513-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="63513-116">3.0</span><span class="sxs-lookup"><span data-stu-id="63513-116">3.0</span></span>
  - <span data-ttu-id="63513-117">2.2</span><span class="sxs-lookup"><span data-stu-id="63513-117">2.2</span></span>
  - <span data-ttu-id="63513-118">2.1</span><span class="sxs-lookup"><span data-stu-id="63513-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="63513-119">Esempi</span><span class="sxs-lookup"><span data-stu-id="63513-119">Examples</span></span>

- <span data-ttu-id="63513-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="63513-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="63513-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="63513-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="63513-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="63513-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="63513-123">Risolvere i problemi</span><span class="sxs-lookup"><span data-stu-id="63513-123">Troubleshoot</span></span>

<span data-ttu-id="63513-124">If the package combination doesn't work, it's not available.</span><span class="sxs-lookup"><span data-stu-id="63513-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="63513-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="63513-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="63513-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="63513-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
