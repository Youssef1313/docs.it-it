---
title: Popolamento di un dataset da un oggetto DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 5e86eb4c37d20be53d271aba9f4913f2eeccd923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928342"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Popolamento di un dataset da un oggetto DataAdapter
ADO.NET <xref:System.Data.DataSet> è una rappresentazione di dati residente in memoria che fornisce un modello di programmazione relazionale coerente indipendente dall'origine dati. Il `DataSet` rappresenta un set completo di dati che include tabelle, vincoli e relazioni tra tabelle. Poiché il `DataSet` è indipendente dall'origine dati, un `DataSet` può includere dati locali dell'applicazione nonché dati di più origini dati. L'interazione con le origini dati esistenti è controllata tramite `DataAdapter`.  
  
 La proprietà `SelectCommand` di `DataAdapter` è un oggetto `Command` che recupera i dati dall'origine dati. Le proprietà `InsertCommand`, `UpdateCommand`e `DeleteCommand` di `DataAdapter` sono oggetti `Command` che gestiscono gli aggiornamenti ai dati nell'origine dati in base alle modifiche apportate nel `DataSet`. Queste proprietà sono descritte in modo più dettagliato nell' [aggiornamento delle origini dati con](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)i DataAdapter.  
  
 Il metodo `Fill` di `DataAdapter` viene usato per popolare un oggetto `DataSet` con i risultati dell'oggetto `SelectCommand` di `DataAdapter`. `Fill` accetta come argomenti un oggetto `DataSet` da popolare e un oggetto `DataTable` o il nome dell'oggetto `DataTable` da popolare con le righe restituite da `SelectCommand`.  
  
