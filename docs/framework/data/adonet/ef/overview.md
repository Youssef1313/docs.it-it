---
title: Cenni preliminari su Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 0934afa96a88b48d8af2d613e83ba793e2f75e71
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248601"
---
# <a name="entity-framework-overview"></a>Panoramica di Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] è un set di tecnologie ADO.NET che supportano lo sviluppo di applicazioni software orientate ai dati. Gli architetti e gli sviluppatori di questo tipo di applicazioni si trovano nella difficile condizione di dover realizzare due obiettivi molto diversi tra loro, ovvero la modellazione delle entità, delle relazioni e della logica dei problemi aziendali che sono preposti a risolvere e al tempo stesso la gestione dei motori dei dati usati per archiviare e recuperare i dati stessi. Dal momento che i dati potrebbero essere distribuiti in più sistemi di archiviazione, ciascuno con i suoi protocolli, è necessario che nelle applicazioni che gestiscono un solo sistema di archiviazione venga rispettato l'equilibrio tra i requisiti del sistema di archiviazione e i requisiti di scrittura di codice dell'applicazione efficiente e gestibile.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] consente agli sviluppatori di utilizzare i dati sotto forma di proprietà e oggetti specifici di un dominio, ad esempio clienti e indirizzi dei clienti, indipendentemente dalle colonne e dalle tabelle di database sottostanti in cui sono archiviati. Con [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], gli sviluppatori possono operare a un livello superiore di astrazione quando gestiscono i dati e possono creare e gestire applicazioni orientate ai dati con meno codice rispetto alle applicazioni tradizionali. Poiché è un componente del .NET Framework, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] le applicazioni possono essere eseguite in qualsiasi computer in cui è installato il .NET Framework a partire dalla versione 3,5 SP1. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]

