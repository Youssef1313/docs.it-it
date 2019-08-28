---
title: Singole operazioni di copia di massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 07c705b9daeeb043ef36f1e3272a3bf259a3c23e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043886"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="9619a-102">Singole operazioni di copia di massa</span><span class="sxs-lookup"><span data-stu-id="9619a-102">Single Bulk Copy Operations</span></span>

<span data-ttu-id="9619a-103">L'approccio più semplice per eseguire un'operazione di copia di massa in SQL Server consiste nell'eseguire una singola operazione in un database.</span><span class="sxs-lookup"><span data-stu-id="9619a-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="9619a-104">Per impostazione predefinita, un'operazione di copia di massa viene eseguita come operazione isolata: l'operazione di copia avviene in modalità non transazionale, senza la possibilità di eseguirne il rollback.</span><span class="sxs-lookup"><span data-stu-id="9619a-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="9619a-105">Per eseguire il rollback di una parte o dell'intera copia di massa quando si verifica un errore, è possibile usare una transazione gestita di <xref:System.Data.SqlClient.SqlBulkCopy> oppure eseguire la copia di massa in una transazione esistente.</span><span class="sxs-lookup"><span data-stu-id="9619a-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="9619a-106">**SqlBulkCopy** funzionerà anche con <xref:System.Transactions> se la connessione viene integrata (in modo implicito o esplicito) in una transazione **System.** Transactions.</span><span class="sxs-lookup"><span data-stu-id="9619a-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="9619a-107">Per ulteriori informazioni, vedere [transazioni e operazioni di copia bulk](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9619a-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="9619a-108">In generale, i passaggi per eseguire un'operazione di copia di massa sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="9619a-108">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="9619a-109">Connettersi al server di origine per recuperare i dati da copiare.</span><span class="sxs-lookup"><span data-stu-id="9619a-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="9619a-110">I dati possono provenire anche da altre origini, se possono essere recuperati da un oggetto<xref:System.Data.IDataReader> o <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9619a-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="9619a-111">Connettersi al server di destinazione, a meno che non si desideri che **SqlBulkCopy** stabilisca una connessione.</span><span class="sxs-lookup"><span data-stu-id="9619a-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="9619a-112">Creare un oggetto <xref:System.Data.SqlClient.SqlBulkCopy>, impostando tutte le proprietà necessarie.</span><span class="sxs-lookup"><span data-stu-id="9619a-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="9619a-113">Impostare la proprietà **DestinationTableName** per indicare la tabella di destinazione per l'operazione di inserimento bulk.</span><span class="sxs-lookup"><span data-stu-id="9619a-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="9619a-114">Chiamare uno dei metodi **WriteToServer** .</span><span class="sxs-lookup"><span data-stu-id="9619a-114">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="9619a-115">Facoltativamente, aggiornare le proprietà e chiamare di nuovo **WriteToServer** in caso di necessità.</span><span class="sxs-lookup"><span data-stu-id="9619a-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="9619a-116">Chiamare <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A> o eseguire il wrapping delle operazioni di copia di massa all'interno di un'istruzione `Using`.</span><span class="sxs-lookup"><span data-stu-id="9619a-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="9619a-117">È consigliabile assicurare che la corrispondenza tra i tipi di dati della colonna di origine e quelli di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9619a-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="9619a-118">Se i tipi di dati non corrispondono, **SqlBulkCopy** tenta di convertire ogni valore di origine nel tipo di dati di destinazione usando le regole utilizzate <xref:System.Data.SqlClient.SqlParameter.Value%2A>da.</span><span class="sxs-lookup"><span data-stu-id="9619a-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="9619a-119">Le conversioni possono influenzare le prestazioni e possono provocare errori imprevisti.</span><span class="sxs-lookup"><span data-stu-id="9619a-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="9619a-120">Ad esempio, non è sempre possibile convertire un tipo di dati `Double` in `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9619a-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="9619a-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="9619a-121">Example</span></span>

<span data-ttu-id="9619a-122">Nell'applicazione console riportata di seguito viene illustrato come caricare i dati usando la classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="9619a-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="9619a-123">In questo esempio viene utilizzato <xref:System.Data.SqlClient.SqlDataReader> un oggetto per copiare i dati dalla tabella **Production. Product** nel database di SQL Server **AdventureWorks** a una tabella simile nello stesso database.</span><span class="sxs-lookup"><span data-stu-id="9619a-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9619a-124">Questo esempio non verrà eseguito a meno che non siano state create le tabelle di lavoro come descritto in configurazione di esempio per la [copia bulk](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="9619a-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="9619a-125">Questo codice viene fornito per illustrare la sintassi per l'utilizzo solo di **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="9619a-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="9619a-126">Se la tabella di origine e quella di destinazione risiedono nella stessa istanza di SQL Server, per copiare i dati è più semplice e rapido usare un'istruzione `INSERT … SELECT` Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="9619a-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="9619a-127">Esecuzione di un'operazione di copia di massa con Transact-SQL e la classe Command</span><span class="sxs-lookup"><span data-stu-id="9619a-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="9619a-128">Nell'esempio seguente viene illustrato come usare il metodo <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> per eseguire l'istruzione BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="9619a-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="9619a-129">Il percorso di file per l'origine dati è relativo al server.</span><span class="sxs-lookup"><span data-stu-id="9619a-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="9619a-130">Per la corretta esecuzione dell'operazione di copia di massa, è necessario che il processo server abbia accesso a tale percorso.</span><span class="sxs-lookup"><span data-stu-id="9619a-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a><span data-ttu-id="9619a-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9619a-131">See also</span></span>

- [<span data-ttu-id="9619a-132">Operazioni di copia di massa in SQL Server</span><span class="sxs-lookup"><span data-stu-id="9619a-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="9619a-133">Provider gestiti ADO.NET e Centro per sviluppatori di set di dati</span><span class="sxs-lookup"><span data-stu-id="9619a-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
