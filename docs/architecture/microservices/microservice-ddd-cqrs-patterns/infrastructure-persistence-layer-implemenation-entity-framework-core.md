---
title: Implementazione del livello di persistenza dell'infrastruttura con Entity Framework Core
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Esplorare i dettagli di implementazione per il livello di persistenza dell'infrastruttura con Entity Framework Core.
ms.date: 10/08/2018
ms.openlocfilehash: 7e3480999b115ac13f8d7ebcaed826b407aa7637
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674098"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="a1488-103">Implementare il livello di persistenza dell'infrastruttura con Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a1488-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="a1488-104">Quando si usano database relazionali come SQL Server, Oracle o PostgreSQL, uno degli approcci consigliati consiste nell'implementare il livello di persistenza basato su Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a1488-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="a1488-105">Entity Framework supporta LINQ e fornisce oggetti fortemente tipizzati per il modello, oltre alla persistenza semplificata nel database.</span><span class="sxs-lookup"><span data-stu-id="a1488-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="a1488-106">Entity Framework è da tempo incluso in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1488-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="a1488-107">Quando si usa .NET Core, è necessario usare anche Entity Framework Core, che viene eseguito in Windows o Linux in modo analogo a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1488-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="a1488-108">Entity Framework Core è una versione completamente rinnovata di Entity Framework, caratterizzata da un footprint ridotto e in cui sono state implementati importanti miglioramenti nelle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a1488-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="a1488-109">Introduzione a Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a1488-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="a1488-110">Entity Framework (EF) Core è una versione semplice, estendibile e multipiattaforma della tecnologia di accesso dati Entity Framework più diffusa.</span><span class="sxs-lookup"><span data-stu-id="a1488-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="a1488-111">È stato introdotto con .NET Core a metà del 2016.</span><span class="sxs-lookup"><span data-stu-id="a1488-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="a1488-112">Dal momento che nella documentazione Microsoft è già disponibile un'introduzione a Entity Framework Core, in questa sede verranno forniti solo i collegamenti a tali informazioni.</span><span class="sxs-lookup"><span data-stu-id="a1488-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1488-113">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a1488-113">Additional resources</span></span>

- <span data-ttu-id="a1488-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="a1488-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="a1488-115">**Introduzione ad ASP.NET Core ed Entity Framework Core con Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="a1488-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="a1488-116">**DbContext Class** </span><span class="sxs-lookup"><span data-stu-id="a1488-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="a1488-117">**Confrontare EF Core e EF6.x** </span><span class="sxs-lookup"><span data-stu-id="a1488-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="a1488-118">Infrastruttura in Entity Framework Core dal punto di vista della progettazione basata su dominio</span><span class="sxs-lookup"><span data-stu-id="a1488-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="a1488-119">Dal punto di vista della progettazione basata su dominio, un'importante funzionalità di Entity Framework è data dalla possibilità di usare le entità di dominio POCO, note nella terminologia di Entity Framework come *entità Code First* POCO.</span><span class="sxs-lookup"><span data-stu-id="a1488-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="a1488-120">Se si usano le entità di dominio POCO, le classi del modello di dominio non riconoscono la persistenza, risultando conformi ai principi di [Persistence Ignorance](https://deviq.com/persistence-ignorance/) e [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance).</span><span class="sxs-lookup"><span data-stu-id="a1488-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="a1488-121">Per ogni schema di progettazione basata su dominio è consigliabile incapsulare le regole e il comportamento del dominio regole all'interno della classe di entità stessa, in modo che possa controllare invarianti, convalide e regole durante l'accesso a qualsiasi raccolta.</span><span class="sxs-lookup"><span data-stu-id="a1488-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="a1488-122">Nella progettazione basata su dominio non è quindi buona norma consentire l'accesso pubblico a raccolte di oggetti valore o entità figlio.</span><span class="sxs-lookup"><span data-stu-id="a1488-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="a1488-123">È invece opportuno esporre metodi che consentano di controllare come e quando è possibile aggiornare i campi e le raccolte di proprietà, nonché il comportamento e le azioni che devono essere eseguite in tale circostanza.</span><span class="sxs-lookup"><span data-stu-id="a1488-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="a1488-124">A partire da Entity Framework Core 1.1, per soddisfare tali requisiti di progettazione basata su dominio, nelle entità è possibile includere campi normali invece di proprietà pubbliche.</span><span class="sxs-lookup"><span data-stu-id="a1488-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="a1488-125">Se non si vuole che un campo di entità sia accessibile dall'esterno, è sufficiente creare solo l'attributo o il campo invece di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="a1488-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="a1488-126">È anche possibile usare setter di proprietà private.</span><span class="sxs-lookup"><span data-stu-id="a1488-126">You can also use private property setters.</span></span>

