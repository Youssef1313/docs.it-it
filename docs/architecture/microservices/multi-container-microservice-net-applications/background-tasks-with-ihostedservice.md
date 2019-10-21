---
title: Implementare attività in background in microservizi con IHostedService e la classe BackgroundService
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Informazioni sulle nuove opzioni per usare IHostedService e BackgroundService per implementare attività in background nei microservizi .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: ad91268925ad36d5b60d5d0601eee7544b79ab2e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318679"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="821ba-103">Implementare attività in background in microservizi con IHostedService e la classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="821ba-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="821ba-104">Le attività in background e i processi pianificati sono elementi che potrebbe essere necessario implementare, prima o poi, in un'applicazione basata su microservizi o in qualsiasi tipo di applicazione.</span><span class="sxs-lookup"><span data-stu-id="821ba-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="821ba-105">La differenza quando si usa un'architettura di microservizi consiste nella possibilità di implementare un singolo processo/contenitore di microservizi per ospitare queste attività in background così da poterlo ridurre o aumentare in base alle necessità, o persino assicurarsi che venga eseguita una sola istanza di tale processo/contenitore di microservizi.</span><span class="sxs-lookup"><span data-stu-id="821ba-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="821ba-106">Da un punto di vista generico, in .NET Core questi tipi di attività vengono chiamati *Servizi ospitati*, perché sono servizi/logica ospitati all'interno di un host, un'applicazione o un microservizio.</span><span class="sxs-lookup"><span data-stu-id="821ba-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="821ba-107">Si noti che, in questo caso, il servizio ospitato indica semplicemente una classe con la logica di attività in background.</span><span class="sxs-lookup"><span data-stu-id="821ba-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="821ba-108">Fin dalla versione .NET Core 2.0, il framework fornisce una nuova interfaccia denominata <xref:Microsoft.Extensions.Hosting.IHostedService> che consente di implementare facilmente i servizi ospitati.</span><span class="sxs-lookup"><span data-stu-id="821ba-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="821ba-109">L'idea di base è che è possibile registrare più attività in background (servizi ospitati), che vengono eseguite in background mentre l'host Web o l'host è in esecuzione, come illustrato nell'immagine 6-26.</span><span class="sxs-lookup"><span data-stu-id="821ba-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1.x e 2.x supportano IWebHost per i processi in background nelle app web, .NET Core 2.1 supporta IHost per i processi in background con app console semplici.](./media/image26.png)

