---
ms.openlocfilehash: 8cc2e1436059f92564d4c3ec534632674081ae75
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394455"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="d61e3-101">SignalR: costruttori HubConnectionContext modificati</span><span class="sxs-lookup"><span data-stu-id="d61e3-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="d61e3-102">I costruttori `HubConnectionContext` di SignalR sono stati modificati in modo da accettare un tipo di opzioni, anziché più parametri, alle opzioni di aggiunta di una prova futura.</span><span class="sxs-lookup"><span data-stu-id="d61e3-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="d61e3-103">Questa modifica sostituisce due costruttori con un solo costruttore che accetta un tipo di opzioni.</span><span class="sxs-lookup"><span data-stu-id="d61e3-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d61e3-104">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="d61e3-104">Version introduced</span></span>

<span data-ttu-id="d61e3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d61e3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d61e3-106">Comportamento precedente</span><span class="sxs-lookup"><span data-stu-id="d61e3-106">Old behavior</span></span>

<span data-ttu-id="d61e3-107">`HubConnectionContext` ha due costruttori:</span><span class="sxs-lookup"><span data-stu-id="d61e3-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="d61e3-108">Nuovo comportamento</span><span class="sxs-lookup"><span data-stu-id="d61e3-108">New behavior</span></span>

<span data-ttu-id="d61e3-109">I due costruttori sono stati rimossi e sostituiti con un costruttore:</span><span class="sxs-lookup"><span data-stu-id="d61e3-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="d61e3-110">Motivo della modifica</span><span class="sxs-lookup"><span data-stu-id="d61e3-110">Reason for change</span></span>

<span data-ttu-id="d61e3-111">Il nuovo costruttore utilizza un nuovo oggetto opzioni.</span><span class="sxs-lookup"><span data-stu-id="d61e3-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="d61e3-112">Di conseguenza, le funzionalità di `HubConnectionContext` possono essere espanse in futuro senza rendere più costruttori e modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="d61e3-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d61e3-113">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="d61e3-113">Recommended action</span></span>

<span data-ttu-id="d61e3-114">Anziché utilizzare il costruttore seguente:</span><span class="sxs-lookup"><span data-stu-id="d61e3-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext, 
    keepAliveInterval: TimeSpan.FromSeconds(15), 
    loggerFactory, 
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="d61e3-115">Usare il costruttore seguente:</span><span class="sxs-lookup"><span data-stu-id="d61e3-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="d61e3-116">Category</span><span class="sxs-lookup"><span data-stu-id="d61e3-116">Category</span></span>

<span data-ttu-id="d61e3-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d61e3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d61e3-118">API interessate</span><span class="sxs-lookup"><span data-stu-id="d61e3-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