<span data-ttu-id="a1488-127">In modo analogo, è ora possibile accedere in sola lettura alle raccolte usando una proprietà pubblica tipizzata come `IReadOnlyCollection<T>`, che è supportata da un membro di campo privato per la raccolta (ad esempio `List<T>`) nell'entità che si basa su Entity Framework per la persistenza.</span><span class="sxs-lookup"><span data-stu-id="a1488-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="a1488-128">Nelle versioni precedenti di Entity Framework le proprietà della raccolta dovevano supportare `ICollection<T>`, di conseguenza gli sviluppatori che usavano la classe di entità padre potevano aggiungere o rimuovere elementi tramite le relative raccolte di proprietà.</span><span class="sxs-lookup"><span data-stu-id="a1488-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="a1488-129">Tale possibilità era però in conflitto con i criteri consigliati per la progettazione basata su dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="a1488-130">È possibile usare una raccolta privata esponendo al contempo un oggetto `IReadOnlyCollection<T>` di sola lettura, come illustrato nell'esempio di codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a1488-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="a1488-131">Si noti che è possibile solo accedere alla proprietà `OrderItems` in modalità di sola lettura usando `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="a1488-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="a1488-132">Questo tipo è di sola lettura ed è quindi protetto dai normali aggiornamenti esterni.</span><span class="sxs-lookup"><span data-stu-id="a1488-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="a1488-133">Entity Framework Core offre un modo per eseguire il mapping del modello di dominio al database fisico senza "contaminare" il modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="a1488-134">Si tratta di codice .NET POCO puro, dal momento che l'azione di mapping viene implementata nel livello di persistenza.</span><span class="sxs-lookup"><span data-stu-id="a1488-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="a1488-135">In tale azione di mapping è necessario configurare il mapping tra campi e database.</span><span class="sxs-lookup"><span data-stu-id="a1488-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="a1488-136">Nell'esempio seguente del metodo `OnModelCreating` della classe `OrderingContext` e `OrderEntityTypeConfiguration`, la chiamata a `SetPropertyAccessMode` indica a Entity Framework Core di accedere alla proprietà `OrderItems` tramite il relativo campo.</span><span class="sxs-lookup"><span data-stu-id="a1488-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="a1488-137">Quando i campi vengono usati al posto delle proprietà, l'entità `OrderItem` viene salvata in modo permanente come se includesse una proprietà `List<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="a1488-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="a1488-138">Tale entità espone comunque una singola funzione di accesso, ovvero il metodo `AddOrderItem` per aggiungere nuovi elementi all'ordine.</span><span class="sxs-lookup"><span data-stu-id="a1488-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="a1488-139">Di conseguenza, il comportamento e i dati sono strettamente legati tra loro e saranno coerenti in tutto il codice dell'applicazione che usa il modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="a1488-140">Implementare repository personalizzati con Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a1488-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="a1488-141">A livello di implementazione, un repository è semplicemente una classe che contiene codice per la persistenza dei dati coordinato da un'unità di lavoro (DBContext in Entity Framework Core) durante l'esecuzione degli aggiornamenti, come illustrato nella classe seguente:</span><span class="sxs-lookup"><span data-stu-id="a1488-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="a1488-142">Si noti che l'interfaccia IBuyerRepository proviene dal livello del modello di dominio sotto forma di contratto.</span><span class="sxs-lookup"><span data-stu-id="a1488-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="a1488-143">L'implementazione del repository viene però effettuata a livello di persistenza e infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="a1488-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="a1488-144">L'elemento DbContext di Entity Framework attraversa il costruttore tramite il modello di inserimento delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="a1488-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="a1488-145">È condiviso tra più repository nello stesso ambito della richiesta HTTP, grazie alla relativa durata predefinita (`ServiceLifetime.Scoped`) nel contenitore IoC (che può essere anche impostato in modo esplicito con `services.AddDbContext<>`).</span><span class="sxs-lookup"><span data-stu-id="a1488-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="a1488-146">Metodi da implementare in un repository (aggiornamenti o transazioni e query)</span><span class="sxs-lookup"><span data-stu-id="a1488-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="a1488-147">All'interno di ogni classe di repository, è necessario inserire i metodi di persistenza che aggiornano lo stato delle entità contenute dall'aggregato correlato.</span><span class="sxs-lookup"><span data-stu-id="a1488-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="a1488-148">Tenere presente che esiste una relazione uno a uno tra un aggregato e il repository correlato.</span><span class="sxs-lookup"><span data-stu-id="a1488-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="a1488-149">Considerare che un oggetto entità radice aggregato potrebbe contenere entità figlio incorporate nel relativo grafo di Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a1488-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="a1488-150">Un acquirente potrebbe ad esempio usare più metodi di pagamento come entità figlio correlate.</span><span class="sxs-lookup"><span data-stu-id="a1488-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="a1488-151">Dal momento che l'approccio per il microservizio Ordering in eShopOnContainers si basa anche su CQS/CQRS, la maggior parte delle query non viene implementata in repository personalizzati.</span><span class="sxs-lookup"><span data-stu-id="a1488-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="a1488-152">Gli sviluppatori possono scegliere di creare le query e i join necessari per il livello di presentazione senza le restrizioni imposte dagli aggregati, dai repository personalizzati per aggregato e, più in generale dalla progettazione basata su dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="a1488-153">La maggior parte degli repository personalizzati suggeriti da questa guida include numerosi metodi transazionali o di aggiornamento, ma solo i metodi di query devono ottenere i dati da aggiornare.</span><span class="sxs-lookup"><span data-stu-id="a1488-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="a1488-154">Il repository BuyerRepository implementa ad esempio un metodo FindAsync, perché l'applicazione deve sapere se un particolare acquirente esiste già prima di creare un nuovo acquirente correlato all'ordine.</span><span class="sxs-lookup"><span data-stu-id="a1488-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="a1488-155">I metodi di query effettivi per ottenere i dati da inviare al livello di presentazione o alle app client vengono però implementati, come già detto, nelle query CQRS basate su query flessibili usando Dapper.</span><span class="sxs-lookup"><span data-stu-id="a1488-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="a1488-156">Uso di un repository personalizzato invece di usare direttamente DbContext di Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a1488-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="a1488-157">La classe DbContext di Entity Framework si basa sugli schemi Unit of Work e Repository e può essere usata direttamente dal codice utente, ad esempio da un controller MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1488-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="a1488-158">In questo modo è possibile creare il codice più semplice, come nel microservizio Catalog CRUD di eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a1488-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="a1488-159">Nei casi in cui si vuole che il codice sia il più semplice possibile è consigliabile usare direttamente la classe DbContext, come fanno molti sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="a1488-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="a1488-160">L'implementazione di repository personalizzati offre però diversi vantaggi quando si implementano microservizi o applicazioni più complesse.</span><span class="sxs-lookup"><span data-stu-id="a1488-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="a1488-161">Gli schemi Unit of Work and Repository vengono usati per incapsulare il livello di persistenza dell'infrastruttura in modo che sia scollegato dai livelli di applicazione e modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="a1488-162">L'implementazione di questi schemi può facilitare l'uso di repository fittizi che simulano l'accesso al database.</span><span class="sxs-lookup"><span data-stu-id="a1488-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="a1488-163">Nella Figura 7-18 è possibile osservare le differenze tra il mancato uso di repository (e l'uso diretto della classe DbContext di Entity Framework) e l'uso di repository per agevolare il comportamento fittizio di tali repository.</span><span class="sxs-lookup"><span data-stu-id="a1488-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Confronto tra l'uso di un repository personalizzato e una semplice classe DbContext: il repository personalizzato aggiunge un livello di astrazione che consente di semplificare il test rendendo fittizio il repository.](./media/image19.png)