## <a name="give-life-to-models"></a>Dare vita ai modelli
 Un approccio di progettazione comune e consolidato quando si compila un'applicazione o un servizio consiste nel dividere l'applicazione o il servizio in tre parti: un modello di dominio, un modello logico e un modello fisico. Il modello di dominio definisce le entità e le relazioni nel sistema da modellare. Il modello logico per un database relazionale normalizza le entità e le relazioni in tabelle con vincoli di chiave esterna. Il modello fisico gestisce le funzionalità di un determinato motore dei dati specificando dettagli sull'archiviazione come il partizionamento e l'indicizzazione.

 Il modello fisico viene ridefinito dagli amministratori del database per migliorare le prestazioni, ma i programmatori che scrivono il codice delle applicazioni tendono a usare solo il modello logico scrivendo query SQL e chiamando stored procedure. I modelli di dominio vengono in genere usati come strumento per l'acquisizione e la comunicazione dei requisiti di un'applicazione, spesso come diagrammi inerti visualizzati e discussi nelle fasi iniziali di un progetto e quindi abbandonati. Molti team di sviluppo saltano la fase di creazione di un modello concettuale e partono direttamente dall'indicazione di tabelle, colonne e chiavi in un database relazionale.

 Consente agli sviluppatori di eseguire query su entità e relazioni nel modello di dominio (denominato modello *concettuale* in [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e di tradurre tali operazioni nell'origine dati. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] comandi specifici. Le applicazioni non sono quindi più vincolate a dipendenze hard-coded su una determinata origine dati.

 Quando si usa Code First, viene eseguito il mapping del modello concettuale al modello di archiviazione nel codice. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] può dedurre il modello concettuale in base ai tipi di oggetto e alle configurazioni aggiuntive definite. I metadati di mapping vengono generati in fase di esecuzione in base a una combinazione della modalità di definizione dei tipi di dominio e delle informazioni di configurazione aggiuntive fornite nel codice. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] genera il database secondo le necessità in base ai metadati. Per ulteriori informazioni, vedere [creazione e mapping di un modello concettuale](https://go.microsoft.com/fwlink/?LinkID=235382).

 Quando si usano gli strumenti di Entity Data Model, il modello concettuale, il modello di archiviazione e i mapping tra i due vengono espressi in schemi basati su XML e definiti in file con estensioni corrispondenti:

- Il linguaggio CSDL (Conceptual Schema Definition Language) definisce il modello concettuale. CSDL è l' [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]implementazione di dell' [Entity Data Model](../entity-data-model.md). L'estensione del file è csdl.

- Il linguaggio SSDL (Store Schema Definition Language) definisce il modello di archiviazione, chiamato anche modello logico. L'estensione del file è ssdl.

- Il linguaggio MSL (Mapping Specification Language) definisce i mapping tra il modello di archiviazione e il modello concettuale. L'estensione del file è msl.

Il modello di archiviazione e i mapping possono essere modificati in base alle esigenze senza che sia necessario modificare il modello concettuale, le classi di dati o il codice dell'applicazione. Poiché i modelli di archiviazione sono specifici del provider, è possibile usare un modello concettuale coerente in varie origini dati.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Usa questi file di modello e di mapping per creare, leggere, aggiornare ed eliminare operazioni su entità e relazioni nel modello concettuale per eseguire operazioni equivalenti nell'origine dati. Supporta [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] anche il mapping di entità nel modello concettuale alle stored procedure nell'origine dati. Per ulteriori informazioni, vedere le [Specifiche CSDL, SSDL e MSL](./language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Eseguire il mapping di oggetti ai dati
 La programmazione orientata a oggetti pone una serie di sfide relativamente all'interazione con i sistemi di archiviazione dei dati. Anche se l'organizzazione delle classi in genere rispecchia l'organizzazione delle tabelle dei database relazionali, non si può parlare di una corrispondenza esatta. Più tabelle normalizzate corrispondono spesso a una singola classe e le relazioni tra classi sono spesso rappresentate in modo diverso rispetto alle relazioni tra tabelle. Per rappresentare il cliente per un determinato ordine, ad esempio, una classe `Order` potrebbe usare una proprietà contenente un riferimento a un'istanza di una classe `Customer`, mentre una riga della tabella `Order` in un database contiene una colonna o un set di colonne di chiave esterna con un valore che corrisponde a un valore di chiave primaria nella tabella `Customer`. Una classe `Customer` potrebbe disporre di una proprietà denominata `Orders` contenente una raccolta di istanze della classe `Order`, mentre la tabella `Customer` in un database non include colonne confrontabili. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] offre agli sviluppatori la flessibilità per rappresentare relazioni in questo modo o per modellare con maggiore precisione le relazioni come vengono rappresentate nel database.

 Le soluzioni esistenti hanno tentato di colmare questo divario, spesso definito "mancata corrispondenza dell'impedenza" eseguendo solo il mapping di classi e proprietà orientate a oggetti a tabelle e colonne relazionali. Anziché adottare questo approccio tradizionale, il esegue [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] il mapping di tabelle relazionali, colonne e vincoli di chiave esterna nei modelli logici a entità e relazioni nei modelli concettuali. Il risultato ottenuto è una maggiore flessibilità nella definizione degli oggetti e nell'ottimizzazione del modello logico. Gli strumenti di Entity Data Model generano classi di dati estendibili basate sul modello concettuale. Queste classi sono classi parziali che è possibile estendere con membri altri aggiunti dallo sviluppatore. Per impostazione predefinita, le classi generate per un particolare modello concettuale derivano da classi di base che forniscono servizi per la materializzazione di entità come oggetti e per il rilevamento e il salvataggio delle modifiche. Queste classi possono essere usate dagli sviluppatori per gestire le entità e le relazioni come oggetti correlati da associazioni. Gli sviluppatori possono inoltre personalizzare le classi generate per un modello concettuale. Per ulteriori informazioni, vedere [utilizzo di oggetti](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Accedere ai dati di entità e modificarli

