---
title: Integrazione di System.Transactions con SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 075eea42c65a822fc46ca14f820599567c35d231
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791361"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integrazione di System.Transactions con SQL Server
Nel .NET Framework versione 2,0 è stato introdotto un Framework di transazione a cui è <xref:System.Transactions> possibile accedere tramite lo spazio dei nomi. Questo framework espone le transazioni in modo completamente integrato nel .NET Framework, incluso ADO.NET.  
  
 Oltre ai miglioramenti apportati alla programmabilità <xref:System.Transactions> , e ADO.NET possono interagire per coordinare le ottimizzazioni quando si utilizzano le transazioni. Una transazione promuovibile è una transazione di tipo semplice (locale) che può essere promossa in modo automatico a una transazione completamente distribuita in base alle esigenze.  
  
 A partire da ADO.NET 2,0 <xref:System.Data.SqlClient> , supporta le transazioni promuovibili quando si lavora con SQL Server. Una transazione promuovibile non richiama l'overhead aggiunto di una transazione distribuita, a meno che non sia necessario. Le transazioni promuovibili sono automatiche e non richiedono alcun intervento da parte dello sviluppatore.  
  
 Le transazioni promuovibili sono disponibili solo quando si usa il .NET Framework provider di dati per`SqlClient`SQL Server () con SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Creazione di transazioni promuovibili  
 Il provider .NET Framework per SQL Server fornisce il supporto per le transazioni promuovibili, che vengono gestite tramite le classi <xref:System.Transactions> nello spazio dei nomi .NET Framework. Le transazioni promuovibili consentono di ottimizzare le transazioni distribuite rinviandone la creazione finché non è richiesta. Se è necessario un solo gestore di risorse, non si verificherà alcuna transazione distribuita.  
  
> [!NOTE]
> In un scenario ad attendibilità parziale è richiesto <xref:System.Transactions.DistributedTransactionPermission> quando una transazione viene promossa a transazione distribuita.  
  
## <a name="promotable-transaction-scenarios"></a>Scenari di transazioni promuovibili  
 In genere, le transazioni distribuite richiedono un notevole utilizzo delle risorse, in quanto sono gestite da Microsoft Distributed Transaction Coordinator (MS DTC) che integra tutti i gestori delle risorse a cui si accede nella transazione. Una transazione promuovibile è una forma speciale di <xref:System.Transactions> transazione che delega efficacemente il lavoro a una semplice transazione di SQL Server. <xref:System.Transactions>, <xref:System.Data.SqlClient>e SQL Server coordinano il lavoro necessario per gestire la transazione, promuovendo tale operazione a una transazione distribuita completa in base alle esigenze.  
  
 Il vantaggio derivante dall'utilizzo delle transazioni promuovibili consiste nel fatto che quando si apre una connessione tramite un transazione <xref:System.Transactions.TransactionScope> attiva e non sono presenti altre transazioni aperte, viene eseguito il commit della transazione come tipo semplice, anziché provocare l'overhead aggiuntivo di una piena transazione distribuita.  
  
### <a name="connection-string-keywords"></a>Parole chiave della stringa di connessione  
 La proprietà <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> supporta la parola chiave `Enlist`, che indica se <xref:System.Data.SqlClient> rileverà i contesti transazionali ed elenca automaticamente la connessione in una transazione distribuita. Se `Enlist=true`, la connessione verrà automaticamente elencata nel contesto di transazione corrente del thread di apertura. Se `Enlist=false`, la connessione `SqlClient` non interagirà con una transazione distribuita. Il valore predefinito per `Enlist` è true. Se `Enlist` non è specificato nella stringa di connessione e se viene rilevata una transazione distribuita all'apertura della connessione, quest'ultima verrà automaticamente elencata nella transazione distribuita.  
  
 Le parole chiave `Transaction Binding` di una stringa di connessione <xref:System.Data.SqlClient.SqlConnection> controllano l'associazione della connessione a una transazione `System.Transactions` elencata. È anche disponibile tramite le proprietà <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> e <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Nella tabella seguente sono descritti i valori possibili.  
  