<span data-ttu-id="a1488-165">**Figura 7-18**.</span><span class="sxs-lookup"><span data-stu-id="a1488-165">**Figure 7-18**.</span></span> <span data-ttu-id="a1488-166">Uso di repository personalizzati anziché una semplice classe DbContext</span><span class="sxs-lookup"><span data-stu-id="a1488-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="a1488-167">Per il comportamento fittizio è possibile scegliere tra diverse alternative.</span><span class="sxs-lookup"><span data-stu-id="a1488-167">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="a1488-168">È possibile applicare il comportamento fittizio solo ai repository oppure a un'intera unità di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a1488-168">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="a1488-169">In genere è sufficiente applicare il comportamento fittizio solo ai repository e non è necessario ricorrere alle tecniche complesse per astrarre e applicare il comportamento fittizio a un'intera unità di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a1488-169">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="a1488-170">Più avanti, quando verrà trattato il livello dell'applicazione, verrà illustrato il funzionamento del modello di inserimento delle dipendenze in ASP.NET Core e verrà spiegato come implementarlo quando si usano i repository.</span><span class="sxs-lookup"><span data-stu-id="a1488-170">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="a1488-171">In poche parole, i repository personalizzati consentono di testare il codice più facilmente con gli unit test che non sono interessati dallo stato del livello dati.</span><span class="sxs-lookup"><span data-stu-id="a1488-171">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="a1488-172">Se si eseguono test che accedono anche al database effettivo tramite Entity Framework, non si tratta di unit test, ma di test di integrazione, sono molto più lenti.</span><span class="sxs-lookup"><span data-stu-id="a1488-172">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="a1488-173">Se si usa direttamente DbContext, è necessario rendere la classe fittizia oppure eseguire gli unit test con un'istanza in memoria di SQL Server contenente dati prevedibili per gli unit test.</span><span class="sxs-lookup"><span data-stu-id="a1488-173">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="a1488-174">Una classe DbContext fittizia o il controllo di dati finti richiede tuttavia un intervento maggiore rispetto a un comportamento fittizio a livello di repository.</span><span class="sxs-lookup"><span data-stu-id="a1488-174">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="a1488-175">Naturalmente, sarebbe sempre possibile testare i controller MVC.</span><span class="sxs-lookup"><span data-stu-id="a1488-175">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="a1488-176">Durata dell'istanza di DbContext di Entity Framework e IUnitOfWork nel contenitore IoC</span><span class="sxs-lookup"><span data-stu-id="a1488-176">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="a1488-177">Potrebbe essere necessario condividere l'oggetto `DbContext` (esposto come oggetto `IUnitOfWork`) tra più repository all'interno dello stesso ambito della richiesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a1488-177">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="a1488-178">Questa condizione si verifica, ad esempio, quando l'operazione in esecuzione deve gestire più aggregati o semplicemente quando si usano più istanze di repository.</span><span class="sxs-lookup"><span data-stu-id="a1488-178">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="a1488-179">È anche importante ricordare che l'interfaccia `IUnitOfWork` fa parte del livello di dominio e non è un tipo di Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="a1488-179">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="a1488-180">A questo scopo, è necessario impostare su ServiceLifetime.Scoped la durata del servizio per l'istanza dell'oggetto `DbContext`.</span><span class="sxs-lookup"><span data-stu-id="a1488-180">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="a1488-181">Si tratta della durata predefinita quando si registra un oggetto `DbContext` con `services.AddDbContext` nel contenitore IoC dal metodo ConfigureServices del file `Startup.cs` nel progetto API Web di ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1488-181">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="a1488-182">Questa condizione è illustrata nel codice che segue.</span><span class="sxs-lookup"><span data-stu-id="a1488-182">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="a1488-183">La modalità di creazione di un'istanza di DbContext non deve essere configurata come ServiceLifetime.Transient o ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="a1488-183">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="a1488-184">Durata dell'istanza del repository nel contenitore IoC</span><span class="sxs-lookup"><span data-stu-id="a1488-184">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="a1488-185">In modo analogo, la durata del repository deve essere in genere impostata come inclusa nell'ambito (InstancePerLifetimeScope in Autofac).</span><span class="sxs-lookup"><span data-stu-id="a1488-185">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="a1488-186">Può anche essere temporanea (InstancePerDependency in Autofac), ma se si usa la durata inclusa nell'ambito il servizio risulterà più efficiente in termini di memoria.</span><span class="sxs-lookup"><span data-stu-id="a1488-186">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="a1488-187">Si noti che l'uso della durata del singleton per il repository potrebbe causare gravi problemi di concorrenza quando l'oggetto DbContext è impostato sulla durata con ambito (InstancePerLifetimeScope), ovvero la durata predefinita per un oggetto DBContext.</span><span class="sxs-lookup"><span data-stu-id="a1488-187">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1488-188">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a1488-188">Additional resources</span></span>