<span data-ttu-id="821ba-111">**Figura 6-26**.</span><span class="sxs-lookup"><span data-stu-id="821ba-111">**Figure 6-26**.</span></span> <span data-ttu-id="821ba-112">Uso di IHostedService in un WebHost rispetto a un Host</span><span class="sxs-lookup"><span data-stu-id="821ba-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="821ba-113">Si noti la differenza tra `WebHost` e `Host`.</span><span class="sxs-lookup"><span data-stu-id="821ba-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="821ba-114">Un `WebHost` (classe base che implementa `IWebHost`) in ASP.NET Core 2.0 è l'elemento infrastruttura che si usa per fornire funzionalità di server HTTP al processo, ad esempio durante l'implementazione di un'app Web MVC o un servizio API Web.</span><span class="sxs-lookup"><span data-stu-id="821ba-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="821ba-115">Offre tutta l'efficacia di una nuova infrastruttura in ASP.NET Core, consentendo di usare l'aggiunta di dipendenze, inserire middleware nella pipeline di richieste e così via e di usare con precisione le interfacce `IHostedServices` per le attività in background.</span><span class="sxs-lookup"><span data-stu-id="821ba-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="821ba-116">In .NET Core 2.1 è stato introdotto un `Host` (classe di base che implementa `IHost`).</span><span class="sxs-lookup"><span data-stu-id="821ba-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="821ba-117">In pratica, un `Host` consente di avere un'infrastruttura simile a quella che si ha con `WebHost` (aggiunta di dipendenze, i servizi ospitati e così via), ma in questo caso si avrà un processo semplice e più snello come host, senza elementi correlati a MVC, API Web o funzionalità del server HTTP.</span><span class="sxs-lookup"><span data-stu-id="821ba-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="821ba-118">Di conseguenza, è possibile scegliere e creare un processo host specializzato con IHost per gestire i servizi ospitati e nient'altro, ad esempio un microservizio realizzato solo per l'hosting di `IHostedServices`, oppure è possibile in alternativa estendere un `WebHost` esistente di ASP.NET Core, ad esempio un'API Web di ASP.NET Core o un'app MVC già esistente.</span><span class="sxs-lookup"><span data-stu-id="821ba-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="821ba-119">Ogni approccio presenta vantaggi e svantaggi in base alle esigenze aziendali e di scalabilità.</span><span class="sxs-lookup"><span data-stu-id="821ba-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="821ba-120">In sostanza, se le attività in background non hanno nulla a che fare con HTTP (IWebHost), è consigliabile usare IHost.</span><span class="sxs-lookup"><span data-stu-id="821ba-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="821ba-121">Registrazione di servizi ospitati in un Host o WebHost</span><span class="sxs-lookup"><span data-stu-id="821ba-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="821ba-122">Approfondiamo ulteriormente l'interfaccia di `IHostedService` perché il suo utilizzo è abbastanza simile in un `WebHost` o un `Host`.</span><span class="sxs-lookup"><span data-stu-id="821ba-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="821ba-123">SignalR è un esempio di un elemento che usa i servizi ospitati, ma è possibile usarlo anche per operazioni molto più semplici, quali:</span><span class="sxs-lookup"><span data-stu-id="821ba-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="821ba-124">Un'attività che esegue in background il polling di un database alla ricerca di modifiche.</span><span class="sxs-lookup"><span data-stu-id="821ba-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="821ba-125">Un'attività pianificata di aggiornamento periodico della cache.</span><span class="sxs-lookup"><span data-stu-id="821ba-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="821ba-126">Un'implementazione di QueueBackgroundWorkItem che consente di eseguire un'attività in un thread in background.</span><span class="sxs-lookup"><span data-stu-id="821ba-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="821ba-127">L'elaborazione di messaggi da una coda di messaggi in background di un'app Web condividendo servizi comuni come `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="821ba-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="821ba-128">Un'attività in background avviata con `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="821ba-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="821ba-129">È praticamente possibile ripartire il carico di lavoro di qualsiasi azione in un'attività in background basata su IHostedService.</span><span class="sxs-lookup"><span data-stu-id="821ba-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="821ba-130">Per aggiungere uno o più `IHostedServices` al proprio `WebHost` o `Host` basta registrarli usando l'aggiunta standard di inserimento dipendenze in un `WebHost` di ASP.NET Core (oppure in un `Host` di .NET Core 2.1 e versioni successive).</span><span class="sxs-lookup"><span data-stu-id="821ba-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="821ba-131">In pratica, è necessario registrare i servizi ospitati all'interno del noto metodo `ConfigureServices()` della classe `Startup`, come illustrato nel codice seguente da un tipico WebHost ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="821ba-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="821ba-132">In questo codice, il servizio ospitato `GracePeriodManagerService` è il codice effettivo del microservizio aziendale Ordering in eShopOnContainers, mentre gli altri due sono solo esempi aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="821ba-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="821ba-133">L'esecuzione dell'attività in background `IHostedService` è coordinata con la durata dell'applicazione (a tal fine, host o microservizio).</span><span class="sxs-lookup"><span data-stu-id="821ba-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="821ba-134">Si registrano le attività quando viene avviata l'applicazione e si ha la possibilità di eseguire un'azione automatica o di pulizia quando è in corso l'arresto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="821ba-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="821ba-135">Senza usare `IHostedService`, è sempre possibile avviare un thread in background per eseguire qualsiasi attività.</span><span class="sxs-lookup"><span data-stu-id="821ba-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="821ba-136">La differenza è precisamente nel tempo di arresto dell'app, quando il thread potrebbe essere semplicemente terminato senza la possibilità di eseguire operazioni di pulizia automatica.</span><span class="sxs-lookup"><span data-stu-id="821ba-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="821ba-137">Interfaccia IHostedService</span><span class="sxs-lookup"><span data-stu-id="821ba-137">The IHostedService interface</span></span>

<span data-ttu-id="821ba-138">Quando si registra un `IHostedService`, .NET Core chiamerà i metodi `StartAsync()` e `StopAsync()` del tipo `IHostedService` rispettivamente durante l'avvio e l'arresto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="821ba-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="821ba-139">In particolare, il metodo start viene chiamato dopo che il server è stato avviato e `IApplicationLifetime.ApplicationStarted` viene attivato.</span><span class="sxs-lookup"><span data-stu-id="821ba-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="821ba-140">Il `IHostedService` definito in .NET Core sarà simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="821ba-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

<span data-ttu-id="821ba-141">Come è facile immaginare, è possibile creare più implementazioni di IHostedService e registrarle nel metodo `ConfigureService()` nel contenitore DI, come illustrato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="821ba-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="821ba-142">Tutti i servizi ospitati verranno avviati e arrestati con l'applicazione/microservizio.</span><span class="sxs-lookup"><span data-stu-id="821ba-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="821ba-143">Lo sviluppatore è responsabile della gestione dell'azione di arresto o dei servizi quando il metodo `StopAsync()` viene attivato dall'host.</span><span class="sxs-lookup"><span data-stu-id="821ba-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="821ba-144">Implementazione di IHostedService con una classe personalizzata del servizio ospitato che deriva dalla classe base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="821ba-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="821ba-145">È possibile procedere alla creazione da zero di una classe personalizzata del servizio ospitato e implementare l'interfaccia `IHostedService`, come è necessario fare quando si usa .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="821ba-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="821ba-146">Tuttavia, poiché la maggior parte delle attività in background avrà esigenze simili per quanto riguarda la gestione dei token di annullamento e altre operazioni tipiche, è disponibile una classe di base astratta molto pratica per la derivazione, denominata `BackgroundService` a partire da .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="821ba-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="821ba-147">Tale classe esegue il lavoro principale necessario per configurare l'attività in background.</span><span class="sxs-lookup"><span data-stu-id="821ba-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="821ba-148">Il codice successivo è la classe di base astratta BackgroundService nell'implementazione di .NET Core.</span><span class="sxs-lookup"><span data-stu-id="821ba-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="821ba-149">Quando si deriva dalla classe base astratta precedente, grazie a tale implementazione ereditata, è sufficiente implementare il metodo `ExecuteAsync()` nella classe personalizzata del servizio ospitato, come illustrato di seguito nel codice semplificato da eShopOnContainers, che esegue il polling di un database e pubblica eventi di integrazione nel Bus di eventi quando necessario.</span><span class="sxs-lookup"><span data-stu-id="821ba-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="821ba-150">In questo caso specifico per eShopOnContainers, viene eseguito un metodo dell'applicazione che cerca in una tabella di database gli ordini con uno stato specifico; quando vengono applicate le modifiche, pubblica eventi di integrazione usando il bus di eventi (al di sotto di questo potrebbe usare RabbitMQ o il bus di servizio di Azure).</span><span class="sxs-lookup"><span data-stu-id="821ba-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="821ba-151">Naturalmente, è possibile eseguire in alternativa qualsiasi altra attività di business in background.</span><span class="sxs-lookup"><span data-stu-id="821ba-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="821ba-152">Per impostazione predefinita, il token di annullamento è impostato con un timeout di 5 secondi, nonostante sia possibile modificare tale valore durante la compilazione di `WebHost` usando l'estensione `UseShutdownTimeout` di `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="821ba-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="821ba-153">Ciò significa che il nostro servizio dovrebbe essere annullato entro 5 secondi; in caso contrario verrà terminato improvvisamente.</span><span class="sxs-lookup"><span data-stu-id="821ba-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="821ba-154">Il codice seguente permette di modificare tale intervallo di tempo in 10 secondi.</span><span class="sxs-lookup"><span data-stu-id="821ba-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="821ba-155">Diagramma classi di riepilogo</span><span class="sxs-lookup"><span data-stu-id="821ba-155">Summary class diagram</span></span>

