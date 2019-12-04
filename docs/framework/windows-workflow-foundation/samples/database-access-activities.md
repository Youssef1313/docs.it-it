---
title: Attività di accesso al database
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: eec368803eeacb2bab729bcd6d57cc7fc6107256
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710853"
---
# <a name="database-access-activities"></a><span data-ttu-id="b5ce3-102">Attività di accesso al database</span><span class="sxs-lookup"><span data-stu-id="b5ce3-102">Database Access Activities</span></span>

<span data-ttu-id="b5ce3-103">Le attività di accesso al database consentono di accedere a un database all'interno di un flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="b5ce3-104">Queste attività consentono l'accesso ai database per recuperare o modificare informazioni e utilizzare [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) per accedere al database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5ce3-105">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5ce3-106">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b5ce3-107">Se questa directory non esiste, andare alla pagina di download per scaricare tutti gli esempi di Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5ce3-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5ce3-108">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="b5ce3-109">Attività di database</span><span class="sxs-lookup"><span data-stu-id="b5ce3-109">Database Activities</span></span>

<span data-ttu-id="b5ce3-110">Nelle sezioni seguenti viene descritto in dettaglio l'elenco delle attività incluse in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="b5ce3-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="b5ce3-111">DbUpdate</span></span>

<span data-ttu-id="b5ce3-112">Esegue una query SQL che produce una modifica nel database (inserimento, aggiornamento, eliminazione e altre modifiche).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="b5ce3-113">Questa classe esegue le relative operazioni in modo asincrono (deriva da <xref:System.Activities.AsyncCodeActivity> e usa le relative funzionalità asincrone).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="b5ce3-114">È possibile configurare le informazioni di connessione impostando un nome invariante del provider (`ProviderName`) e la stringa di connessione (`ConnectionString`) o solo usando un nome di configurazione della stringa di connessione (`ConfigFileSectionName`) dal file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="b5ce3-115">La query da eseguire viene configurata nella relativa proprietà `Sql` e i parametri vengono passati tramite la raccolta `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="b5ce3-116">Dopo l'esecuzione di `DbUpdate`, il numero di record interessati viene restituito nella proprietà `AffectedRecords`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="b5ce3-117">Argomento</span><span class="sxs-lookup"><span data-stu-id="b5ce3-117">Argument</span></span>|<span data-ttu-id="b5ce3-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-118">Description</span></span>|
|-|-|
|<span data-ttu-id="b5ce3-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-119">ProviderName</span></span>|<span data-ttu-id="b5ce3-120">Nome invariante del provider ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="b5ce3-121">Se viene impostato questo argomento, è necessario impostare anche `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b5ce3-122">ConnectionString</span></span>|<span data-ttu-id="b5ce3-123">Stringa di connessione per connettersi al database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-123">Connection string to connect to the database.</span></span> <span data-ttu-id="b5ce3-124">Se viene impostato questo argomento, è necessario impostare anche `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-125">ConfigName</span></span>|<span data-ttu-id="b5ce3-126">Nome della sezione del file di configurazione in cui sono archiviate le informazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="b5ce3-127">Quando viene impostato questo argomento, `ProviderName` e `ConnectionString` non sono richiesti.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="b5ce3-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="b5ce3-128">CommandType</span></span>|<span data-ttu-id="b5ce3-129">Tipo di <xref:System.Data.Common.DbCommand> da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="b5ce3-130">Sql</span><span class="sxs-lookup"><span data-stu-id="b5ce3-130">Sql</span></span>|<span data-ttu-id="b5ce3-131">Comando SQL da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="b5ce3-132">Parametri</span><span class="sxs-lookup"><span data-stu-id="b5ce3-132">Parameters</span></span>|<span data-ttu-id="b5ce3-133">Raccolta di parametri della query SQL.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="b5ce3-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="b5ce3-134">AffectedRecords</span></span>|<span data-ttu-id="b5ce3-135">Numero di record interessato dall'ultima operazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="b5ce3-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="b5ce3-136">DbQueryScalar</span></span>

<span data-ttu-id="b5ce3-137">Esegue una query che recupera un singolo valore dal database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="b5ce3-138">Questa classe esegue le relative operazioni in modo asincrono (deriva da <xref:System.Activities.AsyncCodeActivity%601> e usa le relative funzionalità asincrone).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="b5ce3-139">È possibile configurare le informazioni di connessione impostando un nome invariante del provider (`ProviderName`) e la stringa di connessione (`ConnectionString`) o solo usando un nome di configurazione della stringa di connessione (`ConfigFileSectionName`) dal file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="b5ce3-140">La query da eseguire viene configurata nella relativa proprietà `Sql` e i parametri vengono passati tramite la raccolta `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="b5ce3-141">Dopo l'esecuzione di `DbQueryScalar`, il valore scalare viene restituito nell'argomento `Result out` (di tipo `TResult`, definito nella classe di base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="b5ce3-142">Argomento</span><span class="sxs-lookup"><span data-stu-id="b5ce3-142">Argument</span></span>|<span data-ttu-id="b5ce3-143">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-143">Description</span></span>|
|-|-|
|<span data-ttu-id="b5ce3-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-144">ProviderName</span></span>|<span data-ttu-id="b5ce3-145">Nome invariante del provider ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="b5ce3-146">Se viene impostato questo argomento, è necessario impostare anche `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b5ce3-147">ConnectionString</span></span>|<span data-ttu-id="b5ce3-148">Stringa di connessione per connettersi al database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-148">Connection string to connect to the database.</span></span> <span data-ttu-id="b5ce3-149">Se viene impostato questo argomento, è necessario impostare anche `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-150">ConfigName</span></span>|<span data-ttu-id="b5ce3-151">Nome della sezione del file di configurazione in cui sono archiviate le informazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="b5ce3-152">Quando viene impostato questo argomento, `ProviderName` e `ConnectionString` non sono richiesti.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="b5ce3-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="b5ce3-153">CommandType</span></span>|<span data-ttu-id="b5ce3-154">Tipo di <xref:System.Data.Common.DbCommand> da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="b5ce3-155">Sql</span><span class="sxs-lookup"><span data-stu-id="b5ce3-155">Sql</span></span>|<span data-ttu-id="b5ce3-156">Comando SQL da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="b5ce3-157">Parametri</span><span class="sxs-lookup"><span data-stu-id="b5ce3-157">Parameters</span></span>|<span data-ttu-id="b5ce3-158">Raccolta di parametri della query SQL.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="b5ce3-159">Risultato</span><span class="sxs-lookup"><span data-stu-id="b5ce3-159">Result</span></span>|<span data-ttu-id="b5ce3-160">Valore scalare ottenuto dopo l'esecuzione della query.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="b5ce3-161">Questo argomento è di tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="b5ce3-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="b5ce3-162">DbQuery</span></span>

<span data-ttu-id="b5ce3-163">Esegue una query che recupera un elenco di oggetti.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="b5ce3-164">Dopo l'esecuzione della query, viene eseguita una funzione di mapping (può essere <xref:System.Func%601><`DbDataReader`, `TResult`> o <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="b5ce3-165">Questa funzione di mapping ottiene un record in un oggetto `DbDataReader` e ne esegue il mapping all'oggetto da restituire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="b5ce3-166">È possibile configurare le informazioni di connessione impostando un nome invariante del provider (`ProviderName`) e la stringa di connessione (`ConnectionString`) o solo usando un nome di configurazione della stringa di connessione (`ConfigFileSectionName`) dal file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="b5ce3-167">La query da eseguire viene configurata nella relativa proprietà `Sql` e i parametri vengono passati tramite la raccolta `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="b5ce3-168">I risultati della query SQL vengono recuperati usando un oggetto `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="b5ce3-169">L'attività scorre `DbDataReader` ed esegue il mapping delle righe in `DbDataReader` a un'istanza di `TResult`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="b5ce3-170">L'utente di `DbQuery` deve fornire il codice di mapping. questa operazione può essere eseguita in due modi: usando un <xref:System.Func%601><`DbDataReader`, `TResult`> o <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="b5ce3-171">Nel primo caso, il mapping viene eseguito in un singolo impulso.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="b5ce3-172">È pertanto più veloce, ma non può essere serializzato in XAML.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="b5ce3-173">Nel secondo caso, il mapping viene eseguito in più impulsi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="b5ce3-174">Può quindi risultare più lento, ma può essere serializzato in XAML e modificato in modo dichiarativo (qualsiasi attività esistente può partecipare al mapping).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="b5ce3-175">Argomento</span><span class="sxs-lookup"><span data-stu-id="b5ce3-175">Argument</span></span>|<span data-ttu-id="b5ce3-176">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-176">Description</span></span>|
|-|-|
|<span data-ttu-id="b5ce3-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-177">ProviderName</span></span>|<span data-ttu-id="b5ce3-178">Nome invariante del provider ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="b5ce3-179">Se viene impostato questo argomento, è necessario impostare anche `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b5ce3-180">ConnectionString</span></span>|<span data-ttu-id="b5ce3-181">Stringa di connessione per connettersi al database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-181">Connection string to connect to the database.</span></span> <span data-ttu-id="b5ce3-182">Se viene impostato questo argomento, è necessario impostare anche `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-183">ConfigName</span></span>|<span data-ttu-id="b5ce3-184">Nome della sezione del file di configurazione in cui sono archiviate le informazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="b5ce3-185">Quando viene impostato questo argomento, `ProviderName` e `ConnectionString` non sono richiesti.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="b5ce3-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="b5ce3-186">CommandType</span></span>|<span data-ttu-id="b5ce3-187">Tipo di <xref:System.Data.Common.DbCommand> da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="b5ce3-188">Sql</span><span class="sxs-lookup"><span data-stu-id="b5ce3-188">Sql</span></span>|<span data-ttu-id="b5ce3-189">Comando SQL da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="b5ce3-190">Parametri</span><span class="sxs-lookup"><span data-stu-id="b5ce3-190">Parameters</span></span>|<span data-ttu-id="b5ce3-191">Raccolta di parametri della query SQL.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="b5ce3-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="b5ce3-192">Mapper</span></span>|<span data-ttu-id="b5ce3-193">Funzione di mapping (<xref:System.Func%601><`DbDataReader`, `TResult`>) che accetta un record nel `DataReader` ottenuto come risultato dell'esecuzione della query e restituisce un'istanza di un oggetto di tipo `TResult` da aggiungere alla raccolta di `Result`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="b5ce3-194">In questo caso, il mapping viene eseguito in un singolo impulso, ma non può essere modificato in modo dichiarativo tramite la finestra di progettazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="b5ce3-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="b5ce3-195">MapperFunc</span></span>|<span data-ttu-id="b5ce3-196">Funzione di mapping (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) che accetta un record nel `DataReader` ottenuto come risultato dell'esecuzione della query e restituisce un'istanza di un oggetto di tipo `TResult` da aggiungere alla raccolta di `Result`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="b5ce3-197">In questo caso, il mapping viene eseguito in più impulsi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="b5ce3-198">Questa funzione può essere serializzata in XAML e modificata in modo dichiarativo (qualsiasi attività esistente può partecipare al mapping).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="b5ce3-199">Risultato</span><span class="sxs-lookup"><span data-stu-id="b5ce3-199">Result</span></span>|<span data-ttu-id="b5ce3-200">Elenco di oggetti ottenuto come risultato dell'esecuzione della query e dell'esecuzione della funzione di mapping per ogni record in `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="b5ce3-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="b5ce3-201">DbQueryDataSet</span></span>

<span data-ttu-id="b5ce3-202">Esegue una query che restituisce un oggetto <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b5ce3-203">Questa classe esegue le relative operazioni in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="b5ce3-204">Deriva da <xref:System.Activities.AsyncCodeActivity><`TResult`> e usa le relative funzionalità asincrone.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="b5ce3-205">È possibile configurare le informazioni di connessione impostando un nome invariante del provider (`ProviderName`) e la stringa di connessione (`ConnectionString`) o solo usando un nome di configurazione della stringa di connessione (`ConfigFileSectionName`) dal file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="b5ce3-206">La query da eseguire viene configurata nella relativa proprietà `Sql` e i parametri vengono passati tramite la raccolta `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="b5ce3-207">Dopo l'esecuzione del `DbQueryDataSet` viene restituito `DataSet` nell'argomento `Result out` (di tipo `TResult`, definito nella classe di base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="b5ce3-208">Argomento</span><span class="sxs-lookup"><span data-stu-id="b5ce3-208">Argument</span></span>|<span data-ttu-id="b5ce3-209">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-209">Description</span></span>|
|-|-|
|<span data-ttu-id="b5ce3-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-210">ProviderName</span></span>|<span data-ttu-id="b5ce3-211">Nome invariante del provider ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="b5ce3-212">Se viene impostato questo argomento, è necessario impostare anche `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b5ce3-213">ConnectionString</span></span>|<span data-ttu-id="b5ce3-214">Stringa di connessione per connettersi al database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-214">Connection string to connect to the database.</span></span> <span data-ttu-id="b5ce3-215">Se viene impostato questo argomento, è necessario impostare anche `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="b5ce3-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="b5ce3-216">ConfigName</span></span>|<span data-ttu-id="b5ce3-217">Nome della sezione del file di configurazione in cui sono archiviate le informazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="b5ce3-218">Quando viene impostato questo argomento, `ProviderName` e `ConnectionString` non sono richiesti.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="b5ce3-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="b5ce3-219">CommandType</span></span>|<span data-ttu-id="b5ce3-220">Tipo di <xref:System.Data.Common.DbCommand> da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="b5ce3-221">Sql</span><span class="sxs-lookup"><span data-stu-id="b5ce3-221">Sql</span></span>|<span data-ttu-id="b5ce3-222">Comando SQL da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="b5ce3-223">Parametri</span><span class="sxs-lookup"><span data-stu-id="b5ce3-223">Parameters</span></span>|<span data-ttu-id="b5ce3-224">Raccolta di parametri della query SQL.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="b5ce3-225">Risultato</span><span class="sxs-lookup"><span data-stu-id="b5ce3-225">Result</span></span>|<span data-ttu-id="b5ce3-226"><xref:System.Data.DataSet> ottenuto dopo l'esecuzione della query.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="b5ce3-227">Configurazione delle informazioni di connessione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-227">Configuring Connection Information</span></span>

<span data-ttu-id="b5ce3-228">Tutte le attività DbActivities condividono gli stessi parametri di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="b5ce3-229">Possono essere configurate in due modi:</span><span class="sxs-lookup"><span data-stu-id="b5ce3-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="b5ce3-230">`ConnectionString + InvariantName`: impostare il nome invariante del provider ADO.NET e la stringa di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="b5ce3-231">`ConfigName`: impostare il nome della sezione di configurazione che contiene le informazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="b5ce3-232">Nell'attività:</span><span class="sxs-lookup"><span data-stu-id="b5ce3-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="b5ce3-233">Esecuzione dell'esempio</span><span class="sxs-lookup"><span data-stu-id="b5ce3-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="b5ce3-234">Istruzioni per l'impostazione</span><span class="sxs-lookup"><span data-stu-id="b5ce3-234">Setup instructions</span></span>

<span data-ttu-id="b5ce3-235">In questo esempio viene usato un database.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-235">This sample uses a database.</span></span> <span data-ttu-id="b5ce3-236">Con l'esempio viene fornito uno script di impostazione e caricamento (Setup.cmd) .</span><span class="sxs-lookup"><span data-stu-id="b5ce3-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="b5ce3-237">È necessario eseguire il file dal prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="b5ce3-238">Lo script Setup.cmd richiama il file di script CreateDb.sql che contiene i comandi SQL per l'esecuzione delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5ce3-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="b5ce3-239">Crea un database denominato DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="b5ce3-240">Crea la tabella Ruoli.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-240">Creates the Roles table.</span></span>

- <span data-ttu-id="b5ce3-241">Crea la tabella Employees.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-241">Creates Employees table.</span></span>

- <span data-ttu-id="b5ce3-242">Inserisce tre record nella tabella Ruoli.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="b5ce3-243">Inserisce dodici record nella tabella Employees.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="b5ce3-244">Per eseguire Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="b5ce3-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="b5ce3-245">Aprire un prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-245">Open a command prompt.</span></span>

2. <span data-ttu-id="b5ce3-246">Passare alla cartella di esempio DbActivities.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="b5ce3-247">Digitare "Setup. cmd" e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5ce3-248">Setup.cmd tenta di installare l'esempio nell'istanza di SqlExpress del computer locale.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="b5ce3-249">Se si desidera installarlo in un'altra istanza del server SQL, modificare Setup.cmd specificando il nome della nuova istanza.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="b5ce3-250">Per disinstallare il database di esempio</span><span class="sxs-lookup"><span data-stu-id="b5ce3-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="b5ce3-251">Eseguire Cleanup.cmd dalla cartella di esempio in un prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="b5ce3-252">Per eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="b5ce3-252">To run the sample</span></span>

1. <span data-ttu-id="b5ce3-253">Aprire la soluzione in Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="b5ce3-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="b5ce3-254">Per compilare la soluzione, premere CTRL+MAIUSC+B.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b5ce3-255">Per eseguire l'esempio senza debug, premere CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5ce3-256">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5ce3-257">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b5ce3-258">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5ce3-259">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