- <span data-ttu-id="a1488-189">**Implementazione dei modelli con repository e unità di lavoro in un'applicazione MVC ASP.NET** </span><span class="sxs-lookup"><span data-stu-id="a1488-189">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="a1488-190">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** \ (Strategie di implementazione per il modello di repository con Entity Framework, Dapper e Chain)</span><span class="sxs-lookup"><span data-stu-id="a1488-190">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** \</span></span>
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="a1488-191">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** \ (Confronto tra la durata del servizio contenitore IoC di ASP.NET Core con gli ambiti delle istanze di contenitore IoC di Autofac)</span><span class="sxs-lookup"><span data-stu-id="a1488-191">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** \</span></span>
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="a1488-192">Mapping di tabella</span><span class="sxs-lookup"><span data-stu-id="a1488-192">Table mapping</span></span>

<span data-ttu-id="a1488-193">Il mapping di tabella consente di identificare i dati di tabella per i quali eseguire query dal database e che devono essere salvati nel database.</span><span class="sxs-lookup"><span data-stu-id="a1488-193">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="a1488-194">In precedenza, è stato spiegato come usare entità di dominio, ad esempio un dominio order o product, per generare uno schema di database correlato.</span><span class="sxs-lookup"><span data-stu-id="a1488-194">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="a1488-195">Entity Framework si basa principalmente sul concetto di *convenzioni*.</span><span class="sxs-lookup"><span data-stu-id="a1488-195">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="a1488-196">Le convenzioni consentono di rispondere a domande relative a quale sarà il nome della tabella</span><span class="sxs-lookup"><span data-stu-id="a1488-196">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="a1488-197">o quale proprietà è la chiave primaria.</span><span class="sxs-lookup"><span data-stu-id="a1488-197">or “What property is the primary key?”</span></span> <span data-ttu-id="a1488-198">Le convenzioni sono in genere basate su nomi convenzionali: ad esempio la chiave primaria è in genere una proprietà che termina con Id.</span><span class="sxs-lookup"><span data-stu-id="a1488-198">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="a1488-199">Per convenzione, ogni entità viene configurata in modo da eseguire il mapping a una tabella con lo stesso nome della proprietà `DbSet<TEntity>` che espone l'entità nel contesto derivato.</span><span class="sxs-lookup"><span data-stu-id="a1488-199">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="a1488-200">Se per l'entità specificata non viene definito un valore `DbSet<TEntity>`, viene usato il nome di classe.</span><span class="sxs-lookup"><span data-stu-id="a1488-200">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="a1488-201">Annotazioni di dati e API Fluent</span><span class="sxs-lookup"><span data-stu-id="a1488-201">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="a1488-202">Esistono numerose convenzioni aggiuntive di Entity Framework Core e la maggior parte di esse può essere modificata tramite le annotazioni di dati o l'API Fluent, implementata all'interno del metodo OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="a1488-202">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="a1488-203">Le annotazioni di dati devono essere usate sulle classi stesse del modello di entità e questa costituisce una modalità di utilizzo più intrusiva dal punto di vista della progettazione basata su dominio.</span><span class="sxs-lookup"><span data-stu-id="a1488-203">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="a1488-204">Questo in quanto si sta contaminando il modello con annotazioni di dati correlate al database dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="a1488-204">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="a1488-205">D'altra parte, l'API Fluent è un modo pratico per modificare la maggior parte delle convenzioni e i mapping all'interno del livello dell'infrastruttura di persistenza dei dati, in modo che il modello di entità sia pulito e scollegato dall'infrastruttura di persistenza.</span><span class="sxs-lookup"><span data-stu-id="a1488-205">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="a1488-206">API Fluent e il metodo OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="a1488-206">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="a1488-207">Come accennato in precedenza, per modificare le convenzioni e i mapping, è possibile usare il metodo OnModelCreating nella classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="a1488-207">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="a1488-208">Il microservizio Ordering in eShopOnContainers implementa la configurazione e il mapping esplicito, quando necessario, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="a1488-208">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="a1488-209">È possibile impostare tutti i mapping dell'API Fluent all'interno dello stesso metodo OnModelCreating, ma è consigliabile suddividere in parti tale codice e definire più classi di configurazione, una per entità, come illustrato nell'esempio.</span><span class="sxs-lookup"><span data-stu-id="a1488-209">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="a1488-210">In particolare per i modelli di grandi dimensioni, è consigliabile definire classi di configurazione separate per la configurazione di tipi di entità diversi.</span><span class="sxs-lookup"><span data-stu-id="a1488-210">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="a1488-211">Il codice nell'esempio mostra alcuni mapping e dichiarazioni esplicite.</span><span class="sxs-lookup"><span data-stu-id="a1488-211">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="a1488-212">Le convenzioni di Entity Framework Core eseguono però automaticamente molti di questi mapping, di conseguenza il codice effettivo necessario potrebbe essere ridotto.</span><span class="sxs-lookup"><span data-stu-id="a1488-212">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="a1488-213">Algoritmo Hi/Lo in Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a1488-213">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="a1488-214">Un aspetto interessante del codice nell'esempio precedente è che usa l'[algoritmo Hi/Low](https://vladmihalcea.com/the-hilo-algorithm/) come strategia di generazione delle chiavi.</span><span class="sxs-lookup"><span data-stu-id="a1488-214">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="a1488-215">L'algoritmo Hi/Lo è utile quando sono necessarie chiavi univoche prima di apportare modifiche.</span><span class="sxs-lookup"><span data-stu-id="a1488-215">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="a1488-216">Riassumendo, l'algoritmo Hi-Lo assegna identificatori univoci alle righe della tabella, pur non dipendendo immediatamente dall'archiviazione della riga nel database.</span><span class="sxs-lookup"><span data-stu-id="a1488-216">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="a1488-217">In questo modo è possibile iniziare subito a usare gli identificatori, come avviene con gli ID dei normali database sequenziali.</span><span class="sxs-lookup"><span data-stu-id="a1488-217">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="a1488-218">L'algoritmo Hi/Lo descrive un meccanismo per il recupero di un batch di ID univoci da una sequenza di database correlata.</span><span class="sxs-lookup"><span data-stu-id="a1488-218">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="a1488-219">Questi ID sono sicuri perché il database garantisce l'univocità, pertanto non vi sarà alcuna collisione tra utenti.</span><span class="sxs-lookup"><span data-stu-id="a1488-219">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="a1488-220">Questo algoritmo è interessante per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a1488-220">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="a1488-221">Non causa interruzioni nello schema Unit of Work.</span><span class="sxs-lookup"><span data-stu-id="a1488-221">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="a1488-222">Ottiene gli ID di sequenza in batch, per ridurre al minimo i round trip al database.</span><span class="sxs-lookup"><span data-stu-id="a1488-222">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="a1488-223">Genera un identificatore leggibile, a differenza delle tecniche che usano GUID.</span><span class="sxs-lookup"><span data-stu-id="a1488-223">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="a1488-224">Entity Framework Core supporta l'algoritmo [Hi/Lo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) con il metodo ForSqlServerUseSequenceHiLo, come illustrato nell'esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="a1488-224">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="a1488-225">Eseguire il mapping di campi anziché di proprietà</span><span class="sxs-lookup"><span data-stu-id="a1488-225">Map fields instead of properties</span></span>