Oltre a rappresentare una soluzione di mapping relazionale a oggetti, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] è uno strumento che consente alle applicazioni di accedere e modificare i dati rappresentati come entità e relazioni nel modello concettuale. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilizza le informazioni nei file del modello e di mapping per tradurre le query di oggetto eseguite su tipi di entità rappresentati nel modello concettuale in query specifiche dell'origine dati. I risultati della [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] query vengono materializzati in oggetti gestiti da. In [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sono disponibili i metodi seguenti per eseguire una query su un modello concettuale e restituire oggetti:

- LINQ to Entities. Fornisce supporto LINQ (Language Integrated Query) per l'esecuzione di query sui tipi di entità definiti in un modello concettuale. Per ulteriori informazioni, vedere [LINQ to Entities](./language-reference/linq-to-entities.md).

- [https://login.microsoftonline.com/common/]([!INCLUDE[esql](../../../../../includes/esql-md.md)]). Sottolinguaggio SQL indipendente dall'archiviazione che interagisce direttamente con le entità del modello concettuale e che supporta Entity Data Model concetti. [!INCLUDE[esql](../../../../../includes/esql-md.md)]viene utilizzato sia con query di oggetto che con query eseguite tramite il provider EntityClient. Per ulteriori informazioni, vedere [Entity SQL Overview](./language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] include il provider di dati EntityClient. Tale provider gestisce connessioni, converte query di entità in query specifiche dell'origine dati e restituisce un lettore dati usato da [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] per materializzare i dati dell'entità in oggetti. Quando la materializzazione degli oggetti non è richiesta, il provider EntityClient può essere utilizzato anche come un provider di dati ADO.NET standard consentendo alle applicazioni di eseguire query [!INCLUDE[esql](../../../../../includes/esql-md.md)] e di utilizzare il lettore dati di sola lettura restituito. Per ulteriori informazioni, vedere [provider EntityClient per la Entity Framework](entityclient-provider-for-the-entity-framework.md).

Nel diagramma seguente viene illustrata l'architettura di [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] per l'accesso ai dati:

![Diagramma dell'architettura Entity Framework](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Gli strumenti Entity Data Model possono generare una classe derivata da `System.Data.Objects.ObjectContext` o `System.Data.Entity.DbContext` che rappresenta il contenitore di entità nel modello concettuale. Questo contesto dell'oggetto fornisce le funzionalità di registrazione delle modifiche e di gestione di identità, concorrenza e relazioni. Questa classe espone inoltre un metodo `SaveChanges` che scrive inserimenti, aggiornamenti ed eliminazioni nell'origine dati. Analogamente alle query, queste modifiche vengono eseguite da comandi generati automaticamente dal sistema o da stored procedure specificate dallo sviluppatore.

## <a name="data-providers"></a>Provider di dati

Il `EntityClient` provider estende il modello di provider ADO.NET accedendo ai dati in termini di entità e relazioni concettuali. Esegue query che usano [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] fornisce il linguaggio di query sottostante che consente la comunicazione di `EntityClient` con il database. Per ulteriori informazioni, vedere [provider EntityClient per la Entity Framework](entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] include un provider di dati SqlClient aggiornato che supporta gli alberi dei comandi canonici. Per ulteriori informazioni, vedere [SqlClient per la Entity Framework](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Strumenti di Entity Data Model

Insieme al [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] runtime di, Visual Studio include gli strumenti di mapping e di modellazione. Per altre informazioni, vedere [modellazione e mapping](modeling-and-mapping.md).

## <a name="learn-more"></a>Altre informazioni

Per ulteriori informazioni su [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vedere:

[Introduzione](getting-started.md) : vengono fornite informazioni su come iniziare a usare rapidamente la [Guida introduttiva](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), in cui viene illustrato come creare un' [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] applicazione semplice.

[Entity Framework terminologia](terminology.md) : definisce molti dei termini introdotti dal Entity Data Model e [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e usati nella [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentazione.

[Risorse Entity Framework](resources.md) : fornisce collegamenti ad argomenti concettuali e collegamenti ad argomenti e risorse esterni per la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] compilazione di applicazioni.

## <a name="see-also"></a>Vedere anche

- [ADO.NET Entity Framework](index.md)
