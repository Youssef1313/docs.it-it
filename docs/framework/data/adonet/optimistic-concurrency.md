---
title: Concorrenza ottimistica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: a8cca707f8fa82e97e988fcbe015b55e35b93499
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794684"
---
# <a name="optimistic-concurrency"></a>Concorrenza ottimistica
In un ambiente con più utenti sono disponibili due modelli per l'aggiornamento di dati in un database: la concorrenza ottimistica e la concorrenza pessimistica. L'oggetto <xref:System.Data.DataSet> è stato progettato per favorire l'uso della concorrenza ottimistica per attività di lunga durata, quali la gestione in remoto dei dati e l'interazione con i dati.  
  
 La concorrenza pessimistica implica il blocco di righe nell'origine dati per impedire agli altri utenti di apportare modifiche ai dati che possano influire sugli utenti correnti. In un modello pessimistico, quando un utente esegue un'azione che provoca l'applicazione di un blocco, agli altri utenti non sarà consentito eseguire azioni che possano entrare in conflitto con tale blocco, fino a quando tale blocco non verrà rilasciato dal relativo proprietario. Questo tipo di modello viene usato principalmente in ambienti in cui il conflitto per l'uso di dati è elevato e il dispendio di memoria dovuto alla protezione di dati tramite blocchi è inferiore al dispendio relativo all'annullamento di transazioni in caso di conflitti di concorrenza.  
  
 Pertanto, in un modello di concorrenza pessimistica, un blocco viene stabilito da un utente che aggiorna una riga. Fino a che tale utente non completa l'aggiornamento e non rilascia il blocco, nessun altro utente sarà in grado di modificare tale riga. La concorrenza pessimistica è quindi consigliabile in caso di durate limitate dei blocchi, ad esempio nell'elaborazione a livello di programmazione dei record, ma non è un'opzione scalabile nel caso in cui gli utenti interagiscano con i dati e provochino il blocco dei record per periodi di tempo relativamente lunghi.  
  
> [!NOTE]
> Se è necessario aggiornare più righe nella stessa operazione, la creazione di una transazione garantisce una maggior scalabilità rispetto al blocco associato alla concorrenza pessimistica.  
  
 Al contrario, gli utenti che usano la concorrenza ottimistica sono in grado di leggere una riga senza bloccarla. Quando un utente desidera aggiornare una riga, è necessario che l'applicazione stabilisca se tale riga è stata modificata da un altro utente successivamente alla lettura. La concorrenza ottimistica viene solitamente usata in ambienti in cui il conflitto per l'uso dei dati non è elevato. Questo tipo di concorrenza consente un miglioramento delle prestazioni, poiché non è richiesto alcun blocco dei record, operazione che richiede risorse di server aggiuntive. Per mantenere i blocchi dei record, inoltre, è necessaria una connessione permanente al server database. Poiché tali blocchi non sono necessari se si usa un modello di concorrenza ottimistica, le connessioni al server sono in grado di soddisfare un numero superiore di client in un intervallo di tempo minore.  
  
 In un modello di concorrenza ottimistica si verifica una violazione nel caso in cui, dopo che un utente riceve un valore dal database, tale valore viene modificato da un altro utente prima che il primo utente abbia effettuato un tentativo di modifica. L'esempio seguente consente di illustrare in modo migliore come viene risolta una violazione di concorrenza da parte del server.  
  
 Nella tabella seguente viene mostrato un esempio di concorrenza ottimistica.  
  
 Alle ore 13.00 l'Utente1 legge una riga dal database contenente i seguenti valori:  
  
 **Nome cognome CustID**  
  
 101 Smith Bob  
  
|Nome colonna|Valore originale|Valore corrente|Valore nel database|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Dalzi|Dalzi|Dalzi|  
|FirstName|Maria|Maria|Maria|  
  
 Alle ore 13.01 l'Utente2 legge la stessa colonna.  
  
 Alle 1:03, User2 modifica **FirstName** da "Bob" a "Robert" e aggiorna il database.  
  
|Nome colonna|Valore originale|Valore corrente|Valore nel database|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Dalzi|Dalzi|Dalzi|  
|FirstName|Maria|Maria Teresa|Maria|  
  
 L'aggiornamento viene effettuato correttamente, poiché i valori presenti nel database al momento dell'aggiornamento corrispondono ai valori originali a disposizione dell'Utente2.  
  
 Alle ore 13.05 l'Utente1 cambia il nome di "Maria" in "Teresa" e cerca di aggiornare la riga.  
  