|Parola chiave|DESCRIZIONE|  
|-------------|-----------------|  
|Implicit Unbind|Valore predefinito. La connessione viene scollegata dalla transazione una volta completata e torna alla modalità di commit automatico.|  
|Explicit Unbind|La connessione rimane collegata alla transazione fino alla chiusura di quest'ultima. La connessione non verrà eseguita se la transazione associata non è attiva o non corrisponde a <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Uso di TransactionScope  
 La classe <xref:System.Transactions.TransactionScope> rende un blocco di codice transazionale elencando implicitamente le connessioni in una transazione distribuita. È necessario chiamare il metodo <xref:System.Transactions.TransactionScope.Complete%2A> alla fine del blocco <xref:System.Transactions.TransactionScope> prima di lasciarlo. Quando si lascia il blocco viene richiamato il metodo <xref:System.Transactions.TransactionScope.Dispose%2A> . Se è stata generata un'eccezione che ha provocato l'uscita del codice dall'ambito, la transazione sarà considerata interrotta.  
  
 Si consiglia di usare un blocco `using` per assicurare che venga chiamato il metodo <xref:System.Transactions.TransactionScope.Dispose%2A> sull'oggetto <xref:System.Transactions.TransactionScope> quando si esce dal blocco using. Se non viene eseguito il commit o il rollback delle transazioni in sospeso, è possibile che le prestazioni vengano notevolmente compromesse, in quanto il timeout predefinito per <xref:System.Transactions.TransactionScope> è di un minuto. Se non si usa un'istruzione `using` , è necessario eseguire le operazioni in un blocco `Try` e chiamare in modo esplicito il metodo <xref:System.Transactions.TransactionScope.Dispose%2A> nel blocco `Finally` .  
  
 Se viene generata un'eccezione all'interno di <xref:System.Transactions.TransactionScope>, la transazione viene contrassegnata come incoerente e viene interrotta. Il rollback verrà eseguito quando viene eliminato il tipo <xref:System.Transactions.TransactionScope> . Se non viene generata alcuna eccezione, verrà eseguito il commit delle transazioni presenti.  
  
> [!NOTE]
> Per impostazione predefinita, la classe `TransactionScope` crea una transazione in cui il valore di <xref:System.Transactions.Transaction.IsolationLevel%2A> è `Serializable` . A seconda dell'applicazione in uso, potrebbe essere necessario ridurre il livello di isolamento per evitare un'elevata possibilità di conflitto nell'applicazione.  
  
> [!NOTE]
> Si consiglia di eseguire solo operazioni di aggiornamento, inserimento ed eliminazione all'interno delle transazioni distribuite, poiché comportano un utilizzo notevole delle risorse di database. Le istruzioni SELECT possono bloccare le risorse di database inutilmente e, in alcuni scenari, può essere necessario usare le transazioni per questo tipo di istruzioni. È necessario eseguire le operazioni non di database al di fuori dell'ambito della transazione, a meno che non richiedano altri gestori di risorse transazionali. Sebbene un'eccezione nell'ambito della transazione impedisca l'esecuzione del commit, la classe <xref:System.Transactions.TransactionScope> non è in grado di eseguire il rollback delle modifiche apportate al codice al di fuori dell'ambito della transazione stessa. Per eseguire operazioni durante il rollback della transazione, è necessario scrivere la propria implementazione dell'interfaccia <xref:System.Transactions.IEnlistmentNotification> ed elencarla in modo esplicito nella transazione.  
  
## <a name="example"></a>Esempio  
 Per usare <xref:System.Transactions> , è necessario un riferimento a System.Transactions.dll.  
  
 Nella funzione seguente viene illustrato come creare una transazione promuovibile in due istanze diverse di SQL Server, rappresentate da due oggetti <xref:System.Data.SqlClient.SqlConnection> diversi, incapsulati in un blocco <xref:System.Transactions.TransactionScope> . Il codice consente di creare il blocco <xref:System.Transactions.TransactionScope> con un'istruzione `using` , di aprire la prima connessione e di elencarla automaticamente nel tipo <xref:System.Transactions.TransactionScope>. Inizialmente la transazione viene elencata come transazione semplice e non come piena transazione distribuita. La seconda connessione viene inserita in <xref:System.Transactions.TransactionScope> solo se il comando della prima connessione non genera un'eccezione. Quando viene aperta la seconda connessione, la transazione viene automaticamente promossa diventando una piena transazione distribuita. Viene richiamato il metodo <xref:System.Transactions.TransactionScope.Complete%2A> che esegue il commit della transazione solo se non sono state generate eccezioni. Se è stata generata un'eccezione in qualsiasi punto del blocco <xref:System.Transactions.TransactionScope> , il metodo `Complete` non verrà chiamato e verrà eseguito il rollback della transazione distribuita quando <xref:System.Transactions.TransactionScope> viene eliminato al termine del relativo blocco `using` .  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>Vedere anche

- [Transazioni e concorrenza](transactions-and-concurrency.md)
- [Panoramica di ADO.NET](ado-net-overview.md)
