---
title: Isolamento dello snapshot in SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 9f9dfd4f1f299817aa424716aac4408a0b77a240
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958004"
---
# <a name="snapshot-isolation-in-sql-server"></a>Isolamento dello snapshot in SQL Server
L'isolamento dello snapshot migliora la concorrenza per le applicazioni OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Informazioni sull'isolamento dello snapshot e il controllo delle versioni delle righe  
 Una volta abilitato l'isolamento dello snapshot, le versioni di riga aggiornate per ogni transazione vengono mantenute in **tempdb**. Ciascuna transazione viene identificata mediante un numero di sequenza univoco. Questi numeri vengono registrati per ciascuna versione di riga. La transazione funziona con le versioni di riga più recenti che dispongono di un numero di sequenza che precede il numero di sequenza della transazione. La transazione ignora le versioni di riga più recenti, create dopo l'inizio della transazione stessa.  
  
 Il termine "snapshot" è dovuto al fatto che tutte le query nella transazione rilevano la stessa versione, o snapshot, del database, in base allo stato del database all'inizio della transazione. In una transazione snapshot non vengono acquisiti blocchi sulle pagine di dati o sulle righe di dati sottostanti. In questo modo è possibile eseguire altre transazioni senza che vengano bloccate da una precedente transazione non completata. Le transazioni di modifica dei dati non bloccano le transazioni di lettura dei dati così come queste ultime non bloccano le transazioni di scrittura dei dati, esattamente come avviene nel livello di isolamento READ COMMITTED in SQL Server. Questo comportamento non bloccante riduce notevolmente la probabilità di blocchi critici per le transazioni complesse.  
  
 L'isolamento dello snapshot usa un modello di concorrenza ottimistica. Se una transazione snapshot tenta di eseguire il commit delle modifiche apportate ai dati dall'inizio della transazione, verrà eseguito il rollback della transazione e verrà generato un errore. Per evitare che questo si verifichi, è possibile usare i suggerimenti UPDLOCK per le istruzioni SELECT che accedono ai dati da modificare. Per altre informazioni, vedere l'argomento relativo agli hint di blocco nella documentazione online di SQL Server.  
  
 L'isolamento dello snapshot deve essere abilitato impostando l'opzione di database ALLOW_SNAPSHOT_ISOLATION ON prima di usarlo per le transazioni. Questo consente di attivare il meccanismo per l'archiviazione delle versioni di riga nel database temporaneo (**tempdb**). È necessario abilitare l'isolamento dello snapshot in ciascun database in cui esso viene usato con l'istruzione ALTER DATABASE di Transact-SQL. In questo senso, l'isolamento dello snapshot differisce dai livelli di isolamento tradizionali di READ COMMITTED, REPEATABLE READ, SERIALIZABLE e READ UNCOMMITTED, che non richiedono alcuna configurazione. Le istruzioni seguenti attivano l'isolamento dello snapshot e sostituiscono il comportamento READ COMMITTED predefinito con SNAPSHOT:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 L'impostazione dell'opzione READ_COMMITTED_SNAPSHOT ON consente di accedere alle righe la cui versione è stata controllata, al livello di isolamento READ COMMITTED predefinito. Se l'opzione READ_COMMITTED_SNAPSHOT è impostata su OFF, per accedere alle righe della versione è necessario impostare il livello di isolamento dello snapshot in maniera esplicita per ciascuna sessione.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Gestione della concorrenza con livelli di isolamento  
 Il livello di isolamento al quale viene eseguita un'istruzione di Transact-SQL determina il comportamento di blocco e di controllo della versione della riga. Un livello di isolamento dispone di un ambito di connessione, che, una volta impostato per una connessione con l'istruzione SET TRANSACTION ISOLATION LEVEL, rimane attivo finché non viene chiusa la connessione o non viene impostato un livello di isolamento diverso. Quando una connessione viene chiusa e restituita al pool, il livello di isolamento dall'ultima istruzione SET TRANSACTION ISOLATION LEVEL viene mantenuto. Le successive connessioni che riutilizzano una connessione in pool usano il livello di isolamento che era attivo nel momento in cui la connessione è stata inserita nel pool.  
  
 Le singole query eseguite in una connessione possono contenere hint di blocco in grado di modificare l'isolamento per una singola istruzione o transazione, ma che non possono influire sul livello della connessione. I livelli di isolamento o gli hint di blocco impostati in funzioni o stored procedure non modificano il livello di isolamento della connessione che li ha chiamati e restano validi solo per la durata della stored procedure o della chiamata di funzione.  
  
 I quattro livelli di isolamento definiti nello standard SQL-92 sono supportati nelle prime versioni di SQL Server:  
  