|Nome colonna|Valore originale|Valore corrente|Valore nel database|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Dalzi|Dalzi|Dalzi|  
|FirstName|Maria|Teresa|Maria Teresa|  
  
 A questo punto l'Utente1 rileva una violazione della concorrenza ottimistica, poiché i valori del database ("Maria Teresa") non corrispondono più ai valori originali previsti dall'Utente1 ("Maria"). La violazione della concorrenza consente di essere informati del mancato aggiornamento. È quindi necessario decidere se sovrascrivere le modifiche apportate dall'Utente2 con le modifiche apportate dall'Utente1 o annullare le modifiche dell'Utente1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Verifica di violazioni alla concorrenza ottimistica  
 Per verificare eventuali violazioni alla concorrenza ottimistica, sono disponibili diverse tecniche. Una di queste prevede l'inclusione di una colonna timestamp nella tabella. In genere, la funzionalità timestamp, che consente di identificare la data e l'ora dell'ultimo aggiornamento apportato al record, viene fornita dai database. Se si usa questa tecnica, una colonna timestamp viene inclusa nella definizione della tabella. Il timestamp viene aggiornato a ogni aggiornamento del record, in modo da riflettere la data e l'ora correnti. Quando si esegue una verifica di eventuali violazioni alla concorrenza ottimistica, la colonna timestamp viene restituita con una query relativa ai contenuti della tabella. A ogni tentativo di aggiornamento, il valore timestamp del database viene confrontato con il valore timestamp originale contenuto nella riga modificata. Se tali valori corrispondono, l'aggiornamento viene eseguito e la colonna timestamp viene aggiornata con l'ora corrente, in modo da riflettere l'aggiornamento. Se i valori non corrispondono, si è verificata una violazione della concorrenza ottimistica.  
  
 Un'altra tecnica per rilevare eventuali violazioni alla concorrenza ottimistica consiste nel verificare che tutti i valori di colonna originali corrispondano ancora ai valori presenti nel database. Si consideri ad esempio la seguente query:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Per verificare la presenza di una violazione della concorrenza ottimistica quando si aggiorna una riga in **Tabella1**, è necessario eseguire l'istruzione Update seguente:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Se i valori originali corrispondono ai valori del database, sarà possibile effettuare l'aggiornamento. Se un valore è stato modificato, la riga non verrà modificata dall'aggiornamento, poiché la clausola WHERE non sarà in grado di trovare alcuna corrispondenza.  
  
 Notare che è sempre consigliabile restituire un valore univoco di chiave primaria nella query. In caso contrario, è possibile che la precedente istruzione UPDATE provochi l'aggiornamento non desiderato di più righe.  
  
 Se in una colonna dell'origine dati sono consentiti valori null, è necessario estendere la clausola WHERE, in modo che ricerchi un riferimento null corrispondente nella tabella locale e nell'origine dati. La seguente istruzione UPDATE, ad esempio, consente di verificare la corrispondenza tra un riferimento null nella riga locale e un riferimento null nell'origine dati o la corrispondenza tra un valore nella riga locale e il valore nell'origine dati.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Quando si usa il modello di concorrenza ottimistica, è possibile applicare anche criteri meno restrittivi. Ad esempio, se si usano solo le colonne di chiave primaria nella clausola WHERE, i dati verranno sovrascritti, indipendentemente dagli eventuali aggiornamenti apportati alle altre colonne successivamente all'ultima query. È inoltre possibile applicare una clausola WHERE solo a colonne specifiche, in modo che i dati vengano sovrascritti a meno che particolari campi non siano stati aggiornati successivamente all'ultima query.  
  
### <a name="the-dataadapterrowupdated-event"></a>Evento DataAdapter.RowUpdated  
 L'evento **RowUpdated** dell' <xref:System.Data.Common.DataAdapter> oggetto può essere usato in combinazione con le tecniche descritte in precedenza, per fornire una notifica all'applicazione di violazioni della concorrenza ottimistica. **RowUpdated** si verifica dopo ogni tentativo di aggiornamento di una riga **modificata** da un **set di dati**. È quindi possibile aggiungere un particolare codice di gestione, che includa l'elaborazione nel caso in cui si verifichi un'eccezione, l'aggiunta di informazioni personalizzate relative agli errori, l'aggiunta di logica relativa ai nuovi tentativi e così via. L' <xref:System.Data.Common.RowUpdatedEventArgs> oggetto restituisce una proprietà **RecordsAffected** contenente il numero di righe interessate da un particolare comando di aggiornamento per una riga modificata in una tabella. Impostando il comando Update per la verifica della concorrenza ottimistica, la proprietà **RecordsAffected** restituirà, di conseguenza, un valore pari a 0 quando si verifica una violazione della concorrenza ottimistica, perché non è stato aggiornato alcun record. In questo caso viene generata un'eccezione. L'evento **RowUpdated** consente di gestire questa occorrenza ed evitare l'eccezione impostando un valore **RowUpdatedEventArgs. status** appropriato, ad esempio **UpdateStatus. SkipCurrentRow**. Per ulteriori informazioni sull'evento **RowUpdated** , vedere [gestione di eventi DataAdapter](handling-dataadapter-events.md).  
  
 Facoltativamente, è possibile impostare **DataAdapter. ContinueUpdateOnError** su **true**, prima di chiamare **Update**e rispondere alle informazioni sugli errori archiviate nella proprietà **RowError** di una determinata riga al termine dell' **aggiornamento** . Per ulteriori informazioni, vedere [informazioni sugli errori di riga](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Esempio di concorrenza ottimistica  
 Di seguito è riportato un semplice esempio che imposta **UpdateCommand** di un **DataAdapter** per verificare la concorrenza ottimistica, quindi utilizza l'evento **RowUpdated** per verificare le violazioni della concorrenza ottimistica. Quando viene rilevata una violazione della concorrenza ottimistica, l'applicazione imposta il **RowError** della riga per cui l'aggiornamento è stato emesso per riflettere una violazione della concorrenza ottimistica.  
  
 Si noti che i valori dei parametri passati alla clausola WHERE del comando UPDATE vengono mappati ai valori **originali** delle rispettive colonne.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche

- [Recupero e modifica di dati in ADO.NET](retrieving-and-modifying-data.md)
- [Aggiornamento di origini dati con DataAdapter](updating-data-sources-with-dataadapters.md)
- [Informazioni sugli errori di riga](./dataset-datatable-dataview/row-error-information.md)
- [Transazioni e concorrenza](transactions-and-concurrency.md)
- [Panoramica di ADO.NET](ado-net-overview.md)
