---
title: Creare un client REST usando .NET Core
description: Questa esercitazione illustra alcune funzionalità disponibili in .NET Core e nel linguaggio C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850971"
---
# <a name="rest-client"></a>Client REST

## <a name="introduction"></a>Introduzione

Questa esercitazione illustra alcune funzionalità disponibili in .NET Core e nel linguaggio C#. Verranno affrontati gli argomenti seguenti:

* Nozioni di base sull'interfaccia della riga di comando di .NET Core
* Panoramica delle funzionalità del linguaggio C#
* Gestione delle dipendenze con NuGet
* Comunicazioni HTTP
* Elaborazione delle informazioni JSON
* Gestione della configurazione con attributi

Si creerà un'applicazione che invia richieste HTTP a un servizio REST su GitHub, si leggeranno informazioni in formato JSON e si convertirà il pacchetto JSON in oggetti C#. Si imparerà infine a usare e gestire oggetti C#.

In questa esercitazione verranno create anche numerose funzionalità.

Se si vuole proseguire, è possibile scaricare l'[esempio finale](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) di questo argomento. Per istruzioni sul download, vedere [Esempi ed esercitazioni](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Prerequisiti

È necessario configurare il computer per l'esecuzione di .NET core. È possibile trovare le istruzioni di installazione nella pagina di [download di .NET Core](https://dotnet.microsoft.com/download) . Questa applicazione può essere eseguita in Windows, Linux, macOS o in un contenitore Docker.
È necessario installare l'editor di codice preferito. Nelle descrizioni seguenti viene usato [Visual Studio Code](https://code.visualstudio.com/), un editor open source multipiattaforma, ma è possibile usare gli strumenti con cui si ha maggiore familiarità.

## <a name="create-the-application"></a>Creare l'applicazione

Il primo passaggio consiste nel creare una nuova applicazione. Aprire un prompt dei comandi e creare una nuova directory per l'applicazione, impostandola come directory corrente. Digitare il comando `dotnet new console` al prompt dei comandi Questa operazione crea i file iniziali per un'applicazione "Hello World" di base. Poiché si tratta di un nuovo progetto, non è presente alcuna dipendenza, quindi la prima esecuzione scarica .NET Core Framework, installa un certificato di sviluppo ed esegue la gestione pacchetti NuGet per ripristinare le dipendenze mancanti.