- READ UNCOMMITTED rappresenta il livello di isolamento meno restrittivo perché ignora i blocchi inseriti da altre transazioni. Le transazioni eseguite in READ UNCOMMITTED possono leggere i valori dei dati modificati non ancora sottoposti a commit da altre transazioni. Queste letture vengono definite "dirty".  
  
- READ COMMITTED è il livello di isolamento predefinito per SQL Server. Questo livello consente di impedire le letture dirty, specificando che le istruzioni non possono leggere i valori dei dati modificati ma non ancora sottoposti a commit da altre transazioni. Altre transazioni possono ancora modificare, inserire o eliminare dati tra le esecuzioni di singole istruzioni all'interno della transazione corrente, dando luogo a letture non ripetibili o dati "fantasma".  
  
- REPEATABLE READ è un livello di isolamento più restrittivo di READ COMMITTED. Esso include il livello READ COMMITTED e aggiunge la limitazione in base alla quale nessun'altra transazione può modificare o eliminare dati letti dalla transazione corrente finché questa non viene sottoposta a commit. La concorrenza è minore rispetto al livello READ COMMITTED in quanto i blocchi condivisi sui dati letti vengono conservati per la durata della transazione anziché rilasciati al termine di ciascuna istruzione.  
  
- SERIALIZABLE è il livello di isolamento più restrittivo, in quanto blocca intere gamme di chiavi e trattiene i blocchi finché la transazione non è stata completata. Esso include il livello REPEATABLE READ e aggiunge la limitazione in base alla quale altre transazioni non possono inserire nuove righe negli intervalli letti dalla transazione finché quest'ultima non è stata completata.  
  
 Per ulteriori informazioni, vedere la [Guida al blocco delle transazioni e al controllo delle versioni delle righe](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Estensione del livello di isolamento dello snapshot  
 In SQL Server sono state introdotte estensioni ai livelli di isolamento SQL-92 sotto forma del livello di isolamento SNAPSHOT e un'implementazione aggiuntiva di READ COMMITTED. Il livello di isolamento READ_COMMITTED_SNAPSHOT può sostituire READ COMMITTED per tutte le transazioni.  
  
- L'isolamento SNAPSHOT specifica che i dati letti all'interno di una transazione non rifletteranno mai le modifiche apportate da altre transazioni simultanee. La transazione usa le versioni delle righe dei dati esistenti al momento in cui tale transazione viene iniziata. Sui dati non viene posizionato alcun blocco al momento della lettura, quindi le transazioni SNAPSHOT non impediscono la scrittura di dati da parte di altre transazioni. Le transazioni di scrittura dei dati non bloccano la lettura dei dati da parte delle transazioni snapshot. È necessario abilitare l'isolamento dello snapshot impostando l'opzione di database ALLOW_SNAPSHOT_ISOLATION.  
  
- L'opzione di database READ_COMMITTED_SNAPSHOT determina il comportamento del livello di isolamento READ COMMITTED predefinito quando nel database viene abilitato l'isolamento dello snapshot. Se non si specifica in maniera esplicita l'opzione READ_COMMITTED_SNAPSHOT ON, il livello READ COMMITTED viene applicato a tutte le transazioni implicite. Ciò provoca lo stesso comportamento dell'impostazione READ_COMMITTED_SNAPSHOT OFF (predefinita). Quando è attiva l'impostazione READ_COMMITTED_SNAPSHOT OFF, il motore di database usa i blocchi condivisi per l'applicazione del livello di isolamento. Se si imposta l'opzione di database READ_COMMITTED_SNAPSHOT su ON, per impostazione predefinita il motore di database usa il controllo delle versioni delle righe e l'isolamento dello snapshot, anziché usare i blocchi per proteggere i dati.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Funzionamento dell'isolamento dello snapshot e del controllo delle versioni delle righe  
 Quando il livello di isolamento dello SNAPSHOT è abilitato, ogni volta che viene aggiornata una riga, il SQL Server motore di database archivia una copia della riga originale in **tempdb**e aggiunge un numero di sequenza della transazione alla riga. Di seguito è riportata la sequenza degli eventi che si verificano:  
  
- Viene avviata una nuova transazione alla quale viene assegnato un numero di sequenza.  
  
- Il motore di database legge una riga all'interno della transazione e recupera la versione di riga da **tempdb** il cui numero di sequenza è più vicino a e minore di, il numero di sequenza della transazione.  
  
- Il motore di database controlla se il numero di sequenza della transazione è presente nell'elenco dei numeri di sequenza delle transazioni attive non sottoposte a commit al momento dell'avvio della transazione snapshot.  
  
- La transazione legge la versione della riga da **tempdb** aggiornata al momento dell'avvio della transazione. Non rileverà nuove righe inserite dopo che la transazione è stata avviata in quanto questi valori del numero di sequenza sono maggiori del valore del numero di sequenza della transazione.  
  
- La transazione corrente vedrà le righe che sono state eliminate dopo l'inizio della transazione, perché in **tempdb** sarà presente una versione di riga con un valore numerico di sequenza inferiore.  
  
 L'effetto dell'isolamento consiste nel fatto che la transazione rileva tutti i dati esattamente come erano al momento dell'avvio della transazione stessa, senza rispettare o posizionare blocchi sulle tabelle sottostanti. Ciò può comportare un miglioramento delle prestazioni in situazioni di conflitto.  
  
 Una transazione snapshot usa sempre il controllo della concorrenza ottimistica, rifiutando blocchi che potrebbero impedire l'aggiornamento delle righe da parte di altre transazioni. Se una transazione snapshot tenta di eseguire il commit di un aggiornamento per una riga modificata dopo l'inizio della transazione, viene eseguito il rollback della transazione e viene generato un errore.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Utilizzo dell'isolamento dello snapshot in ADO.NET  
 L'isolamento dello snapshot è supportato in ADO.NET dalla classe <xref:System.Data.SqlClient.SqlTransaction>. Se un database è stato abilitato per l'isolamento dello snapshot ma non è configurato per READ_COMMITTED_SNAPSHOT in, è necessario avviare <xref:System.Data.SqlClient.SqlTransaction> un usando il valore di enumerazione **IsolationLevel. snapshot** quando <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> si chiama il metodo. Questo frammento di codice presuppone che la connessione sia un oggetto <xref:System.Data.SqlClient.SqlConnection> aperto.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il comportamento dei diversi livelli di isolamento mediante il tentativo di accesso ai dati bloccati. Questo esempio non può essere usato nel codice di produzione.  
  
 Il codice si connette al database di esempio **AdventureWorks** in SQL Server e crea una tabella denominata **TestSnapshot** e inserisce una riga di dati. Il codice usa l'istruzione ALTER DATABASE di Transact-SQL per attivare l'isolamento dello snapshot per il database, ma non imposta l'opzione READ_COMMITTED_SNAPSHOT, lasciando attivo il comportamento a livello di isolamento READ COMMITTED predefinito. Nel codice vengono eseguite le seguenti azioni:  
  
- Inizia, ma non completa, sqlTransaction1, che usa il livello di isolamento SERIALIZABLE per avviare la transazione di aggiornamento. Ciò consente di bloccare la tabella.  
  
- Viene aperta una seconda connessione e viene avviata una seconda transazione utilizzando il livello di isolamento dello SNAPSHOT per leggere i dati nella tabella **TestSnapshot** . Poiché l'isolamento dello snapshot è abilitato, la transazione può leggere i dati esistenti prima che venga avviata sqlTransaction1.  
  
- Apre una terza connessione e avvia una transazione usando il livello di isolamento READ COMMITTED per tentare di leggere i dati nella tabella. In tal caso, il codice non può leggere i dati perché non è in grado di leggere informazioni successive al posizionamento dei blocchi sulla tabella nella prima transazione, pertanto verrà eseguito il timeout. Lo stesso risultato si ottiene con i livelli di isolamento REPEATABLE READ e SERIALIZABLE poiché questi non possono leggere le informazioni successive al posizionamento dei blocchi nella prima transazione.  
  
- Apre una quarta connessione e avvia una transazione usando il livello di isolamento READ UNCOMMITTED, che esegue una lettura dirty del valore del quale non è stato eseguito il commit in sqlTransaction1. Se non è stato eseguito il commit della prima transazione, questo valore non può esistere nel database.  
  
- Esegue il rollback della prima transazione e si pulisce eliminando la tabella **TestSnapshot** e disattivando l'isolamento dello snapshot per il database **AdventureWorks** .  
  
> [!NOTE]
> Negli esempi seguenti viene usata la stessa stringa di connessione con il pool di connessioni disattivato. Se una connessione è in pool, la reimpostazione del relativo livello di isolamento non implica quella del livello di isolamento nel server. Di conseguenza, le connessioni successive che usano la stessa connessione interna in pool vengono avviate con i livelli di isolamento impostati su quello della connessione in pool. In alternativa a disattivare il pool di connessioni, è possibile impostare il livello di isolamento in modo esplicito per ogni connessione.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il comportamento dell'isolamento dello snapshot durante la modifica dei dati. Nel codice vengono eseguite le seguenti azioni:  
  
- Si connette al database di esempio **AdventureWorks** e Abilita l'isolamento dello snapshot.  
  
- Crea una tabella denominata **TestSnapshotUpdate** e inserisce tre righe di dati di esempio.  
  
- Inizia, ma non completa, sqlTransaction1 usando l'isolamento SNAPSHOT. Nella transazione vengono selezionate tre righe di dati.  
  
- Crea una seconda SqlConnection in **AdventureWorks** e crea una seconda transazione usando il livello di isolamento Read committed che aggiorna un valore in una delle righe selezionate in sqlTransaction1.  
  
- Esegue il commit di sqlTransaction2.  
  
- Torna a sqlTransaction1 e tenta di aggiornare la stessa riga di cui è già stato eseguito il commit da sqlTransaction1. Viene generato l'errore 3960 e viene eseguito il rollback automatico di sqlTransaction1. **SqlException. Number** e **SqlException. Message** vengono visualizzati nella finestra della console.  
  
- Esegue il codice di pulizia per disattivare l'isolamento dello snapshot in **AdventureWorks** ed eliminare la tabella **TestSnapshotUpdate** .  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Utilizzo degli hint di blocco con l'isolamento dello snapshot  
 Nell'esempio precedente la prima transazione seleziona i dati mentre una seconda transazione li aggiorna prima del completamento della prima transazione, causando un conflitto di aggiornamento nel momento in cui la prima transazione tenta di aggiornare la stessa riga. È possibile limitare le probabilità che si verifichi un conflitto di aggiornamento nelle transazioni snapshot a esecuzione prolungata fornendo hint di blocco all'inizio della transazione. Nell'istruzione SELECT seguente viene usato l'hint UPDLOCK per bloccare le righe selezionate:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 L'utilizzo dell'hint di blocco UPDLOCK consente di bloccare eventuali tentativi di aggiornamento delle righe prima del completamento della prima transazione. Ciò garantisce che non si verifichino conflitti quando le righe vengono aggiornate in seguito nella transazione. Vedere l'argomento relativo agli hint di blocco nella documentazione online di SQL Server.  
  
 Se si verificano molti conflitti, l'isolamento dello snapshot potrebbe non rivelarsi la scelta migliore. Gli hint devono essere usati solo se veramente necessari. L'applicazione non è stata progettata per essere basata sugli hint di blocco dell'operazione.  
  
## <a name="see-also"></a>Vedere anche

- [SQL Server e ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](https://go.microsoft.com/fwlink/?LinkId=217917)
- [Guida al controllo delle versioni delle righe e dei blocchi delle transazioni](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