> [!NOTE]
> L'utilizzo di `DataAdapter` per recuperare un'intera tabella richiede del tempo, soprattutto se la tabella contiene molte righe. L'accesso al database, l'individuazione e l'elaborazione dei dati e il successivo trasferimento dei dati al client tramite rete sono infatti processi lunghi. Se viene eseguito il pull dell'intera tabella nel client, vengono anche bloccate tutte le righe sul server. Per migliorare le prestazioni, è possibile usare la clausola `WHERE` in modo da ridurre sensibilmente il numero di righe restituite al client. È anche possibile ridurre la quantità di dati restituiti al client elencando in modo esplicito solo le colonne necessarie nell'istruzione `SELECT` . Un'altra soluzione alternativa efficace consiste nel recuperare le righe in batch, ad esempio diverse centinaia alla volta, e recuperare il batch successivo solo quando il client ha terminato con quello corrente.  
  
 Nel metodo `Fill` viene usato in modo implicito l'oggetto `DataReader` per restituire i nomi e i tipi delle colonne usate per creare le tabelle nel `DataSet`, nonché i dati per compilare le righe delle tabelle nel `DataSet`. Le tabelle e le colonne vengono create solo se non esistono già. In caso contrario, nel metodo `Fill` viene usato lo schema del `DataSet` esistente. I tipi di colonna vengono creati come .NET Framework tipi in base alle tabelle nei [mapping dei tipi di dati in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Le chiavi primarie vengono create solo se sistono nell'origine dati e `DataAdapter` **.** `MissingSchemaAction` è impostato su `MissingSchemaAction` **.** `AddWithKey`. Se `Fill` rileva la presenza di una chiave primaria per una tabella, sovrascriverà i dati presenti nel `DataSet` con quelli prelevati dall'origine dati per le righe in cui i valori della colonna della chiave primaria corrispondono a quelli della riga restituita dall'origine dati. Se non vengono rilevate chiavi primarie , i dati vengono aggiunti alle tabelle nell'oggetto `DataSet`. `Fill`USA i mapping che possono esistere quando si popola `DataSet` (vedere mapping di [DataAdapter DataTable e DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Se `SelectCommand` restituisce i risultati di un OUTER JOIN, mediante `DataAdapter` non viene impostato un valore di `PrimaryKey` per l'oggetto `DataTable`risultante. Per assicurarsi che le righe duplicate vengano risolte correttamente, sarà necessario definire `PrimaryKey` in modo autonomo. Per ulteriori informazioni, vedere [definizione delle chiavi primarie](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Nell'esempio di codice seguente viene creata un'istanza di un tipo <xref:System.Data.SqlClient.SqlDataAdapter> che usa un tipo <xref:System.Data.SqlClient.SqlConnection> nel database `Northwind` di Microsoft SQL Server e viene compilato un tipo <xref:System.Data.DataTable> in un `DataSet` con l'elenco dei clienti. L'istruzione SQL e gli argomenti <xref:System.Data.SqlClient.SqlConnection> passati al costruttore <xref:System.Data.SqlClient.SqlDataAdapter> vengono usati per creare la proprietà <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> del tipo <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
## <a name="example"></a>Esempio  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =   
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> Con il codice illustrato in questo esempio, l'oggetto `Connection`non viene aperto e chiuso in modo esplicito. Il metodo `Fill` apre in modo implicito l'oggetto `Connection` usato da `DataAdapter` se rileva che la connessione non è già aperta. Se la connessione è stata aperta da `Fill` , esso provvederà anche a chiuderla una volta terminato `Fill` . Questa procedura consente di semplificare il codice quando si esegue una singola operazione come `Fill` o `Update`. Tuttavia, se si eseguono più operazioni che richiedono una connessione aperta, per migliorare le prestazioni dell'applicazione è possibile chiamare in modo esplicito il metodo `Open` dell'oggetto `Connection`, eseguire le operazioni sull'origine dati, quindi chiamare il metodo `Close` dell'oggetto `Connection`. È necessario cercare di tenere aperte le connessioni con l'origine dati per un intervallo di tempo minimo, in modo da liberare le risorse che devono essere usate da altre applicazioni client.  
  
## <a name="multiple-result-sets"></a>Più set di risultati  
 Se l'oggetto `DataAdapter` rileva più set di risultati, vengono create più tabelle nel `DataSet`. Alle tabelle viene assegnato il nome predefinito incrementale Table*N*, che inizia con "Table" per Table0. Se il nome di una tabella viene passato come argomento al metodo `Fill` , alle tabelle viene assegnato il nome predefinito incrementale TableName*N*, che inizia con "TableName" per TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Compilazione di un DataSet da più oggetti DataAdapter  
 È possibile usare `DataAdapter` qualsiasi numero di oggetti con un `DataSet`oggetto. Ogni oggetto `DataAdapter` può essere usato per compilare uno o più oggetti `DataTable` e risolvere gli aggiornamenti fino all'origine dati pertinente. Gli oggetti`DataRelation` e `Constraint` possono essere aggiunti all'oggetto `DataSet` localmente, consentendo di creare relazioni tra dati provenienti da origini dati diverse. Un `DataSet` , ad esempio, può contenere dati di un database Microsoft SQL Server, un database IBM DB2 esposto tramite OLE DB e un'origine dati che crea flussi XML. Uno o più oggetti `DataAdapter` possono gestire le comunicazioni con ciascuna origine dati.  
  
### <a name="example"></a>Esempio  
 Nell'esempio di codice seguente vengono compilati un elenco di clienti dal database `Northwind` in Microsoft SQL Server e un elenco di ordini dal database `Northwind` archiviato in Microsoft Access 2000. Viene creata una relazione tra le tabelle compilate tramite `DataRelation`e viene quindi visualizzato l'elenco di clienti con i relativi ordini. Per ulteriori informazioni sugli `DataRelation` oggetti, vedere [aggiunta](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) di DataRelation e [spostamento](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)di oggetti DataRelation.  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _   
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a>Tipo decimal di SQL Server  
 Per impostazione predefinita, `DataSet` archivia i dati usando .NET Framework tipi di dati. Per la maggior parte delle applicazioni, questi tipi consentono di rappresentare in modo adeguato le informazioni delle origini dei dati. Tuttavia, questo tipo di rappresentazione può generare un problema quando il tipo di dati nell'origine dati ha valore numeric o decimal di SQL Server. Il tipo `decimal` di dati .NET Framework consente un massimo di 28 cifre significative, mentre `decimal` il tipo di dati SQL Server consente 38 cifre significative. Se, durante un'operazione `SqlDataAdapter` , `Fill` determina che la precisione di un campo `decimal` di SQL Server è maggiore di 28 caratteri, la riga corrente non viene aggiunta all'oggetto `DataTable`. Viene invece generato un evento `FillError` , che consente di determinare se si è verificata una perdita di precisione e quindi di rispondere in modo appropriato. Per ulteriori informazioni sull' `FillError` evento, vedere Gestione di [eventi DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Per ottenere il valore `decimal` di SQL Server, è anche possibile usare un oggetto <xref:System.Data.SqlClient.SqlDataReader> e chiamare il metodo <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> .  
  
 In ADO.NET 2,0 è stato introdotto <xref:System.Data.SqlTypes> un `DataSet`supporto migliorato per nel. Per altre informazioni, vedere [SqlTypes and the DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>Capitoli OLE DB  
 I rowset gerarchici, o capitoli (tipo OLE DB `DBTYPE_HCHAPTER`, tipo ADO `adChapter`), possono essere usati per compilare il contenuto di un `DataSet`. Quando l'oggetto <xref:System.Data.OleDb.OleDbDataAdapter> rileva una colonna con capitoli durante un'operazione `Fill` , viene creato un oggetto `DataTable` per la colonna e la tabella viene compilata con le colonne e le righe del capitolo. Il nome della tabella creata per la colonna con capitoli viene assegnato usando il nome della tabella padre e il nome della colonna con capitoli nel formato "*NomeTabellaPadreNomeColonnaConCapitoli*". Se nel `DataSet` esiste già una tabella con un nome corrispondente al nome della colonna con capitoli, la tabella corrente viene compilata con i dati del capitolo. Se in una tabella esistente non sono presenti colonne che corrispondono alla colonna rilevata nel capitolo, viene aggiunta una nuova colonna.  
  
 Prima che le tabelle nel `DataSet` siano compilate con i dati delle colonne con capitoli, viene creata una relazione tra le tabelle padre e figlio del rowset gerarchico aggiungendo una colonna di valori integer sia alla tabella padre che alla tabella figlio, impostando l'incremento automatico della colonna padre e creando un `DataRelation` con le colonne aggiunte dalle due tabelle. Il nome della relazione aggiunta viene assegnato usando i nomi della tabella padre e della colonna con capitoli nel formato "*NomeTabellaPadreNomeColonnaConCapitoli*".  
  
 Si noti che la colonna correlata esiste solo nel `DataSet`. Nelle successive operazioni di inserimento dati dall'origine dati, anziché aggiornare le righe esistenti nelle tabelle in base alle modifiche, verranno aggiunte nuove righe.  
  
 Si noti inoltre che se si usa l'overload `DataAdapter.Fill` che accetta un `DataTable`, verrà compilata solo quella tabella. Una colonna di valori integer con incremento automatico verrà comunque aggiunta alla tabella, ma non verrà creata o compilata alcuna tabella figlio e non verrà creata alcuna relazione.  
  
 Nell'esempio seguente viene usato il provider MSDataShape per generare una colonna di ordini con capitoli per ogni cliente presente in un elenco di clienti. Quindi, verrà compilato un `DataSet` con i dati.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 Al termine dell'operazione `Fill` , il `DataSet` contiene due tabelle: `Customers` e `CustomersOrders`, dove `CustomersOrders` rappresenta la colonna con capitoli. Alla tabella `Orders` viene aggiunta un'altra colonna denominata `Customers` e alla tabella `CustomersOrders` viene aggiunta un'altra colonna denominata `CustomersOrders` . Nella colonna `Orders` della tabella `Customers` viene impostato l'incremento automatico. Viene creato un oggetto `DataRelation`, `CustomersOrders`, usando le colonne aggiunte alle tabelle con `Customers` come tabella padre. Nelle tabelle seguenti sono illustrati alcuni risultati di esempio.  
  
### <a name="tablename-customers"></a>TableName: Clienti  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Vedere anche

- [DataAdapter e DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Mapping dei tipi di dati in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Modifica di dati con un oggetto DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [MARS (Multiple Active Result Set)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](https://go.microsoft.com/fwlink/?LinkId=217917)
