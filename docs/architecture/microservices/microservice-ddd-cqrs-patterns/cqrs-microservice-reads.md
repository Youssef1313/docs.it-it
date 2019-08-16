---
title: Implementazione di letture/query in un microservizio CQRS
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Riconoscere l'implementazione del lato query di CQRS nel microservizio degli ordini in eShopOnContainers con Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: f791546e2fc00e276ab55302802a5534465ace58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674338"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="a2d1e-103">Implementare le letture/query in un microservizio CQRS</span><span class="sxs-lookup"><span data-stu-id="a2d1e-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="a2d1e-104">Per le operazioni di lettura/query, il microservizio degli ordini dall'applicazione di riferimento eShopOnContainers implementa le query in modo indipendente dal modello DDD e dall'area transazionale.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="a2d1e-105">Tale operazione veniva eseguita principalmente perché le richieste di query e di transazioni sono estremamente diverse.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="a2d1e-106">Le scritture eseguono le transazioni che devono essere conformi con la logica di dominio.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="a2d1e-107">Le query, d'altra parte, sono idempotenti e possono essere separate dalle regole di dominio.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="a2d1e-108">L'approccio è semplice, come illustrato nella figura 7-3.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="a2d1e-109">L'interfaccia API viene implementata dai controller API Web usando qualsiasi infrastruttura, ad esempio un micro ORM (Object Relational Mapper) come Dapper, e restituendo ViewModel dinamici a seconda delle esigenze delle applicazioni dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![L'approccio più semplice per il lato query in un approccio CQRS semplificato può essere implementato semplicemente interrogando il database con un Micro ORM di tipo Dapper, restituendo ViewModel dinamici.](./media/image3.png)

<span data-ttu-id="a2d1e-111">**Figura 7-3**.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-111">**Figure 7-3**.</span></span> <span data-ttu-id="a2d1e-112">L'approccio più semplice per le query in un microservizio CQRS</span><span class="sxs-lookup"><span data-stu-id="a2d1e-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="a2d1e-113">Questo è l'approccio più semplice possibile per le query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="a2d1e-114">Le definizioni di query interrogano il database e restituiscono un ViewModel dinamico compilato in tempo reale per ogni query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="a2d1e-115">Visto che le query sono idempotenti, non modificheranno i dati indipendentemente da quante volte si esegue una query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="a2d1e-116">Di conseguenza, non si è necessariamente limitati da nessuno schema DDD usato nel lato transazionale, ad esempio aggregazioni e altri schemi, ed è per tale motivo che le query sono separate dall'area transazionale.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="a2d1e-117">È sufficiente eseguire query sul database per i dati necessari per l'interfaccia utente e restituire un ViewModel dinamico che non deve essere definito staticamente in nessun luogo (nessuna classe per i ViewModel) tranne che nelle stesse istruzioni SQL.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="a2d1e-118">Visto che si tratta di un approccio semplice, il codice necessario per il lato di query (ad esempio il codice che usa un micro ORM come [Dapper](https://github.com/StackExchange/Dapper)) può essere implementato [nello stesso progetto API Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="a2d1e-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="a2d1e-119">La figura 7-4 mostra un esempio.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="a2d1e-120">Le query sono definite nel progetto di microservizio **Ordering.API** all'interno della soluzione eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Visualizzazione di Esplora soluzioni del progetto Ordering.API, che mostra la cartella Applicazione > Query.](./media/image4.png)