<span data-ttu-id="a1488-226">Con questa funzionalità, disponibile a partire da Entity Framework Core 1.1, è possibile eseguire direttamente il mapping delle colonne ai campi.</span><span class="sxs-lookup"><span data-stu-id="a1488-226">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="a1488-227">Non è possibile usare proprietà nella classe di entità e limitarsi a eseguire il mapping delle colonne di una tabella ai campi.</span><span class="sxs-lookup"><span data-stu-id="a1488-227">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="a1488-228">Questa funzionalità viene usata in genere per campi privati relativi a un qualsiasi stato interno che non devono essere accessibili dall'esterno dell'entità.</span><span class="sxs-lookup"><span data-stu-id="a1488-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="a1488-229">È possibile eseguire questa operazione con singoli campi o anche con le raccolte, ad esempio un campo `List<>`.</span><span class="sxs-lookup"><span data-stu-id="a1488-229">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="a1488-230">Questo aspetto è stato menzionato in precedenza quando è stata illustrata la modellazione delle classi del modello di dominio, ma qui è possibile comprendere in che modo viene eseguito tale mapping con la configurazione di `PropertyAccessMode.Field` evidenziata nel codice precedente.</span><span class="sxs-lookup"><span data-stu-id="a1488-230">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="a1488-231">Usare le proprietà shadow in Entity Framework Core, nascoste a livello di infrastruttura</span><span class="sxs-lookup"><span data-stu-id="a1488-231">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="a1488-232">In Entity Framework Core le proprietà shadow sono proprietà che non esistono nel modello della classe di entità.</span><span class="sxs-lookup"><span data-stu-id="a1488-232">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="a1488-233">I valori e gli stati di queste proprietà vengono gestiti esclusivamente nella classe [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) a livello di infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="a1488-233">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="a1488-234">Implementare lo schema di specifica della query</span><span class="sxs-lookup"><span data-stu-id="a1488-234">Implement the Query Specification pattern</span></span>

