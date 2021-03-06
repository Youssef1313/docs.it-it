---
title: Cenni preliminari su LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794972"
---
# <a name="linq-to-dataset-overview"></a>Cenni preliminari su LINQ to DataSet
<xref:System.Data.DataSet> È uno dei componenti più diffusi di ADO.NET. Si tratta di un elemento chiave del modello di programmazione disconnesso su cui si basa ADO.NET e consente di memorizzare in modo esplicito i dati da origini dati diverse. Per il livello della presentazione <xref:System.Data.DataSet> è strettamente integrato nei controlli GUI per il data binding. Per il livello intermedio fornisce una cache che mantiene la forma relazionale dei dati e include servizi di navigazione all'interno della gerarchia e di query semplici e rapidi. Una tecnica comune utilizzata per ridurre il numero di richieste in un database consiste nell'utilizzare per <xref:System.Data.DataSet> la memorizzazione nella cache nel livello intermedio. Si consideri, ad esempio, un'applicazione Web ASP.NET basata sui dati. Spesso, una parte significativa dei dati dell'applicazione non viene modificata frequentemente ed è comune a più sessioni o utenti. Tali dati possono essere mantenuti in memoria sul server Web, in modo da ridurre il numero di richieste al database e velocizzare le interazioni utente. Un altro aspetto utile di <xref:System.Data.DataSet> è che consente a un'applicazione di portare subset di dati da una o più origini dati nello spazio dell'applicazione. L'applicazione può quindi modificare i dati in memoria, mantenendo comunque la propria forma relazionale.  
  
 Nonostante l'importanza che lo contraddistingue, <xref:System.Data.DataSet> dispone di funzionalità limitate di query. È possibile usare il metodo <xref:System.Data.DataTable.Select%2A> per il filtro e l'ordinamento e i metodi <xref:System.Data.DataRow.GetChildRows%2A> e <xref:System.Data.DataRow.GetParentRow%2A> per la navigazione all'interno della gerarchia. Per operazioni più complesse, tuttavia, lo sviluppatore deve scrivere una query personalizzata. Le applicazioni risultanti possono quindi essere difficilmente gestibili e caratterizzate da prestazioni inadeguate.  
  
 LINQ to DataSet semplifica e velocizza l'esecuzione di query sui dati memorizzati nella cache <xref:System.Data.DataSet> in un oggetto. Queste query sono espresse nel linguaggio di programmazione stesso, anziché come valori letterali stringa incorporati nel codice dell'applicazione. Gli sviluppatori non devono pertanto imparare un diverso linguaggio di query. Inoltre, LINQ to DataSet consente agli sviluppatori di Visual Studio di lavorare in modo più produttivo, perché l'IDE di Visual Studio fornisce il controllo della sintassi in fase di compilazione, [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]la tipizzazione statica e il supporto IntelliSense per. LINQ to DataSet può essere utilizzato anche per eseguire query su dati che sono stati consolidati da una o più origini dati. In tal modo sono possibili molti scenari in cui è necessario poter rappresentare e gestire i dati con flessibilità. In particolare, questo tipo di modifiche sono richieste nelle applicazioni generiche per la creazione di rapporti, di analisi e di Business Intelligence.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Esecuzione di query su DataSet con LINQ to DataSet  
 Prima di poter iniziare a eseguire query <xref:System.Data.DataSet> su un oggetto utilizzando LINQ to DataSet, è necessario <xref:System.Data.DataSet>popolare. Esistono diversi modi per caricare i dati in un <xref:System.Data.DataSet>oggetto, ad esempio usando <xref:System.Data.Common.DataAdapter> la classe o [LINQ to SQL](./sql/linq/index.md). Dopo che i dati sono stati caricati in <xref:System.Data.DataSet> un oggetto, è possibile iniziare a eseguire una query su di esso. La formulazione di query con LINQ to DataSet è simile [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] all'utilizzo [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]di su altre origini dati abilitate. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]è possibile eseguire query su singole tabelle in un <xref:System.Data.DataSet> oggetto o su più di una tabella utilizzando gli <xref:System.Linq.Enumerable.Join%2A> operatori <xref:System.Linq.Enumerable.GroupJoin%2A> di query standard e.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]le query sono supportate per <xref:System.Data.DataSet> gli oggetti tipizzati e non tipizzati. Se si conosce lo schema di <xref:System.Data.DataSet> in fase di progettazione dell'applicazione, è consigliabile utilizzare <xref:System.Data.DataSet> tipizzati. In un <xref:System.Data.DataSet> tipizzato, per ciascuna colonna delle tabelle e delle righe sono disponibili membri tipizzati, pertanto le query risultano più semplici e più leggibili.  
  
 Oltre agli operatori di query standard implementati in System. Core. dll, LINQ to DataSet aggiunge diverse <xref:System.Data.DataSet>estensioni specifiche che semplificano l'esecuzione di query su un set di <xref:System.Data.DataRow> oggetti. Le estensioni specifiche di <xref:System.Data.DataSet> includono operatori per il confronto di sequenze di righe, nonché metodi che forniscono accesso ai valori di colonna di un oggetto <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Applicazioni a più livelli e LINQ to DataSet  
 Le applicazioni dati a più livelli sono applicazioni mirate ai dati separate in più livelli logici. Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, Per altre informazioni sulle applicazioni dati a più livelli, vedere [usare i set di dati nelle applicazioni a più livelli](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 Nelle applicazioni a più livelli <xref:System.Data.DataSet> viene spesso usato nel livello intermedio per memorizzare nella cache le informazioni per un'applicazione Web. La funzionalità di query LINQ to DataSet viene implementata tramite i metodi di estensione ed estende il <xref:System.Data.DataSet>ADO.NET 2,0 esistente.  
  
## <a name="see-also"></a>Vedere anche

- [Esecuzione di query su oggetti DataSet](querying-datasets-linq-to-dataset.md)
- [LINQ (Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
