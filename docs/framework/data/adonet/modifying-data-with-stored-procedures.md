---
title: Modifica di dati con stored procedure
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: ebf5c61010a6f658d846ed435ea3a7d18d0d3832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934444"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="f17b9-102">Modifica di dati con stored procedure</span><span class="sxs-lookup"><span data-stu-id="f17b9-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="f17b9-103">Le stored procedure possono accettare dati come parametri di input e possono restituire dati come parametri di output, set di risultati o valori restituiti.</span><span class="sxs-lookup"><span data-stu-id="f17b9-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="f17b9-104">Nell'esempio seguente vengono illustrati l'invio e la ricezione di parametri di input, parametri di output e valori restituiti in ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f17b9-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="f17b9-105">Viene inserito un nuovo record in una tabella in cui la colonna della chiave primaria è una colonna Identity di un database SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f17b9-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f17b9-106">Se si usano stored procedure SQL Server per modificare o eliminare dati tramite <xref:System.Data.SqlClient.SqlDataAdapter>, assicurarsi di non usare SET NOCOUNT ON nella definizione della stored procedure.</span><span class="sxs-lookup"><span data-stu-id="f17b9-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="f17b9-107">Con tale comando il totale restituito delle righe interessate è pari a zero e tale situazione viene interpretata da `DataAdapter` come un conflitto di concorrenza.</span><span class="sxs-lookup"><span data-stu-id="f17b9-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="f17b9-108">In questo caso verrà generata un'eccezione <xref:System.Data.DBConcurrencyException>.</span><span class="sxs-lookup"><span data-stu-id="f17b9-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f17b9-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="f17b9-109">Example</span></span>  
 <span data-ttu-id="f17b9-110">Nell'esempio viene utilizzata la stored procedure seguente per inserire una nuova categoria nella tabella delle **categorie** **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="f17b9-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="f17b9-111">Il stored procedure accetta il valore nella colonna **CategoryName** come parametro di input e utilizza la funzione SCOPE_IDENTITY () per recuperare il nuovo valore del campo Identity, **CategoryID**, e restituirlo in un parametro di output.</span><span class="sxs-lookup"><span data-stu-id="f17b9-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="f17b9-112">L'istruzione return utilizza la funzione@ROWCOUNT @ per restituire il numero di righe inserite.</span><span class="sxs-lookup"><span data-stu-id="f17b9-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="f17b9-113">Nell'esempio di codice seguente viene usata la stored procedure `InsertCategory` sopra indicata come origine per <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> di <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="f17b9-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="f17b9-114">Il parametro di output `@Identity` e il valore restituito verranno riflessi in <xref:System.Data.DataSet> dopo l'inserimento del record nel database quando viene chiamato il metodo `Update` di <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="f17b9-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="f17b9-115">Nel codice viene inoltre recuperato il valore restituito:</span><span class="sxs-lookup"><span data-stu-id="f17b9-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f17b9-116">Quando si usa <xref:System.Data.OleDb.OleDbDataAdapter>, è necessario specificare i parametri <xref:System.Data.ParameterDirection> con di **returnValue** prima degli altri parametri.</span><span class="sxs-lookup"><span data-stu-id="f17b9-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f17b9-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f17b9-117">See also</span></span>

- [<span data-ttu-id="f17b9-118">Recupero e modifica di dati in ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f17b9-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="f17b9-119">DataAdapter e DataReader</span><span class="sxs-lookup"><span data-stu-id="f17b9-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="f17b9-120">Esecuzione di un comando</span><span class="sxs-lookup"><span data-stu-id="f17b9-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="f17b9-121">Provider gestiti ADO.NET e Centro per sviluppatori di set di dati</span><span class="sxs-lookup"><span data-stu-id="f17b9-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