<span data-ttu-id="a2d1e-122">**Figura 7-4**.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-122">**Figure 7-4**.</span></span> <span data-ttu-id="a2d1e-123">Query nel microservizio degli ordini in eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a2d1e-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="a2d1e-124">Usare ViewModel creati in modo specifico per le applicazioni client, indipendentemente dai vincoli del modello di dominio</span><span class="sxs-lookup"><span data-stu-id="a2d1e-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="a2d1e-125">Visto che le query vengono eseguite per ottenere i dati necessari dalle applicazioni client, il tipo restituito può essere creato in modo specifico per i client, in base ai dati restituiti dalle query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="a2d1e-126">Questi modelli, detti anche oggetti Data Transfer (DTO), vengono chiamati ViewModel.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="a2d1e-127">I dati restituiti (ViewModel) possono essere il risultato dell'unione di dati da più entità o tabelle nel database o persino tra più aggregazioni definite nel modello di dominio per l'area transazionale.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="a2d1e-128">In questo caso, giacché si stanno creando query indipendenti dal modello di dominio, i limiti e i vincoli delle aggregazioni vengono completamente ignorati e si è liberi di interrogare qualsiasi tabella e colonna che potrebbe essere necessaria.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="a2d1e-129">Questo approccio offre agli sviluppatori grande flessibilità e produttività per creare o aggiornare le query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="a2d1e-130">I ViewModel possono essere tipi statici definiti nelle classi,</span><span class="sxs-lookup"><span data-stu-id="a2d1e-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="a2d1e-131">oppure possono essere creati in modo dinamico in base alle query eseguite (così come implementate nel microservizio degli ordini), una funzionalità molto agile per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="a2d1e-132">Usare Dapper come micro ORM per eseguire query</span><span class="sxs-lookup"><span data-stu-id="a2d1e-132">Use Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="a2d1e-133">È possibile usare qualsiasi micro ORM, Entity Framework Core o persino il normale ADO.NET per l'esecuzione di query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="a2d1e-134">Nell'applicazione di esempio, Dapper è stato selezionato per il microservizio degli ordini in eShopOnContainers come ottimo esempio di micro ORM più diffuso.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="a2d1e-135">Può eseguire semplici query SQL con prestazioni elevate, perché è un framework molto leggero.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="a2d1e-136">Con Dapper, è possibile scrivere una query SQL che può accedere e creare un join a più tabelle.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="a2d1e-137">Dapper è un progetto open source (originalmente creato da Sam Saffron) e fa parte dei blocchi predefiniti usati nell'[Overflow dello stack](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="a2d1e-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="a2d1e-138">Per usare Dapper, è sufficiente installarlo con il [pacchetto NuGet Dapper](https://www.nuget.org/packages/Dapper), come illustrato nella figura riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="a2d1e-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Pacchetto di Dapper visualizzato nella vista di gestione dei pacchetti NuGet in Visual Studio.](./media/image4.1.png)

<span data-ttu-id="a2d1e-140">È anche necessario aggiungere un'istruzione Using, in modo che il codice abbia accesso ai metodi di estensione di Dapper.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="a2d1e-141">Quando si usa Dapper nel codice, si usa direttamente la classe <xref:System.Data.SqlClient.SqlConnection> disponibile nello spazio dei nomi <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="a2d1e-142">Usando il metodo QueryAsync e altri metodi di estensione che estendono la classe <xref:System.Data.SqlClient.SqlConnection> è possibile eseguire query in modo semplice e ad alte prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="a2d1e-143">ViewModel dinamici e statici a confronto</span><span class="sxs-lookup"><span data-stu-id="a2d1e-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="a2d1e-144">Quando i ViewModel vengono restituiti dal lato server alle app client, è possibile considerarli come DTO (Data Transfer Objects) che possono essere diversi per le entità del dominio interno del modello di entità, perché conservano i dati nel modo richiesto dall'app client.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="a2d1e-145">Di conseguenza, in molti casi, è possibile aggregare i dati provenienti da più entità di dominio e comporre il ViewModel con precisione in base al modo in cui l'applicazione client necessita di quei dati.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="a2d1e-146">Tali ViewModel, o DTO, possono essere esplicitamente definiti (come classi contenitori di dati) come la classe `OrderSummary` mostrata in un frammento di codice successivo, oppure è possibile restituire solo ViewModel o DTO dinamici basati semplicemente sugli attributi restituiti dalle query, come tipo dinamico.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="a2d1e-147">ViewModel come tipo dinamico</span><span class="sxs-lookup"><span data-stu-id="a2d1e-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="a2d1e-148">Come illustrato nel codice seguente, un `ViewModel` può essere restituito direttamente dalle query con la semplice restituzione di un tipo *dinamico* internamente basato sugli attributi restituiti da una query.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="a2d1e-149">Ciò significa che il subset di attributi da restituire è basato sulla query stessa.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="a2d1e-150">Di conseguenza, se si aggiunge una nuova colonna alla query o al join, tali dati vengono aggiunti in modo dinamico al `ViewModel` restituito.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="a2d1e-151">L'aspetto importante è che, usando un tipo dinamico, la raccolta dei dati restituita viene assemblata in modo dinamico come ViewModel.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="a2d1e-152">**Vantaggi:** questo approccio riduce la necessità di modificare le classi ViewModel statiche ogni volta che si aggiorna la frase SQL di una query, rendendo molto agile questo approccio di progettazione durante la codifica, con un'evoluzione semplice e rapida per quanto riguarda le modifiche future.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="a2d1e-153">**Svantaggi:** a lungo termine, i tipi dinamici possono influire negativamente sulla chiarezza e sulla compatibilità di un servizio con le app client.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="a2d1e-154">In più, il software middleware come Swashbuckle non può fornire lo stesso livello di documentazione sui tipi restituiti se si usano tipi dinamici.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="a2d1e-155">ViewModel come classi DTO predefinite</span><span class="sxs-lookup"><span data-stu-id="a2d1e-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="a2d1e-156">**Vantaggi:** avere classi ViewModel predefinite statiche, ad esempio "contratti" basati su classi DTO esplicite, è decisamente meglio per le API pubbliche, ma anche per i microservizi a lungo termine, anche se vengono usati solo dall'applicazione stessa.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="a2d1e-157">Se si vogliono specificare i tipi di risposta per Swagger, è necessario usare le classi DTO esplicite come tipo restituito.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="a2d1e-158">Di conseguenza, le classi DTO predefinite consentono di offrire informazioni più complete da Swagger.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="a2d1e-159">In tal modo, la documentazione e la compatibilità delle API migliora durante il loro utilizzo.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="a2d1e-160">**Svantaggi:** come indicato in precedenza, durante il suo aggiornamento, il codice richiede alcuni ulteriori passaggi per aggiornare le classi DTO.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="a2d1e-161">*Suggerimenti basati sull'esperienza Microsoft*: nelle query implementate nel microservizio degli ordini in eShopOnContainers, lo sviluppo è iniziato usando ViewModel dinamici perché era molto semplice e agile nelle prime fasi di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="a2d1e-162">Tuttavia, una volta che lo sviluppo si è stabilizzato, è stato scelto di eseguire il refactoring delle API e di usare DTO statici o predefiniti per i ViewModel, perché era più chiaro per i consumer del microservizio conoscere i tipi di DTO espliciti, usati come "contratti".</span><span class="sxs-lookup"><span data-stu-id="a2d1e-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="a2d1e-163">Nell'esempio seguente, è possibile visualizzare in che modo la query restituisce dati usando una classe DTO ViewModel esplicita: la classe OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="a2d1e-164">Descrivere i tipi di risposta delle API Web</span><span class="sxs-lookup"><span data-stu-id="a2d1e-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="a2d1e-165">Per gli sviluppatori che utilizzano API Web e microservizi è più importante ciò che viene restituito, in particolare i tipi di risposta e i codici di errore, se diversi da quelli standard.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="a2d1e-166">Questi vengono gestiti nei commenti XML e nelle annotazioni dei dati.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="a2d1e-167">Senza la documentazione appropriata nell'interfaccia utente di Swagger, il consumer non riconosce i tipi restituiti né i codici HTTP che potrebbero esserlo.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="a2d1e-168">È possibile risolvere questo problema aggiungendo l'attributo <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, in modo che Swashbuckle possa generare informazioni più complete sui modelli e i valori restituiti dall'API, come mostra il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a2d1e-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="a2d1e-169">Tuttavia, l'attributo `ProducesResponseType` non può usare un tipo dinamico, ma richiede l'uso di tipi espliciti, come il DTO ViewModel `OrderSummary`, mostrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="a2d1e-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="a2d1e-170">Si tratta di un altro motivo per cui i tipi restituiti espliciti sono migliori rispetto ai tipi dinamici, a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="a2d1e-171">Quando si usa l'attributo `ProducesResponseType`, è anche possibile specificare qual è il risultato previsto per quanto riguarda i possibili errori/codici HTTP, ad esempio 200, 400, ecc.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="a2d1e-172">Nella figura seguente, è possibile vedere in che modo l'interfaccia utente di Swagger mostra le informazioni ResponseType.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Visualizzazione browser della pagina dell'interfaccia utente di Swagger per l'API degli ordini.](./media/image5.png)