Prima di iniziare ad apportare modifiche, digitare `dotnet run` ([vedere la nota](#dotnet-restore-note)) al prompt dei comandi per eseguire l'applicazione. `dotnet run` esegue automaticamente `dotnet restore` se nell'ambiente mancano dipendenze. Esegue anche `dotnet build` se l'applicazione deve essere ricompilata.
Dopo l'installazione iniziale, sarà necessario solo eseguire `dotnet restore` o `dotnet build` quando ha senso per il progetto.

## <a name="adding-new-dependencies"></a>Aggiunta di nuove dipendenze

Uno degli obiettivi di progettazione principali di .NET Core è ridurre al minimo le dimensioni dell'installazione di .NET. Se per alcune delle funzionalità di un'applicazione sono necessarie altre librerie, è possibile aggiungere tali dipendenze al file di progetto C# (\*.csproj). Per questo esempio sarà necessario aggiungere il pacchetto `System.Runtime.Serialization.Json` per consentire all'applicazione di elaborare le risposte JSON.

Aprire il file di progetto `csproj`. La prima riga del file dovrebbe essere simile alla seguente:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Subito dopo la riga aggiungere il codice seguente:

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

La maggior parte degli editor di codice offre funzioni di completamento per le diverse versioni di queste librerie. Si preferisce in genere usare la versione più recente dei pacchetti da aggiungere. È importante tuttavia verificare che le versioni di tutti i pacchetti corrispondano tra loro e con la versione del framework dell'applicazione .NET Core.

Dopo aver apportato queste modifiche, eseguire `dotnet restore` ([vedere la nota](#dotnet-restore-note)) per consentire l'installazione del pacchetto nel sistema.

## <a name="making-web-requests"></a>Esecuzione di richieste Web

Si è ora pronti per iniziare a recuperare dati dal Web. In questa applicazione si leggeranno informazioni dall'[API GitHub](https://developer.github.com/v3/). In particolare, si leggeranno informazioni sui progetti nell'ambito di [.NET Foundation](https://www.dotnetfoundation.org/). Si inizierà inviando all'API GitHub la richiesta di recuperare informazioni sui progetti. L'endpoint che verrà usato è: <https://api.github.com/orgs/dotnet/repos>. Poiché si vuole recuperare tutte le informazioni su questi progetti, si userà una richiesta HTTP GET.
Anche il browser usa richieste HTTP GET ed è quindi possibile incollare l'URL nel browser per visualizzare le informazioni che si riceveranno ed elaboreranno.

Per eseguire richieste Web, usare la classe <xref:System.Net.Http.HttpClient>. Come tutte le API .NET moderne, <xref:System.Net.Http.HttpClient> supporta solo metodi asincroni per le API a esecuzione prolungata.
È quindi necessario iniziare creando un metodo asincrono, che verrà inserito nell'implementazione mentre si compila la funzionalità dell'applicazione. Iniziare aprendo il file `program.cs` nella directory del progetto e aggiungendo il metodo seguente alla classe `Program`:

```csharp
private static async Task ProcessRepositories()
{
}
```

Aggiungere quindi un'istruzione `using` all'inizio del metodo `Main`, in modo che il compilatore C# riconosca il tipo <xref:System.Threading.Tasks.Task>:

```csharp
using System.Threading.Tasks;
```

Se si compila il progetto in questo momento, viene generato un avviso per indicare che il metodo non contiene alcun operatore `await` e verrà quindi eseguito in modo sincrono. Ignorare temporaneamente il messaggio. Si aggiungeranno operatori `await` durante la compilazione del metodo.

Rinominare quindi lo spazio dei nomi definito nell'istruzione `namespace` sostituendo `ConsoleApp` (nome predefinito) con `WebAPIClient`. In questo spazio dei nomi si definirà in seguito una classe `repo`.

Aggiornare quindi il metodo `Main` per chiamare questo metodo. Il metodo `ProcessRepositories` restituisce un'attività ed è necessario non uscire dal programma prima che questa sia completata. Usare quindi il metodo `Wait` per bloccare il processo e attendere il completamento dell'attività:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Si dispone a questo punto di un programma che, pur non eseguendo alcuna operazione, opera in modo asincrono. È ora possibile migliorarlo.

È necessario innanzitutto un oggetto in grado di recuperare i dati dal Web; a tale scopo è possibile usare <xref:System.Net.Http.HttpClient>. per gestire la richiesta e le risposte. Creare un'istanza di una singola istanza del tipo nella classe `Program` all'interno del file Program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

Tornare quindi al metodo `ProcessRepositories` e compilarne una prima versione:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Sarà inoltre necessario aggiungere due nuove istruzioni using all'inizio del file per consentirne la compilazione:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Questa prima versione esegue una richiesta Web per leggere l'elenco di tutti i repository presenti nell'organizzazione DotNet Foundation. L'ID di GitHub per .NET Foundation è 'dotnet'. Nelle prime righe l'oggetto <xref:System.Net.Http.HttpClient> viene impostato per questa richiesta, ma prima viene configurato per accettare le risposte JSON di GitHub.
Questo formato è semplicemente JSON. Nella riga successiva viene aggiunta un'intestazione Agente utente a tutte le richieste provenienti da questo oggetto. Queste due intestazioni vengono controllate dal codice server di GitHub e sono necessarie per recuperare informazioni da GitHub.

Dopo aver configurato l'oggetto <xref:System.Net.Http.HttpClient>, si eseguirà una richiesta Web e si recupererà la risposta. In questa prima versione viene usato il metodo pratico <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>. Questo metodo avvia un'attività che esegue la richiesta Web e, quando la richiesta viene restituita, legge il flusso di risposta e ne estrae il contenuto. Il corpo della risposta viene restituito come <xref:System.String>. La stringa è disponibile quando l'attività viene completata.

Le ultime due righe di questo metodo attendono che l'attività sia completata e visualizzano la risposta nella console.
Compilare l'app ed eseguirla. Il messaggio di avviso non viene più visualizzato perché `ProcessRepositories` contiene ora un operatore `await`. Verrà visualizzata una lunga schermata di testo JSON formattato.

## <a name="processing-the-json-result"></a>Elaborazione del risultato JSON

A questo punto è stato scritto il codice per recuperare una risposta da un server Web e visualizzare il testo contenuto nella risposta. Si convertirà ora la risposta JSON in oggetti C#.

Per convertire dati JSON in oggetti C# è possibile usare il serializzatore JSON. La prima attività consisterà nel definire un tipo di classe C# in cui saranno contenute le informazioni usate dalla risposta. Questa operazione verrà eseguita passo dopo passo e si inizierà con un tipo C# semplice contenente il nome del repository:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

Inserire il codice precedente in un nuovo file denominato 'repo.cs'. Questa versione della classe rappresenta il percorso più semplice per elaborare dati JSON. Il nome della classe e il nome del membro corrispondono ai nomi usati nel pacchetto JSON, anziché alle convenzioni C# seguenti. Questo errore verrà risolto in un secondo momento specificando alcuni attributi di configurazione. Questa classe illustra un'altra importante caratteristica della serializzazione e deserializzazione JSON: non tutti i campi del pacchetto JSON fanno parte di questa classe.
Il serializzatore JSON ignorerà le informazioni non incluse nel tipo di classe in uso.
In questo modo sarà più semplice creare tipi compatibili con un solo subset dei campi presenti nel pacchetto JSON.

Dopo aver creato il tipo, è possibile deserializzarlo. Sarà quindi necessario creare un oggetto <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, che deve conoscere il tipo CLR previsto per il pacchetto JSON che recupera. Il pacchetto di GitHub contiene una sequenza di repository e quindi `List<repo>` è il tipo corretto. Aggiungere la riga seguente al metodo `ProcessRepositories`:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Si useranno due nuovi spazi dei nomi e sarà quindi necessario aggiungere anche questi:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Si userà infine il serializzatore per convertire i dati JSON in oggetti C#. Sostituire la chiamata a <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> nel metodo `ProcessRepositories` con le due righe seguenti:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Si noti che ora viene usato <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> anziché <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Il serializzatore usa un flusso anziché una stringa come origine. Verranno ora illustrate alcune funzionalità del linguaggio C# usate nella seconda riga sopra riportata. L'argomento per <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> è un'espressione `await`. Le espressioni await possono essere presenti quasi ovunque nel codice, anche se finora sono apparse solo nell'ambito di un'istruzione di assegnazione.

Inoltre, l'operatore `as` esegue la conversione del tipo in fase di compilazione da `object` a `List<repo>`.
La dichiarazione di <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> indica che viene restituito un oggetto di tipo <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> restituirà il tipo specificato al momento della costruzione (`List<repo>` in questa esercitazione). Se la conversione non riesce, l'operatore `as` restituisce `null` anziché generare un'eccezione.

Questa sezione è quasi completata. Ora che i dati JSON sono stati convertiti in oggetti C#, verrà visualizzato il nome di ogni repository. Sostituire le righe seguenti:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

con il codice seguente:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Compilare l'applicazione ed eseguirla. Verranno stampati i nomi dei repository che fanno parte di .NET Foundation.

## <a name="controlling-serialization"></a>Controllo della serializzazione

Prima di aggiungere altre funzionalità, è necessario indirizzare il tipo `repo` e renderlo conforme ad altre convenzioni C# standard. A questo scopo, è necessario annotare il tipo `repo` con *attributi* che controllano il funzionamento del serializzatore JSON. In questo caso, si useranno questi attributi per definire un mapping tra i nomi di chiavi JSON e i nomi di membri e classi C#. In particolare, verranno usati i due attributi <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>. Per convenzione, tutte le classi di attributo terminano con il suffisso `Attribute`. Questo suffisso, tuttavia, non deve essere necessariamente usato quando si applica un attributo.

Gli attributi <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> si trovano in un'altra libreria che sarà necessario aggiungere al file di progetto C# come dipendenza. Aggiungere la riga seguente alla sezione `<ItemGroup>` del file di progetto:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Dopo aver salvato il file, eseguire `dotnet restore` ([vedere la nota](#dotnet-restore-note)) per recuperare il pacchetto.

Aprire quindi il file `repo.cs`. È possibile modificare il nome in modo da usare la convenzione Pascal e specificare il nome completo `Repository`. Si vuole ora eseguire il mapping dei nodi 'repo' di JSON a questo tipo e sarà quindi necessario aggiungere l'attributo <xref:System.Runtime.Serialization.DataContractAttribute> alla dichiarazione di classe. Si imposterà la proprietà `Name` dell'attributo sul nome dei nodi JSON mappati a questo tipo:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> è un membro dello spazio dei nomi <xref:System.Runtime.Serialization> e sarà quindi necessario aggiungere l'istruzione `using` appropriata all'inizio del file:

```csharp
using System.Runtime.Serialization;
```

Il nome della classe `repo` è stato modificato in `Repository` e sarà quindi necessario apportare la stessa modifica in Program.cs. È possibile che alcuni editor supportino un refactoring di ridenominazione in virtù del quale questa modifica verrebbe apportata in modo automatico.

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Si apporterà quindi la stessa modifica per il campo `name` usando la classe <xref:System.Runtime.Serialization.DataMemberAttribute>. A questo scopo, eseguire le modifiche seguenti alla dichiarazione del campo `name` in repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Con questa operazione si modifica il codice che scrive il nome di ogni repository in program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Eseguire un comando `dotnet build` seguito da un comando `dotnet run` per assicurarsi che i mapping siano stati eseguiti correttamente. L'output ottenuto dovrebbe essere uguale a quello precedente. Prima di elaborare altre proprietà del server Web è necessario apportare un'altra modifica alla classe `Repository`. Il membro `Name` è un campo accessibile pubblicamente. Non essendo questa una prassi raccomandabile nella programmazione orientata agli oggetti, si trasformerà il membro in una proprietà. Ai fini di questa esercitazione, non è necessario eseguire alcun codice specifico per ottenere o impostare la proprietà, ma la conversione in una proprietà consente di aggiungere più facilmente eventuali modifiche in un secondo momento, senza dover modificare il codice che usa la classe `Repository`.

Rimuovere la definizione di campo e sostituirla con una [proprietà implementata automaticamente](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Il compilatore genera il corpo delle funzioni di accesso `get` e `set`, oltre a un campo privato in cui archiviare il nome, con un codice simile al seguente, che è possibile digitare anche manualmente:

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Si apporterà di seguito un'ultima modifica prima di aggiungere nuove funzionalità. Il metodo `ProcessRepositories` può operare in modo asincrono e restituire una raccolta di repository. È ora necessario fare in modo che il metodo restituisca `List<Repository>` e spostare il codice che scrive le informazioni nel metodo `Main`.

Modificare la firma di `ProcessRepositories` in modo da restituire un'attività il cui risultato sia un elenco di oggetti `Repository`:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Restituire quindi i repository dopo aver elaborato la risposta JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Il compilatore genera l'oggetto `Task<T>` come elemento restituito perché il metodo è stato contrassegnato come `async`.
Si modificherà ora il metodo `Main` in modo che acquisisca i risultati e scriva ogni nome di repository nella console. Il metodo `Main` avrà ora un aspetto simile al seguente:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

L'accesso alla proprietà `Result` di un'attività è bloccato fino al completamento dell'attività. In genere, si preferisce attendere il completamento dell'attività con un'espressione `await`, come nel metodo `ProcessRepositories`, ma questa possibilità non è prevista nel metodo `Main`.

## <a name="reading-more-information"></a>Lettura di altre informazioni

Per completare l'esercitazione si elaboreranno ora altre proprietà del pacchetto JSON inviato dall'API di GitHub. Non si intende acquisire tutte le informazioni possibili ma, aggiungendo alcune proprietà, sarà possibile illustrare qualche altra funzionalità del linguaggio C#.

Si inizierà aggiungendo altri tipi semplici alla definizione di classe `Repository`. Aggiungere quindi alla classe le proprietà seguenti:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

In queste proprietà sono incorporate conversioni dal tipo stringa (il contenuto dei pacchetti JSON) al tipo di destinazione. Il tipo <xref:System.Uri>, che per alcuni utenti può essere nuovo, rappresenta un URI o, come in questo caso, un URL. Nel caso dei tipi `Uri` e `int`, se il pacchetto JSON contiene dati che non possono essere convertiti nel tipo di destinazione, l'azione di serializzazione genererà un'eccezione.

Dopo aver aggiunto queste proprietà, aggiornare il metodo `Main` per visualizzare gli elementi seguenti:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Come passaggio conclusivo si aggiungeranno le informazioni necessarie per l'ultima operazione push, formattate nella risposta JSON come illustrato di seguito:

```json
2016-02-08T21:27:00Z
```

Questo formato non segue nessuno dei formati .NET <xref:System.DateTime> standard e, pertanto, sarà necessario scrivere un metodo di conversione personalizzato. Probabilmente si vorrà evitare anche che la stringa non elaborata sia esposta agli utenti della classe `Repository`. Gli attributi possono essere utili per controllare anche questo aspetto. È necessario prima definire una proprietà `private` che contenga la rappresentazione stringa del valore data/ora della classe `Repository`:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

L'attributo <xref:System.Runtime.Serialization.DataMemberAttribute> informa il serializzatore che questo elemento deve essere elaborato, anche se non è un membro pubblico. Sarà quindi necessario scrivere una proprietà pubblica di sola lettura che converta la stringa in un oggetto <xref:System.DateTime> valido e restituisca il valore <xref:System.DateTime> specificato:

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Relativamente ai nuovi costrutti sopra riportati, l'attributo `IgnoreDataMember` informa il serializzatore che questo tipo non deve essere letto o scritto da qualsiasi oggetto JSON. Questa proprietà contiene solo una funzione di accesso `get`. Non è presente alcuna funzione di accesso `set`. Ecco come definire una proprietà di *sola lettura* in C#. È possibile creare anche proprietà di *sola scrittura* in C#, ma con un valore limitato. Il metodo <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizza una stringa e crea prima un oggetto <xref:System.DateTime> usando un formato di data specificato e quindi aggiunge altri metadati a `DateTime` usando un oggetto `CultureInfo`. Se l'operazione di analisi ha esito negativo, la funzione di accesso della proprietà genera un'eccezione.

Per usare <xref:System.Globalization.CultureInfo.InvariantCulture> sarà necessario aggiungere lo spazio dei nomi <xref:System.Globalization> alle istruzioni `using` in `repo.cs`:

```csharp
using System.Globalization;
```

Dopo aver aggiunto un'altra istruzione di output alla console, sarà possibile compilare ed eseguire nuovamente l'app:

```csharp
Console.WriteLine(repo.LastPush);
```

La versione dell'app dovrebbe ora corrispondere all'[esempio completo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Conclusione

In questa esercitazione sono state descritte le procedure necessarie per eseguire richieste Web, analizzare i risultati e visualizzare le proprietà dei risultati. Sono stati inoltre aggiunti nuovi pacchetti come dipendenze del progetto e sono state illustrate alcune delle funzionalità del linguaggio C# che supportano tecniche orientate agli oggetti.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
