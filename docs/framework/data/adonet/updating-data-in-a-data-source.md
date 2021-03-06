---
title: Aggiornamento di dati in un'origine dati
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780621"
---
# <a name="updating-data-in-a-data-source"></a>Aggiornamento di dati in un'origine dati
Le istruzioni SQL che modificano i dati, ad esempio INSERT, UPDATE o DELETE, non restituiscono righe. Analogamente, molte stored procedure eseguono un'operazione ma non restituiscono righe. Per eseguire comandi che non restituiscono righe, creare un oggetto **Command** con il comando SQL appropriato e una **connessione**, inclusi eventuali **parametri**obbligatori. Eseguire il comando con il metodo **ExecuteNonQuery** dell'oggetto **Command** .  
  
 Il metodo **ExecuteNonQuery** restituisce un valore integer che rappresenta il numero di righe interessate dall'istruzione o dalla stored procedure eseguita. Se si eseguono più istruzioni, il valore restituito sarà la somma dei record interessati da ognuna delle istruzioni eseguite.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene eseguita un'istruzione INSERT per inserire un record in un database utilizzando **ExecuteNonQuery**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 Nell'esempio di codice seguente viene eseguito il stored procedure creato dal codice di esempio in [esecuzione di operazioni di catalogo](performing-catalog-operations.md). Non viene restituita alcuna riga dal stored procedure, quindi viene utilizzato il metodo **ExecuteNonQuery** , ma il stored procedure riceve un parametro di input e restituisce un parametro di output e un valore restituito.  
  
 Per l' <xref:System.Data.OleDb.OleDbCommand> oggetto, è innanzitutto necessario aggiungere il parametro **returnValue** alla raccolta **Parameters** .  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>Vedere anche

- [Uso di comandi per modificare i dati](using-commands-to-modify-data.md)
- [Aggiornamento di origini dati con DataAdapter](updating-data-sources-with-dataadapters.md)
- [Comandi e parametri](commands-and-parameters.md)
- [Panoramica di ADO.NET](ado-net-overview.md)
