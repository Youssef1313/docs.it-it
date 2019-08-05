---
title: Implementazione del livello dell'applicazione di microservizi tramite l'API Web
description: Architettura di microservizi .NET per applicazioni .NET incluse in contenitori | Informazioni sull'inserimento di dipendenze e sugli schemi Mediator e i relativi dettagli di implementazione nel livello dell'applicazione API Web.
ms.date: 10/08/2018
ms.openlocfilehash: c8447cfcd3155a873d61ee9287f58774392c279d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676578"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="e4164-103">Implementare il livello dell'applicazione del microservizio usando l'API Web</span><span class="sxs-lookup"><span data-stu-id="e4164-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="e4164-104">Usare l'inserimento delle dipendenze per inserire oggetti dell'infrastruttura nel livello dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="e4164-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="e4164-105">Come accennato in precedenza, il livello dell'applicazione può essere implementato come parte dell'elemento (assembly) che si sta creando, ad esempio in un progetto API Web o un progetto app Web MVC.</span><span class="sxs-lookup"><span data-stu-id="e4164-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="e4164-106">Nel caso di un microservizio creato con ASP.NET Core, il livello dell'applicazione sarà in genere la libreria di API Web.</span><span class="sxs-lookup"><span data-stu-id="e4164-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="e4164-107">Per separare ciò che proviene da ASP.NET Core (l'infrastruttura più i controlli) dal codice del livello dell'applicazione personalizzato, è facoltativamente possibile inserire il livello dell'applicazione in una libreria di classi separata.</span><span class="sxs-lookup"><span data-stu-id="e4164-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="e4164-108">Il codice del livello dell'applicazione del microservizio degli ordini, ad esempio, viene direttamente implementato come parte del progetto **Ordering.API** (un progetto API Web ASP.NET Core), come illustrato nella figura 7-23.</span><span class="sxs-lookup"><span data-stu-id="e4164-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

![Visualizzazione Esplora soluzioni del microservizio Ordering.API, con le sottocartelle della cartella Applicazione visualizzate: Comportamenti, Comandi, DomainEventHandlers, IntegrationEvents, Modelli, Query e Convalide.](./media/image20.png)