<span data-ttu-id="a2d1e-174">**Figura 7-5.**</span><span class="sxs-lookup"><span data-stu-id="a2d1e-174">**Figure 7-5**.</span></span> <span data-ttu-id="a2d1e-175">Interfaccia utente di Swagger che mostra i tipi di risposta e i possibili codici di stato HTTP da un'API Web</span><span class="sxs-lookup"><span data-stu-id="a2d1e-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="a2d1e-176">È possibile vedere nell'immagine precedente alcuni valori di esempio basati sui tipi ViewModel, oltre ai codici di stato HTTP che possono essere restituiti.</span><span class="sxs-lookup"><span data-stu-id="a2d1e-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a2d1e-177">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a2d1e-177">Additional resources</span></span>

- <span data-ttu-id="a2d1e-178">**Dapper** </span><span class="sxs-lookup"><span data-stu-id="a2d1e-178">**Dapper** </span></span>\
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="a2d1e-179">**Julie Lerman. Punti dati - Dapper, Entity Framework e app ibride (articolo Mag. MSDN)**  </span><span class="sxs-lookup"><span data-stu-id="a2d1e-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)** </span></span>\
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- <span data-ttu-id="a2d1e-180">**Pagine della Guida dell'API Web ASP.NET Core con Swagger** </span><span class="sxs-lookup"><span data-stu-id="a2d1e-180">**ASP.NET Core Web API Help Pages using Swagger** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="a2d1e-181">[Precedente](eshoponcontainers-cqrs-ddd-microservice.md)
>[Successivo](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="a2d1e-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>