<span data-ttu-id="821ba-156">Nell'immagine seguente viene illustrato un riepilogo visivo delle classi e delle interfacce necessarie per l'implementazione di IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="821ba-156">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagramma classi: IWebHost e IHost possono ospitare molti servizi, che ereditano da BackgroundService, che implementa IHostedService.](./media/image27.png)

<span data-ttu-id="821ba-158">**Figura 6-27**.</span><span class="sxs-lookup"><span data-stu-id="821ba-158">**Figure 6-27**.</span></span> <span data-ttu-id="821ba-159">Diagramma classi che mostra più classi e interfacce correlate a IHostedService</span><span class="sxs-lookup"><span data-stu-id="821ba-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="821ba-160">Considerazioni finali sulla distribuzione</span><span class="sxs-lookup"><span data-stu-id="821ba-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="821ba-161">È importante notare che la modalità di distribuzione del `WebHost` di ASP.NET Core o del `Host` di .NET Core può incidere negativamente sulla soluzione finale.</span><span class="sxs-lookup"><span data-stu-id="821ba-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="821ba-162">Ad esempio, se si distribuisce il `WebHost` in IIS o in un normale Servizio App di Azure, l'host può essere arrestato a causa di ricicli del pool di app.</span><span class="sxs-lookup"><span data-stu-id="821ba-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="821ba-163">Se invece si distribuisce l'host come contenitore in un agente di orchestrazione come Kubernetes o Service Fabric, è possibile controllare il numero garantito di istanze attive dell'host.</span><span class="sxs-lookup"><span data-stu-id="821ba-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="821ba-164">In più, è possibile considerare altri approcci nel cloud fatti apposta per questi scenari, ad esempio le Funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="821ba-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="821ba-165">Infine, se è necessario che il servizio sia sempre in esecuzione e si esegue la distribuzione in un'istanza di Windows Server, è possibile usare un servizio di Windows.</span><span class="sxs-lookup"><span data-stu-id="821ba-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="821ba-166">Ma anche per un `WebHost` distribuito in un pool di applicazioni, esistono scenari come il ripopolamento o lo scaricamento della cache in memoria dell'applicazione che sarebbero comunque applicabili.</span><span class="sxs-lookup"><span data-stu-id="821ba-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="821ba-167">L'interfaccia di `IHostedService` fornisce un modo pratico per avviare le attività in background in un'applicazione Web di ASP.NET Core (in .NET Core 2.0 ) o in qualsiasi processo/host (a partire da .NET Core 2.1 con `IHost`).</span><span class="sxs-lookup"><span data-stu-id="821ba-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="821ba-168">Il vantaggio principale è la possibilità che si ottiene con l'annullamento automatico di pulire il codice delle attività in background quando è in corso la chiusura dell'host stesso.</span><span class="sxs-lookup"><span data-stu-id="821ba-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="821ba-169">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="821ba-169">Additional resources</span></span>

- <span data-ttu-id="821ba-170">**Creare un'attività pianificata in ASP.NET Core/Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="821ba-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span>  
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="821ba-171">**Implementazione di IHostedService in ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="821ba-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span>  
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="821ba-172">**GenericHost Sample using ASP.NET Core 2.1** (Esempio di GenericHost con ASP.NET Core 2.1)</span><span class="sxs-lookup"><span data-stu-id="821ba-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span>  
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="821ba-173">[Precedente](test-aspnet-core-services-web-apps.md)
>[Successivo](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="821ba-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