<span data-ttu-id="e4164-110">**Figura 7-23**.</span><span class="sxs-lookup"><span data-stu-id="e4164-110">**Figure 7-23**.</span></span> <span data-ttu-id="e4164-111">Livello dell'applicazione nel progetto API Web ASP.NET Core Ordering.API</span><span class="sxs-lookup"><span data-stu-id="e4164-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="e4164-112">ASP.NET Core include un semplice [contenitore IoC predefinito](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (rappresentato dall'interfaccia IServiceProvider) che supporta l'inserimento del costruttore per impostazione predefinita, mentre ASP.NET rende disponibili determinati servizi tramite l'inserimento delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="e4164-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="e4164-113">In ASP.NET Core il termine *servizio* indica qualsiasi tipo registrato che verrà inserito tramite l'inserimento delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="e4164-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="e4164-114">I servizi del contenitore predefinito vengono configurati nel metodo ConfigureServices nella classe Startup dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="e4164-115">Le dipendenze vengono implementate nei servizi necessari per un tipo e registrati nel contenitore IoC.</span><span class="sxs-lookup"><span data-stu-id="e4164-115">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="e4164-116">È in genere necessario inserire dipendenze che implementano oggetti dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e4164-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="e4164-117">Un repository è un tipico esempio di dipendenza da inserire,</span><span class="sxs-lookup"><span data-stu-id="e4164-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="e4164-118">ma è possibile inserire qualsiasi altra dipendenza dell'infrastruttura disponibile.</span><span class="sxs-lookup"><span data-stu-id="e4164-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="e4164-119">Per implementazioni più semplici, è possibile inserire direttamente l'oggetto schema Unit of Work (oggetto DbContext EF), perché DBContext è anche l'implementazione degli oggetti persistenza dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e4164-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="e4164-120">Nell'esempio seguente è possibile osservare come .NET Core inserisca gli oggetti del repository necessari tramite il costruttore.</span><span class="sxs-lookup"><span data-stu-id="e4164-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="e4164-121">La classe è un gestore comando, che verrà illustrato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="e4164-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="e4164-122">La classe usa i repository inseriti per eseguire la transazione e rendere permanenti le modifiche allo stato.</span><span class="sxs-lookup"><span data-stu-id="e4164-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="e4164-123">Non è importante se tale classe è un gestore comando, un metodo del controller API Web ASP.NET Core o un [servizio dell'applicazione nella progettazione basata su domini](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="e4164-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="e4164-124">È in definitiva una semplice classe che usa repository, entità di dominio e altre funzionalità di coordinamento dell'applicazione in modo simile a un gestore comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="e4164-125">L'inserimento delle dipendenze funziona allo stesso modo per tutte le classi citate, come nell'esempio che usa l'inserimento delle dipendenze basato sul costruttore.</span><span class="sxs-lookup"><span data-stu-id="e4164-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="e4164-126">Registrare i tipi di implementazione delle dipendenze e interfacce o astrazioni</span><span class="sxs-lookup"><span data-stu-id="e4164-126">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="e4164-127">Prima di usare gli oggetti inseriti tramite i costruttori, è necessario sapere dove registrare le interfacce e le classi che generano gli oggetti inseriti nelle classi dell'applicazione tramite l'inserimento delle dipendenze,</span><span class="sxs-lookup"><span data-stu-id="e4164-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="e4164-128">come nell'inserimento delle dipendenze basato sul costruttore, come illustrato prima.</span><span class="sxs-lookup"><span data-stu-id="e4164-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="e4164-129">Usare il contenitore IoC predefinito specificato da ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e4164-129">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="e4164-130">Quando si usa il contenitore IoC predefinito fornito da ASP.NET Core, si registrano i tipi che si vuole inserire nel metodo ConfigureServices nel file Startup.cs, come nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="e4164-131">Lo schema più comune quando si registrano i tipi in un contenitore IoC prevede la registrazione di una coppia di tipi: un'interfaccia e la classe di implementazione correlata.</span><span class="sxs-lookup"><span data-stu-id="e4164-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="e4164-132">Quando dunque si richiede un oggetto dal contenitore IoC tramite un costruttore, si richiede un oggetto di un determinato tipo di interfaccia.</span><span class="sxs-lookup"><span data-stu-id="e4164-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="e4164-133">Nell'esempio precedente l'ultima riga indica che, quando uno dei costruttori ha una dipendenza da IMyCustomRepository (interfaccia o astrazione), il contenitore IoC inserirà un'istanza della classe di implementazione MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="e4164-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="e4164-134">Usare la libreria Scrutor per la registrazione automatica dei tipi</span><span class="sxs-lookup"><span data-stu-id="e4164-134">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="e4164-135">Quando si usa l'inserimento delle dipendenze in .NET Core, potrebbe essere necessario analizzare un assembly e registrarne automaticamente i tipi, per convenzione.</span><span class="sxs-lookup"><span data-stu-id="e4164-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="e4164-136">Questa funzionalità non è attualmente disponibile in ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4164-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="e4164-137">È tuttavia possibile la libreria [Scrutor](https://github.com/khellang/Scrutor) a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="e4164-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="e4164-138">Questo approccio è utile quando è necessario registrare decine di tipi nel contenitore IoC.</span><span class="sxs-lookup"><span data-stu-id="e4164-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e4164-139">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e4164-139">Additional resources</span></span>

- <span data-ttu-id="e4164-140">**Matthew King. Registrazione di servizi con Scrutor** </span><span class="sxs-lookup"><span data-stu-id="e4164-140">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="e4164-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="e4164-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="e4164-142">Repository GitHub.</span><span class="sxs-lookup"><span data-stu-id="e4164-142">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="e4164-143">Usare Autofac come contenitore IoC</span><span class="sxs-lookup"><span data-stu-id="e4164-143">Use Autofac as an IoC container</span></span>

<span data-ttu-id="e4164-144">È anche possibile usare contenitori IoC aggiuntivi e collegarli alla pipeline ASP.NET Core, come nel microservizio degli ordini in eShopOnContainers, che usa [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="e4164-144">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="e4164-145">Quando si usa Autofac, in genere si registrano i tipi tramite i moduli, che consentono di dividere i tipi di registrazioni tra più file a seconda della posizione dei tipi, proprio come si potrebbero distribuire i tipi di applicazioni in più librerie di classi.</span><span class="sxs-lookup"><span data-stu-id="e4164-145">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="e4164-146">Il seguente, ad esempio, è il [modulo dell'applicazione Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) per il progetto [API Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) con i tipi da inserire.</span><span class="sxs-lookup"><span data-stu-id="e4164-146">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="e4164-147">Autofac offre inoltre una funzionalità per [l'analisi degli assembly e la registrazione dei tipi in base alle convenzioni di denominazione](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="e4164-147">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="e4164-148">Il processo di registrazione e i relativi concetti sono molto simili al modo in cui è possibile registrare i tipi con il contenitore IoC ASP.NET Core, ma la sintassi quando si usa Autofac è leggermente diversa.</span><span class="sxs-lookup"><span data-stu-id="e4164-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="e4164-149">Nel codice di esempio l'astrazione IOrderRepository viene registrata con la classe di implementazione OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="e4164-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="e4164-150">Quando dunque un costruttore dichiara una dipendenza tramite l'astrazione o l'interfaccia IOrderRepository, il contenitore IoC inserirà un'istanza della classe OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="e4164-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="e4164-151">Il tipo di ambito di un'istanza determina come un'istanza viene condivisa tra le richieste per lo stesso servizio o dipendenza.</span><span class="sxs-lookup"><span data-stu-id="e4164-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="e4164-152">Quando viene effettuata una richiesta per una dipendenza, il contenitore IoC può restituire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e4164-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="e4164-153">Una singola istanza per ogni ambito di durata (detta *con ambito* nel contenitore IoC ASP.NET Core).</span><span class="sxs-lookup"><span data-stu-id="e4164-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="e4164-154">Una nuova istanza per ogni dipendenza (detta *temporanea* nel contenitore IoC ASP.NET Core).</span><span class="sxs-lookup"><span data-stu-id="e4164-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="e4164-155">Una singola istanza condivisa tra tutti gli oggetti tramite il contenitore IoC (detta *singleton* nel contenitore IoC ASP.NET Core).</span><span class="sxs-lookup"><span data-stu-id="e4164-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e4164-156">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e4164-156">Additional resources</span></span>

- <span data-ttu-id="e4164-157">**Introduzione all'inserimento delle dipendenze in ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e4164-157">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="e4164-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="e4164-158">**Autofac.**</span></span> <span data-ttu-id="e4164-159">Documentazione ufficiale.</span><span class="sxs-lookup"><span data-stu-id="e4164-159">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="e4164-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre** (Confronto tra la durata del servizio contenitore ASP.NET Core IoC e gli ambiti delle istanze di contenitore Autofac IoC)</span><span class="sxs-lookup"><span data-stu-id="e4164-160">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="e4164-161">Implementare gli schemi Command e Command Handler</span><span class="sxs-lookup"><span data-stu-id="e4164-161">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="e4164-162">Nell'esempio di inserimento delle dipendenze tramite costruttore illustrato nella sezione precedente il contenitore IoC ha inserito i repository tramite un costruttore in una classe.</span><span class="sxs-lookup"><span data-stu-id="e4164-162">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="e4164-163">Ma esattamente dove sono stati inseriti?</span><span class="sxs-lookup"><span data-stu-id="e4164-163">But exactly where were they injected?</span></span> <span data-ttu-id="e4164-164">In un'API Web semplice, ad esempio il microservizio catalogo in eShopOnContainers, vengono inseriti nel livello dei controller MVC, in un costruttore del controller, come parte della pipeline di richiesta di ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4164-164">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="e4164-165">Nel codice iniziale di questa sezione (la classe [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) del servizio Ordering.API in eShopOnContainers), tuttavia, l'inserimento delle dipendenze viene eseguito tramite il costruttore di un particolare gestore comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-165">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="e4164-166">Verrà ora illustrato che cos'è un gestore comando e perché usarlo.</span><span class="sxs-lookup"><span data-stu-id="e4164-166">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="e4164-167">Lo schema Command è intrinsecamente correlato allo schema CQRS illustrato prima in questa guida.</span><span class="sxs-lookup"><span data-stu-id="e4164-167">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="e4164-168">CQRS presenta due aree.</span><span class="sxs-lookup"><span data-stu-id="e4164-168">CQRS has two sides.</span></span> <span data-ttu-id="e4164-169">La prima è quella delle query, in cui si usano query semplificate con il micro ORM [Dapper](https://github.com/StackExchange/dapper-dot-net), illustrato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="e4164-169">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="e4164-170">La seconda area è quella dei comandi, ovvero il punto iniziale delle transazioni e il canale di input dall'esterno del servizio.</span><span class="sxs-lookup"><span data-stu-id="e4164-170">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="e4164-171">Come illustrato nella figura 7-24, lo schema si basa sull'accettazione dei comandi dal lato client, sulla loro elaborazione in base alle regole del modello di dominio e infine sulla persistenza degli stati con le transazioni.</span><span class="sxs-lookup"><span data-stu-id="e4164-171">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Visualizzazione di alto livello del lato operazioni di scrittura in CQRS: l'app dell'interfaccia utente invia un comando attraverso l'API che raggiunge un CommandHandler, che dipende dal modello di dominio e dall'infrastruttura per aggiornare il database.](./media/image21.png)

<span data-ttu-id="e4164-173">**Figura 7-24**.</span><span class="sxs-lookup"><span data-stu-id="e4164-173">**Figure 7-24**.</span></span> <span data-ttu-id="e4164-174">Panoramica generale dei comandi o "lato transazionale" nello schema CQRS</span><span class="sxs-lookup"><span data-stu-id="e4164-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="e4164-175">Classe di comando</span><span class="sxs-lookup"><span data-stu-id="e4164-175">The command class</span></span>

<span data-ttu-id="e4164-176">Un comando è una richiesta per il sistema di eseguire un'azione che modifica lo stato del sistema.</span><span class="sxs-lookup"><span data-stu-id="e4164-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="e4164-177">I comandi sono imperativi e devono essere elaborati una sola volta.</span><span class="sxs-lookup"><span data-stu-id="e4164-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="e4164-178">Poiché i comandi sono imperativi, in genere vengono denominati con un verbo al modo imperativo (ad esempio, "create" o "update") e possono includere il tipo di aggregazione, ad esempio CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="e4164-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="e4164-179">Diversamente da un evento, un comando non è un fatto avvenuto nel passato, ma solo una richiesta e quindi può essere rifiutato.</span><span class="sxs-lookup"><span data-stu-id="e4164-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="e4164-180">I comandi possono essere originati dall'interfaccia utente a seguito di una richiesta di un utente o da un gestore di processi quando ordina a un'aggregazione di eseguire un'azione.</span><span class="sxs-lookup"><span data-stu-id="e4164-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="e4164-181">Una caratteristica importante di un comando è che deve essere elaborato una sola volta da un singolo ricevitore.</span><span class="sxs-lookup"><span data-stu-id="e4164-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="e4164-182">Un comando è infatti una singola azione o transazione che si vuole eseguire nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="e4164-183">Lo stesso comando di creazione di un ordine, ad esempio, non deve essere elaborato più di una volta.</span><span class="sxs-lookup"><span data-stu-id="e4164-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="e4164-184">Si tratta di una differenza importante rispetto agli eventi.</span><span class="sxs-lookup"><span data-stu-id="e4164-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="e4164-185">Gli eventi possono essere elaborati più volte, perché più sistemi o microservizi possono essere interessati.</span><span class="sxs-lookup"><span data-stu-id="e4164-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="e4164-186">È anche importante che un comando venga elaborato una sola volta qualora non sia idempotente.</span><span class="sxs-lookup"><span data-stu-id="e4164-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="e4164-187">Un comando è idempotente se può essere eseguito più volte senza modificare il risultato, a causa della natura del comando o del modo in cui il sistema gestisce il comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="e4164-188">È consigliabile rendere idempotenti i comandi e gli aggiornamenti quando è opportuno per le regole business e gli invarianti del dominio.</span><span class="sxs-lookup"><span data-stu-id="e4164-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="e4164-189">Per usare lo stesso esempio, se per qualsiasi motivo (logica di ripetizione dei tentativi, intrusioni e così via) lo stesso comando CreateOrder raggiunge più volte il sistema, è consigliabile identificarlo e assicurarsi di non creare più ordini.</span><span class="sxs-lookup"><span data-stu-id="e4164-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="e4164-190">A questo scopo, è necessario associare alle operazioni qualche forma di identità e stabilire se il comando è già stato elaborato.</span><span class="sxs-lookup"><span data-stu-id="e4164-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="e4164-191">Un comando viene inviato a un singolo ricevitore e non viene pubblicato.</span><span class="sxs-lookup"><span data-stu-id="e4164-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="e4164-192">La pubblicazione è riservata agli eventi che determinano un fatto, ovvero qualcosa che è accaduto e potrebbe essere interessante per i ricevitori dell'evento.</span><span class="sxs-lookup"><span data-stu-id="e4164-192">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="e4164-193">Nel caso degli eventi, per l'entità di pubblicazione non è importante chi riceve l'evento o come lo gestisce,</span><span class="sxs-lookup"><span data-stu-id="e4164-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="e4164-194">ma gli eventi di dominio o integrazione, di cui si è già parlato nelle sezioni precedenti, sono diversi.</span><span class="sxs-lookup"><span data-stu-id="e4164-194">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="e4164-195">Un comando viene implementato con una classe contenente campi dati o raccolte con tutte le informazioni necessarie per eseguire tale comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="e4164-196">Un comando è un particolare tipo di DTO (Data Transfer Object), usato in modo specifico per richiedere modifiche o transazioni.</span><span class="sxs-lookup"><span data-stu-id="e4164-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="e4164-197">Il comando in sé si basa esclusivamente sulle informazioni necessarie per elaborare il comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="e4164-198">L'esempio seguente illustra la classe CreateOrderCommand semplificata.</span><span class="sxs-lookup"><span data-stu-id="e4164-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="e4164-199">Si tratta di un comando non modificabile usato nel microservizio degli ordini in eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e4164-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="e4164-200">In sostanza, la classe del comando contiene tutti i dati necessari per eseguire una transazione aziendale usando gli oggetti modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e4164-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="e4164-201">I comandi quindi sono semplicemente strutture dei dati contenenti dati di sola lettura e nessun comportamento.</span><span class="sxs-lookup"><span data-stu-id="e4164-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="e4164-202">Il nome del comando ne indica lo scopo.</span><span class="sxs-lookup"><span data-stu-id="e4164-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="e4164-203">In numerosi linguaggi, come C#, i comandi sono rappresentati come classi, ma non si tratta di vere e proprie classi nel senso degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="e4164-203">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="e4164-204">Un'altra caratteristica dei comandi è di non essere modificabili, perché l'utilizzo previsto è che vengano elaborati direttamente dal modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e4164-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="e4164-205">Non è necessario modificarli nell'arco della durata prevista.</span><span class="sxs-lookup"><span data-stu-id="e4164-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="e4164-206">In una classe C# l'immutabilità può essere ottenuta anche senza setter o altri metodi che modificano lo stato interno.</span><span class="sxs-lookup"><span data-stu-id="e4164-206">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="e4164-207">Tenere presente che se si intende o si prevede che i comandi vengano sottoposti a un processo di serializzazione/deserializzazione, le proprietà devono avere un setter privato e l'attributo `[DataMember]` (o `[JsonProperty]`), altrimenti il deserializzatore non sarà in grado di ricostruire l'oggetto nella destinazione con i valori richiesti.</span><span class="sxs-lookup"><span data-stu-id="e4164-207">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="e4164-208">Ad esempio, la classe del comando per la creazione di un ordine è probabilmente simile, in termini di dati, all'ordine che si vuole creare, ma è altrettanto probabile che non siano necessari gli stessi attributi.</span><span class="sxs-lookup"><span data-stu-id="e4164-208">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="e4164-209">CreateOrderCommand, ad esempio, non ha un ID ordine, perché l'ordine non è ancora stato creato.</span><span class="sxs-lookup"><span data-stu-id="e4164-209">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="e4164-210">Molte classi di comandi possono essere semplici e richiedere solo alcuni campi per gli stati che devono essere modificati,</span><span class="sxs-lookup"><span data-stu-id="e4164-210">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="e4164-211">ad esempio quando si deve solo modificare lo stato di un ordine da "in corso" a "pagato" o "spedito" usando un comando simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-211">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="e4164-212">Alcuni sviluppatori preferiscono tenere gli oggetti richiesta dell'interfaccia utente separati dagli oggetti DTO dei comandi, anche se non è necessario.</span><span class="sxs-lookup"><span data-stu-id="e4164-212">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="e4164-213">Si tratta di una separazione noiosa, non particolarmente utile, e la forma degli oggetti è quasi esattamente la stessa.</span><span class="sxs-lookup"><span data-stu-id="e4164-213">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="e4164-214">In eShopOnContainers, ad esempio, alcuni comandi provengono direttamente dal lato client.</span><span class="sxs-lookup"><span data-stu-id="e4164-214">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="e4164-215">Classe del gestore comando</span><span class="sxs-lookup"><span data-stu-id="e4164-215">The Command Handler class</span></span>

<span data-ttu-id="e4164-216">È consigliabile implementare una classe di gestore comando specifica per ogni comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-216">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="e4164-217">In tale classe, che è alla base del funzionamento dello schema, si useranno l'oggetto comando, gli oggetti dominio e gli oggetti del repository dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e4164-217">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="e4164-218">Il gestore comando è di fatto il cuore del livello dell'applicazione in termini di CQRS e progettazione basata su domini.</span><span class="sxs-lookup"><span data-stu-id="e4164-218">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="e4164-219">Tutta la logica del dominio deve tuttavia essere contenuta nelle classi di dominio, ovvero le radici di aggregazione (entità radice), le entità figlio o i [servizi di dominio](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ma non nel gestore comando, che è una classe del livello dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-219">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="e4164-220">La classe del gestore comandi offre un efficace trampolino di lancio per il modo in cui si ottiene il principio di singola responsabilità (SRP, Single Responsibility Principle) menzionato in una sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="e4164-220">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="e4164-221">Un gestore comando riceve un comando e ottiene un risultato dall'aggregazione usata.</span><span class="sxs-lookup"><span data-stu-id="e4164-221">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="e4164-222">Il risultato deve essere la corretta esecuzione del comando o un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="e4164-222">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="e4164-223">Se è un'eccezione, lo stato del sistema non dovrebbe risultare modificato.</span><span class="sxs-lookup"><span data-stu-id="e4164-223">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="e4164-224">Il gestore comando in genere esegue questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="e4164-224">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="e4164-225">Riceve l'oggetto comando, ad esempio un DTO (dal [Mediator](https://en.wikipedia.org/wiki/Mediator_pattern) o da un altro oggetto dell'infrastruttura).</span><span class="sxs-lookup"><span data-stu-id="e4164-225">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="e4164-226">Verifica che il comando sia valido (se non viene convalidato dal Mediator).</span><span class="sxs-lookup"><span data-stu-id="e4164-226">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="e4164-227">Crea un'istanza della radice di aggregazione che è la destinazione del comando corrente.</span><span class="sxs-lookup"><span data-stu-id="e4164-227">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="e4164-228">Esegue il metodo sull'istanza della radice di aggregazione, ottenendo dal comando i dati necessari.</span><span class="sxs-lookup"><span data-stu-id="e4164-228">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="e4164-229">Rende permanente il nuovo stato dell'aggregazione nel database correlato.</span><span class="sxs-lookup"><span data-stu-id="e4164-229">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="e4164-230">Quest'ultima operazione è la transazione vera e propria.</span><span class="sxs-lookup"><span data-stu-id="e4164-230">This last operation is the actual transaction.</span></span>

<span data-ttu-id="e4164-231">Un gestore comando in genere si occupa di una singola aggregazione basata sulla radice di aggregazione (entità radice).</span><span class="sxs-lookup"><span data-stu-id="e4164-231">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="e4164-232">Se più aggregazioni devono essere interessate dalla ricezione di un singolo comando, è possibile usare gli eventi di dominio per propagare gli stati o le azioni in più aggregazioni.</span><span class="sxs-lookup"><span data-stu-id="e4164-232">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="e4164-233">L'importante in questo caso è che, quando un comando viene elaborato, tutta la logica di dominio deve essere nel modello di dominio (le aggregazioni), completamente incapsulata e pronta per il testing unità.</span><span class="sxs-lookup"><span data-stu-id="e4164-233">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="e4164-234">Il gestore comando è solo un modo per ottenere il modello di dominio dal database e, come passaggio finale, per indicare al livello infrastruttura (repository) di rendere permanenti le modifiche quando il modello viene modificato.</span><span class="sxs-lookup"><span data-stu-id="e4164-234">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="e4164-235">Il vantaggio di questo approccio è che è possibile effettuare il refactoring della logica di dominio in un modello di dominio avanzato, completamente incapsulato e isolato senza modificare il codice nei livelli infrastruttura o applicazione, che costituiscono il livello di plumbing (gestori comando, API Web, repository e così via).</span><span class="sxs-lookup"><span data-stu-id="e4164-235">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="e4164-236">Quando i gestori comando sono complessi, con una logica eccessiva, può trattarsi di code smell.</span><span class="sxs-lookup"><span data-stu-id="e4164-236">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="e4164-237">Esaminarli e, se si trova la logica di dominio, effettuare il refactoring del codice per spostare tale comportamento del dominio nei metodi degli oggetti dominio (la radice di aggregazione e l'entità figlio).</span><span class="sxs-lookup"><span data-stu-id="e4164-237">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="e4164-238">Come esempio di classe di gestore comando, il codice seguente illustra la stessa classe CreateOrderCommandHandler vista all'inizio di questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="e4164-238">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="e4164-239">In questo caso, sono in evidenza il metodo Handle e le operazioni con gli oggetti o le aggregazioni del modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e4164-239">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="e4164-240">I seguenti sono passaggi aggiuntivi che devono essere eseguiti da un gestore comando:</span><span class="sxs-lookup"><span data-stu-id="e4164-240">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="e4164-241">Usare i dati del comando per operare con i metodi e il comportamento della radice di aggregazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-241">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="e4164-242">All'interno degli oggetti dominio, generare eventi di dominio mentre la transazione è in esecuzione, ma trasparente dal punto di vista del gestore comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-242">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="e4164-243">Se il risultato dell'operazione di aggregazione è positivo e dopo che la transazione è stata completata, generare gli eventi di integrazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-243">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="e4164-244">che potrebbe anche essere generato dalle classi dell'infrastruttura, ad esempio i repository.</span><span class="sxs-lookup"><span data-stu-id="e4164-244">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e4164-245">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e4164-245">Additional resources</span></span>

- <span data-ttu-id="e4164-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \ (In corrispondenza dei limiti, le applicazioni non sono orientate a oggetti)</span><span class="sxs-lookup"><span data-stu-id="e4164-246">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** \</span></span>
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="e4164-247">**Comandi ed eventi** </span><span class="sxs-lookup"><span data-stu-id="e4164-247">**Commands and events** </span></span>\
  <http://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="e4164-248">**What does a command handler do?** (Qual è la funzione di un gestore comandi?)</span><span class="sxs-lookup"><span data-stu-id="e4164-248">**What does a command handler do?**</span></span> \
  <http://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="e4164-249">**Jimmy Bogard. Domain Command Patterns - Handlers** \ (Modelli di comando di dominio - Gestori)</span><span class="sxs-lookup"><span data-stu-id="e4164-249">**Jimmy Bogard. Domain Command Patterns – Handlers** \</span></span>
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="e4164-250">**Jimmy Bogard. Domain Command Patterns - Validation** \ (Modelli di comando di dominio - Convalida)</span><span class="sxs-lookup"><span data-stu-id="e4164-250">**Jimmy Bogard. Domain Command Patterns – Validation** \</span></span>
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="e4164-251">Pipeline di elaborazione del comando: come attivare un gestore comando</span><span class="sxs-lookup"><span data-stu-id="e4164-251">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="e4164-252">La domanda successiva è come richiamare un gestore comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-252">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="e4164-253">È possibile chiamarlo manualmente da ogni controller ASP.NET Core correlato.</span><span class="sxs-lookup"><span data-stu-id="e4164-253">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="e4164-254">Tale approccio sarebbe tuttavia troppo vincolante e non è l'ideale.</span><span class="sxs-lookup"><span data-stu-id="e4164-254">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="e4164-255">Le altre due principali opzioni, che sono quelle consigliate, sono:</span><span class="sxs-lookup"><span data-stu-id="e4164-255">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="e4164-256">Tramite un elemento schema Mediator in memoria.</span><span class="sxs-lookup"><span data-stu-id="e4164-256">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="e4164-257">Con una coda di messaggi asincroni, tra i controller e i gestori.</span><span class="sxs-lookup"><span data-stu-id="e4164-257">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="e4164-258">Usare lo schema Mediator (in memoria) nella pipeline del comando</span><span class="sxs-lookup"><span data-stu-id="e4164-258">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="e4164-259">Come illustrato nella figura 7-25, in un approccio CQRS si usa un Mediator intelligente, simile a un bus in memoria, in grado di eseguire il reindirizzamento al gestore comandi appropriato in base al tipo di comando o DTO che viene ricevuto.</span><span class="sxs-lookup"><span data-stu-id="e4164-259">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="e4164-260">Le singole frecce nere tra i componenti rappresentano le dipendenze tra gli oggetti (in molti casi inseriti tramite inserimento delle dipendenze) con le interazioni correlate.</span><span class="sxs-lookup"><span data-stu-id="e4164-260">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Zoom avanti dall'immagine precedente: il controller ASP.NET Core invia il comando alla pipeline del comando di MediatR in modo che arrivi al gestore appropriato.](./media/image22.png)

<span data-ttu-id="e4164-262">**Figura 7-25**.</span><span class="sxs-lookup"><span data-stu-id="e4164-262">**Figure 7-25**.</span></span> <span data-ttu-id="e4164-263">Uso dello schema Mediator in esecuzione in un singolo microservizio CQRS</span><span class="sxs-lookup"><span data-stu-id="e4164-263">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="e4164-264">L'uso dello schema Mediator è sensato perché nelle applicazioni aziendali l'elaborazione delle richieste può essere complessa.</span><span class="sxs-lookup"><span data-stu-id="e4164-264">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="e4164-265">Potrebbe essere necessario aggiungere un numero indeterminato di problematiche trasversali, ad esempio registrazione, convalide, controllo e sicurezza.</span><span class="sxs-lookup"><span data-stu-id="e4164-265">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="e4164-266">In questi casi, è possibile affidarsi a una pipeline di Mediator (vedere [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) per fornire un mezzo per gestire questi comportamenti o problematiche trasversali aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="e4164-266">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="e4164-267">Un Mediator è un oggetto che incapsula la modalità di questo processo: coordina l'esecuzione in base a uno stato, il modo in cui un gestore comando viene richiamato o il payload fornito al gestore.</span><span class="sxs-lookup"><span data-stu-id="e4164-267">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="e4164-268">Con un componente Mediator è possibile applicare le problematiche trasversali in modo centralizzato e trasparente applicando gli elementi Decorator (o [comportamenti della pipeline](https://github.com/jbogard/MediatR/wiki/Behaviors) da [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="e4164-268">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="e4164-269">Per altre informazioni, vedere lo [schema Decorator](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="e4164-269">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="e4164-270">Gli elementi Decorator e i comportamenti sono simili alla [programmazione orientata agli aspetti](https://en.wikipedia.org/wiki/Aspect-oriented_programming), che viene applicata solo a una pipeline di processi specifica gestita dal componente Mediator.</span><span class="sxs-lookup"><span data-stu-id="e4164-270">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="e4164-271">Gli aspetti nella programmazione orientata agli aspetti, che implementano i problemi trasversali, vengono applicati in base ai *weaver degli aspetti* inseriti in fase di compilazione o in base all'intercettazione della chiamata all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="e4164-271">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="e4164-272">Si dice a volte che entrambi i tipici approcci alla programmazione orientata agli aspetti "fanno magie", perché non è facile vedere come funziona la programmazione orientata agli aspetti.</span><span class="sxs-lookup"><span data-stu-id="e4164-272">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="e4164-273">Quando si affrontano problemi o bug gravi, può essere difficile eseguire il debug della programmazione orientata agli aspetti.</span><span class="sxs-lookup"><span data-stu-id="e4164-273">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="e4164-274">D'altra parte, questi elementi Decorator/comportamenti sono espliciti e vengono applicati solo nel contesto del Mediator, quindi il debug è molto più prevedibile e semplice.</span><span class="sxs-lookup"><span data-stu-id="e4164-274">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="e4164-275">Nel microservizio degli ordini di eShopOnContainers vengono implementati due comportamenti di esempio, una classe [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) e una classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs).</span><span class="sxs-lookup"><span data-stu-id="e4164-275">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="e4164-276">L'implementazione dei comportamenti viene illustrata nella sezione successiva spiegando in che modo eShopOnContainers implementa i [comportamenti](https://github.com/jbogard/MediatR/wiki/Behaviors) di [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0).</span><span class="sxs-lookup"><span data-stu-id="e4164-276">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="e4164-277">Usare le code di messaggi (out-of-process) nella pipeline del comando</span><span class="sxs-lookup"><span data-stu-id="e4164-277">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="e4164-278">È anche possibile usare i messaggi asincroni basati su broker o code di messaggi, come illustrato nella figura 7-26.</span><span class="sxs-lookup"><span data-stu-id="e4164-278">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="e4164-279">Questa opzione può anche essere combinata con il componente Mediator subito prima del gestore comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-279">That option could also be combined with the mediator component right before the command handler.</span></span>

![La pipeline del comando può essere gestita anche da una coda di messaggi a disponibilità elevata per recapitare i comandi al gestore appropriato.](./media/image23.png)

<span data-ttu-id="e4164-281">**Figura 7-26**.</span><span class="sxs-lookup"><span data-stu-id="e4164-281">**Figure 7-26**.</span></span> <span data-ttu-id="e4164-282">Uso delle code di messaggi (comunicazione out-of-process e interprocesso) con i comandi CQRS</span><span class="sxs-lookup"><span data-stu-id="e4164-282">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="e4164-283">L'uso di code di messaggi per accettare i comandi può rendere ancora più complessa la pipeline del comando, perché probabilmente sarà necessario dividere la pipeline in due processi connessi tramite la coda di messaggi esterna.</span><span class="sxs-lookup"><span data-stu-id="e4164-283">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="e4164-284">È consigliabile servirsene se è necessario migliorare la scalabilità e le prestazioni in base alla messaggistica asincrona.</span><span class="sxs-lookup"><span data-stu-id="e4164-284">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="e4164-285">Si consideri che, nel caso della figura 7-26, il controller inserisce solo il messaggio di comando nella coda e torna indietro.</span><span class="sxs-lookup"><span data-stu-id="e4164-285">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="e4164-286">I gestori comando elaborano quindi i messaggi alla velocità stabilita.</span><span class="sxs-lookup"><span data-stu-id="e4164-286">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="e4164-287">Ecco un vantaggio considerevole delle code: la coda di messaggi può fungere da buffer nei casi in cui è necessaria l'iperscalabilità, ad esempio per le quotazioni di borsa o altri scenari con un volume elevato di dati in ingresso.</span><span class="sxs-lookup"><span data-stu-id="e4164-287">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="e4164-288">A causa della natura asincrona delle code di messaggi, è tuttavia necessario capire come comunicare all'applicazione client l'esito positivo o negativo dell'elaborazione del comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-288">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="e4164-289">Di norma, è preferibile non usare mai i comandi di tipo "fire and forget".</span><span class="sxs-lookup"><span data-stu-id="e4164-289">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="e4164-290">Ogni applicazione aziendale deve sapere se un comando è stato elaborato correttamente o quanto meno convalidato e accettato.</span><span class="sxs-lookup"><span data-stu-id="e4164-290">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="e4164-291">Poter rispondere al client dopo la convalida di un messaggio di comando inviato a una coda asincrona accresce quindi la complessità del sistema, rispetto a un'elaborazione di comando in-process che restituisce il risultato dell'operazione dopo l'esecuzione della transazione.</span><span class="sxs-lookup"><span data-stu-id="e4164-291">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="e4164-292">Usando le code, potrebbe essere necessario restituire il risultato dell'elaborazione del comando tramite altri messaggi sul risultato dell'operazione, per cui saranno richiesti componenti aggiuntivi e una comunicazione personalizzata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="e4164-292">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="e4164-293">Inoltre, i comandi asincroni sono comandi unidirezionali, che in molti casi potrebbero non essere necessari, come illustrato dall'interessante scambio seguente tra Burtsev Alexey e Greg Young nell'ambito di una [conversazione online](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="e4164-293">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="e4164-294">\[Burtsev Alexey\] Trovo una gran quantità di codice dove le persone usano la gestione dei comandi asincroni o la messaggistica basata su comandi unidirezionali senza alcun motivo per farlo (non devono eseguire operazioni lunghe, non devono eseguire codice asincrono esterno, non devono neppure attraversare il limite dell'applicazione per usare il bus di messaggi).</span><span class="sxs-lookup"><span data-stu-id="e4164-294">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="e4164-295">Perché rendono tutto così complesso senza motivo?</span><span class="sxs-lookup"><span data-stu-id="e4164-295">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="e4164-296">E finora non ho visto un solo esempio di codice CQRS con il blocco dei gestori comando, anche se funzionerebbe davvero bene nella maggior parte dei casi.</span><span class="sxs-lookup"><span data-stu-id="e4164-296">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="e4164-297">\[Greg Young\] \[...\] non esiste un comando asincrono, che è in realtà un altro evento.</span><span class="sxs-lookup"><span data-stu-id="e4164-297">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="e4164-298">Se devo accettare quello che tu mi invii e generare un evento se non sono d'accordo, non mi stai più dicendo di fare qualcosa \[quindi, non è un comando\].</span><span class="sxs-lookup"><span data-stu-id="e4164-298">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="e4164-299">Mi stai dicendo che qualcosa è stato fatto.</span><span class="sxs-lookup"><span data-stu-id="e4164-299">It's you telling me something has been done.</span></span> <span data-ttu-id="e4164-300">A prima vista, sembra una piccola differenza, ma le implicazioni sono molte.</span><span class="sxs-lookup"><span data-stu-id="e4164-300">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="e4164-301">I comandi asincroni accrescono considerevolmente la complessità di un sistema, perché non esiste un modo semplice per indicare gli errori.</span><span class="sxs-lookup"><span data-stu-id="e4164-301">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="e4164-302">I comandi asincroni non sono quindi consigliati se non quando sono necessari requisiti di ridimensionamento o in casi particolari quando si comunicano i microservizi interni tramite la messaggistica.</span><span class="sxs-lookup"><span data-stu-id="e4164-302">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="e4164-303">In tali casi, è necessario progettare un sistema di segnalazione e ripristino separato per gli errori.</span><span class="sxs-lookup"><span data-stu-id="e4164-303">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="e4164-304">Nella versione iniziale di eShopOnContainers è stato deciso di usare l'elaborazione dei comandi sincroni, avviata dalle richieste HTTP e gestita dallo schema Mediator.</span><span class="sxs-lookup"><span data-stu-id="e4164-304">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="e4164-305">In questo modo è possibile restituire facilmente l'esito positivo o negativo del processo, come nell'implementazione [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="e4164-305">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="e4164-306">In ogni caso, la decisione deve essere presa in base ai requisiti aziendali dell'applicazione o del microservizio.</span><span class="sxs-lookup"><span data-stu-id="e4164-306">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="e4164-307">Implementare la pipeline di elaborazione del comando con uno schema Mediator (MediatR)</span><span class="sxs-lookup"><span data-stu-id="e4164-307">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="e4164-308">Come implementazione di esempio, questa guida propone l'uso della pipeline in-process basata sullo schema Mediator per gestire l'inserimento dei comandi e instradare i comandi, in memoria, ai gestori comando appropriati.</span><span class="sxs-lookup"><span data-stu-id="e4164-308">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="e4164-309">La guida propone anche l'applicazione di [comportamenti](https://github.com/jbogard/MediatR/wiki/Behaviors) per separare le problematiche trasversali.</span><span class="sxs-lookup"><span data-stu-id="e4164-309">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="e4164-310">Per l'implementazione in .NET Core, sono disponibili più librerie open source che implementano lo schema Mediator.</span><span class="sxs-lookup"><span data-stu-id="e4164-310">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="e4164-311">Quella usata in questa guida è la libreria open source [MediatR](https://github.com/jbogard/MediatR) (creata da Jimmy Bogard), ma è possibile adottare un altro approccio.</span><span class="sxs-lookup"><span data-stu-id="e4164-311">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="e4164-312">MediatR è una libreria semplice di piccole dimensioni che consente di elaborare messaggi in memoria, ad esempio un comando, applicando al contempo elementi Decorator o comportamenti.</span><span class="sxs-lookup"><span data-stu-id="e4164-312">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="e4164-313">L'uso dello schema Mediator consente di ridurre l'accoppiamento e di isolare le problematiche del lavoro richiesto, connettendosi automaticamente nello stesso tempo al gestore che esegue tale lavoro, in questo caso ai gestori comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-313">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="e4164-314">Un altro valido motivo per usare lo schema Mediator è stato illustrato da Jimmy durante la revisione di questa guida:</span><span class="sxs-lookup"><span data-stu-id="e4164-314">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="e4164-315">Penso che qui valga la pena parlare dei test, che offrono un quadro coerente del comportamento del sistema.</span><span class="sxs-lookup"><span data-stu-id="e4164-315">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="e4164-316">Richiesta in ingresso, risposta in uscita. Questo aspetto è risultato piuttosto utile nella creazione di test dal comportamento coerente.</span><span class="sxs-lookup"><span data-stu-id="e4164-316">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="e4164-317">Verrà prima di tutto esaminato un controller API Web di esempio, in cui è effettivamente possibile usare l'oggetto Mediator.</span><span class="sxs-lookup"><span data-stu-id="e4164-317">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="e4164-318">Se non si usasse l'oggetto Mediator, sarebbe necessario inserire tutte le dipendenze per tale controller, ad esempio un oggetto logger e altri.</span><span class="sxs-lookup"><span data-stu-id="e4164-318">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="e4164-319">Il costruttore sarebbe quindi piuttosto complesso.</span><span class="sxs-lookup"><span data-stu-id="e4164-319">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="e4164-320">D'altra parte, se si usa l'oggetto Mediator, il costruttore del controller può essere molto più semplice, con solo alcune dipendenze invece di molte se ne fosse presente una per ogni operazione trasversale, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-320">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="e4164-321">Si può osservare che il Mediator fornisce un controller API Web essenziale.</span><span class="sxs-lookup"><span data-stu-id="e4164-321">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="e4164-322">Inoltre, nei metodi del controller, il codice per inviare un comando all'oggetto Mediator è praticamente di una sola riga:</span><span class="sxs-lookup"><span data-stu-id="e4164-322">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="e4164-323">Implementare i comandi idempotenti</span><span class="sxs-lookup"><span data-stu-id="e4164-323">Implement idempotent Commands</span></span>

<span data-ttu-id="e4164-324">In **eShopOnContainers** un esempio più avanzato di quello precedente prevede l'invio di un oggetto CreateOrderCommand dal microservizio degli ordini.</span><span class="sxs-lookup"><span data-stu-id="e4164-324">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="e4164-325">Poiché tuttavia il processo aziendale degli ordini è un po' più complesso e, in questo caso, inizia di fatto con il microservizio Basket, l'azione di invio dell'oggetto CreateOrderCommand viene eseguita da un gestore eventi di integrazione denominato >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) anziché da un semplice controller API Web chiamato dall'app client come nel più semplice esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="e4164-325">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="e4164-326">L'azione di invio del comando a MediatR è però molto simile, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="e4164-326">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="e4164-327">Questo caso è tuttavia anche un po' più avanzato perché vengono anche implementati comandi idempotenti.</span><span class="sxs-lookup"><span data-stu-id="e4164-327">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="e4164-328">Il processo CreateOrderCommand dovrebbe essere idempotente, quindi, se per qualsiasi motivo lo stesso messaggio viene duplicato in rete, ad esempio a causa di più tentativi, lo stesso ordine aziendale verrà elaborato più di una volta.</span><span class="sxs-lookup"><span data-stu-id="e4164-328">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="e4164-329">Per l'implementazione viene eseguito il wrapping del comando aziendale (in questo caso CreateOrderCommand), che viene quindi incorporato in un generico IdentifiedCommand di cui viene tenuta traccia usando un ID di ogni messaggio in arrivo dalla rete che deve essere idempotente.</span><span class="sxs-lookup"><span data-stu-id="e4164-329">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="e4164-330">Nel codice seguente è possibile osservare che IdentifiedCommand è semplicemente un oggetto DTO con un ID e l'oggetto comando aziendale di cui viene eseguito il wrapping.</span><span class="sxs-lookup"><span data-stu-id="e4164-330">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="e4164-331">Quindi l'elemento CommandHandler per l'elemento IdentifiedCommand denominato [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) fondamentalmente controllerà se l'ID immesso come parte del messaggio esiste già in una tabella.</span><span class="sxs-lookup"><span data-stu-id="e4164-331">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="e4164-332">Se esiste già, tale comando non verrà elaborato di nuovo, quindi si comporta come un comando idempotente.</span><span class="sxs-lookup"><span data-stu-id="e4164-332">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="e4164-333">Tale codice dell'infrastruttura viene eseguito dalla chiamata al metodo `_requestManager.ExistAsync` seguente.</span><span class="sxs-lookup"><span data-stu-id="e4164-333">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="e4164-334">Poiché IdentifiedCommand funge da busta del comando aziendale, quando il comando aziendale deve essere elaborato perché non è un ID ripetuto, prende tale comando aziendale interno e lo invia di nuovo al Mediator, come nell'ultima parte del codice illustrato sopra quando si esegue `_mediator.Send(message.Command)`, da [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="e4164-334">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="e4164-335">Durante tale operazione, collegherà ed eseguirà il gestore comando aziendale, in questo caso [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), che sta eseguendo le transazioni nel database degli ordini, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="e4164-335">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="e4164-336">Registrare i tipi usati da MediatR</span><span class="sxs-lookup"><span data-stu-id="e4164-336">Register the types used by MediatR</span></span>

<span data-ttu-id="e4164-337">Per consentire a MediatR di conoscere le classi di gestori comando, è necessario registrare le classi Mediator e le classi di gestori comando nel contenitore IoC.</span><span class="sxs-lookup"><span data-stu-id="e4164-337">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="e4164-338">Per impostazione predefinita, MediatR usa Autofac come contenitore IoC, ma è anche possibile usare il contenitore IoC ASP.NET Core predefinito o qualsiasi altro contenitore supportato da MediatR.</span><span class="sxs-lookup"><span data-stu-id="e4164-338">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="e4164-339">Il codice seguente illustra come registrare i tipi e i comandi di Mediator quando si usano i moduli di Autofac.</span><span class="sxs-lookup"><span data-stu-id="e4164-339">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="e4164-340">È qui che "avviene la vera e propria magia" con MediatR.</span><span class="sxs-lookup"><span data-stu-id="e4164-340">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="e4164-341">Poiché ogni gestore comandi implementa l'interfaccia `IAsyncRequestHandler<T>` generica, quando si registrano gli assembly, il codice registra con `RegisteredAssemblyTypes` tutti i tipi contrassegnati come `IAsyncRequestHandler` mentre correla gli elementi `CommandHandlers` con i rispettivi `Commands`, grazie alla relazione stabilita nella classe `CommandHandler`, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-341">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="e4164-342">Questo è il codice che correla i comandi con i gestori comando.</span><span class="sxs-lookup"><span data-stu-id="e4164-342">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="e4164-343">Il gestore è solo una semplice classe, ma eredita da `RequestHandler<T>`, dove T è il tipo di comando, e MediatR verifica che venga richiamato con il payload corretto (il comando).</span><span class="sxs-lookup"><span data-stu-id="e4164-343">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="e4164-344">Applicare problematiche trasversali quando si elaborano i comandi con i comportamenti in MediatR</span><span class="sxs-lookup"><span data-stu-id="e4164-344">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="e4164-345">Un aspetto da considerare è la possibilità di applicare problematiche trasversali alla pipeline Mediator.</span><span class="sxs-lookup"><span data-stu-id="e4164-345">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="e4164-346">È anche possibile osservare alla fine del codice del modulo di registrazione di Autofac come registra un tipo di comportamento, in particolare una classe LoggingBehavior personalizzata e una classe ValidatorBehavior,</span><span class="sxs-lookup"><span data-stu-id="e4164-346">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="e4164-347">ma è anche possibile aggiungere altri comportamenti personalizzati.</span><span class="sxs-lookup"><span data-stu-id="e4164-347">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="e4164-348">Tale classe [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) può essere implementata come il codice seguente, che registra le informazioni sul gestore comando che viene eseguito e l'esito positivo o negativo.</span><span class="sxs-lookup"><span data-stu-id="e4164-348">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="e4164-349">Semplicemente implementando questa classe di comportamento e registrandola nella pipeline (nell'oggetto MediatorModule di cui sopra), tutti i comandi elaborati con MediatR registreranno le informazioni sull'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e4164-349">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="e4164-350">Il microservizio degli ordini di eShopOnContainers applica anche un secondo comportamento per le convalide di base, la classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) che si basa sulla libreria [FluentValidation](https://github.com/JeremySkinner/FluentValidation), come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-350">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="e4164-351">In questo caso il comportamento genera un'eccezione se la convalida non riesce, ma è anche possibile restituire un oggetto risultato che contiene il risultato del comando se ha avuto esito positivo o i messaggi di convalida nel caso contrario.</span><span class="sxs-lookup"><span data-stu-id="e4164-351">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="e4164-352">Questo probabilmente semplificherebbe la visualizzazione dei risultati della convalida per l'utente.</span><span class="sxs-lookup"><span data-stu-id="e4164-352">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="e4164-353">Quindi in base alla libreria [FluentValidation](https://github.com/JeremySkinner/FluentValidation), è stata creata una convalida per i dati passati con CreateOrderCommand, come nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="e4164-353">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="e4164-354">È possibile creare convalide aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="e4164-354">You could create additional validations.</span></span> <span data-ttu-id="e4164-355">È un modo molto essenziale e accurato di implementare le convalide dei comandi.</span><span class="sxs-lookup"><span data-stu-id="e4164-355">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="e4164-356">In modo simile, è possibile implementare altri comportamenti per ulteriori aspetti o problematiche trasversali che si vuole applicare ai comandi quando li si gestisce.</span><span class="sxs-lookup"><span data-stu-id="e4164-356">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e4164-357">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e4164-357">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="e4164-358">Schema Mediator</span><span class="sxs-lookup"><span data-stu-id="e4164-358">The mediator pattern</span></span>

- <span data-ttu-id="e4164-359">**Schema Mediator** </span><span class="sxs-lookup"><span data-stu-id="e4164-359">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="e4164-360">Schema Decorator</span><span class="sxs-lookup"><span data-stu-id="e4164-360">The decorator pattern</span></span>

- <span data-ttu-id="e4164-361">**Schema Decorator** </span><span class="sxs-lookup"><span data-stu-id="e4164-361">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="e4164-362">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="e4164-362">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="e4164-363">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="e4164-363">**MediatR.**</span></span> <span data-ttu-id="e4164-364">Repository GitHub.</span><span class="sxs-lookup"><span data-stu-id="e4164-364">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="e4164-365">**CQRS with MediatR and AutoMapper** \ (CQRS con MediatR e AutoMapper)</span><span class="sxs-lookup"><span data-stu-id="e4164-365">**CQRS with MediatR and AutoMapper** \</span></span>
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="e4164-366">**Put your controllers on a diet: POSTs and commands.** (Mettere a dieta i controller: POST e comandi)</span><span class="sxs-lookup"><span data-stu-id="e4164-366">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="e4164-367">**Tackling cross-cutting concerns with a mediator pipeline** \ (Affrontare i problemi di montaggio incrociato con una pipeline MediatR)</span><span class="sxs-lookup"><span data-stu-id="e4164-367">**Tackling cross-cutting concerns with a mediator pipeline** \</span></span>
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="e4164-368">**CQRS and REST: the perfect match** \ (CQRS e REST: la coppia perfetta)</span><span class="sxs-lookup"><span data-stu-id="e4164-368">**CQRS and REST: the perfect match** \</span></span>
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="e4164-369">**MediatR Pipeline Examples** \ (Esempi di pipeline MediatR)</span><span class="sxs-lookup"><span data-stu-id="e4164-369">**MediatR Pipeline Examples** \</span></span>
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="e4164-370">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \ (Fixture di test per sezioni verticali per MediatR e ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="e4164-370">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** \</span></span>
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="e4164-371">**MediatR Extensions for Microsoft Dependency Injection Released** \ (Rilascio delle estensioni MediatR per l'inserimento di dipendenze Microsoft)</span><span class="sxs-lookup"><span data-stu-id="e4164-371">**MediatR Extensions for Microsoft Dependency Injection Released** \</span></span>
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="e4164-372">Convalida Fuent</span><span class="sxs-lookup"><span data-stu-id="e4164-372">Fluent validation</span></span>

- <span data-ttu-id="e4164-373">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="e4164-373">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="e4164-374">Repository GitHub.</span><span class="sxs-lookup"><span data-stu-id="e4164-374">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="e4164-375">[Precedente](microservice-application-layer-web-api-design.md)
> [Successivo](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e4164-375">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