<span data-ttu-id="a1488-235">Come descritto in precedenza nella sezione relativa alla progettazione, lo schema di specifica della query è un schema di progettazione basato su dominio concepito come punto in cui è possibile inserire la definizione di una query con logica facoltativa di ordinamento e paging.</span><span class="sxs-lookup"><span data-stu-id="a1488-235">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="a1488-236">Lo schema di specifica della query consente di definire una query in un oggetto.</span><span class="sxs-lookup"><span data-stu-id="a1488-236">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="a1488-237">Per poter incapsulare una query di paging che cerca alcuni prodotti, ad esempio, è possibile creare una specifica PagedProduct che accetta i parametri di input necessari (pageNumber, pageSize, filter e così via).</span><span class="sxs-lookup"><span data-stu-id="a1488-237">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="a1488-238">In questo modo, qualsiasi metodo di repository (in genere un overload List()) accetterà un elemento IQuerySpecification ed eseguirà la query in base a tale specifica.</span><span class="sxs-lookup"><span data-stu-id="a1488-238">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="a1488-239">Un esempio di interfaccia di specifica generica è il codice seguente tratto da [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="a1488-239">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="a1488-240">L'implementazione della classe di base di una specifica generica è la seguente.</span><span class="sxs-lookup"><span data-stu-id="a1488-240">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="a1488-241">La specifica seguente carica una singola entità carrello (basket) dato l'ID carrello (basketId) o l'ID acquirente (buyerId) a cui appartiene il carrello.</span><span class="sxs-lookup"><span data-stu-id="a1488-241">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="a1488-242">Esegue il [caricamento eager](https://docs.microsoft.com/ef/core/querying/related-data) della raccolta Items del carrello.</span><span class="sxs-lookup"><span data-stu-id="a1488-242">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="a1488-243">È infine possibile osservare sotto in che modo un repository generico di Entity Framework può usare tale specifica per filtrare ed eseguire il caricamento eager di dati correlati a un dato tipo di entità T.</span><span class="sxs-lookup"><span data-stu-id="a1488-243">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="a1488-244">Oltre a incapsulare la logica di filtro, la specifica è in grado di indicare la forma dei dati da restituire, incluse le proprietà da popolare.</span><span class="sxs-lookup"><span data-stu-id="a1488-244">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="a1488-245">Anche se non è consigliabile restituire espressioni IQueryable da un repository, è possibile usarle all'interno del repository per creare un set di risultati.</span><span class="sxs-lookup"><span data-stu-id="a1488-245">Although we don’t recommend to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="a1488-246">È possibile vedere questo approccio usato nel metodo List sopra, che utilizza espressioni intermedie IQueryable per creare l'elenco di istruzioni includes della query prima di eseguire la query con i criteri della specifica nell'ultima riga.</span><span class="sxs-lookup"><span data-stu-id="a1488-246">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1488-247">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a1488-247">Additional resources</span></span>

- <span data-ttu-id="a1488-248">**Mapping di tabella** </span><span class="sxs-lookup"><span data-stu-id="a1488-248">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="a1488-249">**Use HiLo to generate keys with Entity Framework Core** \ (Usare HiLo per generare chiavi con Entity Framework Core)</span><span class="sxs-lookup"><span data-stu-id="a1488-249">**Use HiLo to generate keys with Entity Framework Core** \</span></span>
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="a1488-250">**Campi sottostanti** </span><span class="sxs-lookup"><span data-stu-id="a1488-250">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="a1488-251">**Steve Smith. Encapsulated Collections in Entity Framework Core** \ (Raccolte incapsulate in Entity Framework Core)</span><span class="sxs-lookup"><span data-stu-id="a1488-251">**Steve Smith. Encapsulated Collections in Entity Framework Core** \</span></span>
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="a1488-252">**Proprietà shadow** </span><span class="sxs-lookup"><span data-stu-id="a1488-252">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="a1488-253">**The Specification pattern.**  \ (Schema Specification)</span><span class="sxs-lookup"><span data-stu-id="a1488-253">**The Specification pattern** \</span></span>
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="a1488-254">[Precedente](infrastructure-persistence-layer-design.md)
> [Successivo](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="a1488-254">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>