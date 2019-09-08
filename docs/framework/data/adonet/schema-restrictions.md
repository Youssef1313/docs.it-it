---
title: Restrizione dello schema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: d0250e573dc24bfcad97a2f2606cb2e6c8e520da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782765"
---
# <a name="schema-restrictions"></a><span data-ttu-id="3455f-102">Restrizione dello schema</span><span class="sxs-lookup"><span data-stu-id="3455f-102">Schema Restrictions</span></span>
<span data-ttu-id="3455f-103">Il secondo parametro facoltativo del metodo **GetSchema** è costituito dalle restrizioni utilizzate per limitare la quantità di informazioni sullo schema restituite e viene passato al metodo **GetSchema** come una matrice di stringhe.</span><span class="sxs-lookup"><span data-stu-id="3455f-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="3455f-104">La posizione nella matrice determina i valori che è possibile passare ed equivale al numero della restrizione.</span><span class="sxs-lookup"><span data-stu-id="3455f-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="3455f-105">Nella tabella seguente, ad esempio, vengono descritte le restrizioni supportate dalla raccolta di schemi "Tables" usando il provider di dati .NET Framework per SQL Server:</span><span class="sxs-lookup"><span data-stu-id="3455f-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="3455f-106">Restrizioni aggiuntive per le raccolte di schemi di SQL Server vengono indicate alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="3455f-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="3455f-107">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-107">Restriction Name</span></span>|<span data-ttu-id="3455f-108">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-108">Parameter Name</span></span>|<span data-ttu-id="3455f-109">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-109">Restriction Default</span></span>|<span data-ttu-id="3455f-110">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-111">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-112">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-113">1</span><span class="sxs-lookup"><span data-stu-id="3455f-113">1</span></span>|  
|<span data-ttu-id="3455f-114">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-114">Owner</span></span>|@Owner|<span data-ttu-id="3455f-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-116">2</span><span class="sxs-lookup"><span data-stu-id="3455f-116">2</span></span>|  
|<span data-ttu-id="3455f-117">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-117">Table</span></span>|@Name|<span data-ttu-id="3455f-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-118">TABLE_NAME</span></span>|<span data-ttu-id="3455f-119">3</span><span class="sxs-lookup"><span data-stu-id="3455f-119">3</span></span>|  
|<span data-ttu-id="3455f-120">TableType</span><span class="sxs-lookup"><span data-stu-id="3455f-120">TableType</span></span>|@TableType|<span data-ttu-id="3455f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3455f-121">TABLE_TYPE</span></span>|<span data-ttu-id="3455f-122">4</span><span class="sxs-lookup"><span data-stu-id="3455f-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="3455f-123">Impostazione dei valori di restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="3455f-124">Per usare una delle restrizioni della raccolta di schemi "Tables", è sufficiente creare una matrice di stringa con quattro elementi, quindi posizionare un valore nell'elemento che corrisponde al numero della restrizione.</span><span class="sxs-lookup"><span data-stu-id="3455f-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="3455f-125">Ad esempio, per limitare le tabelle restituite dal metodo **GetSchema** solo alle tabelle nello schema "Sales", impostare il secondo elemento della matrice su "Sales" prima di passarlo al metodo **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="3455f-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3455f-126">Le raccolte di restrizioni per `SqlClient` e `OracleClient` includono una colonna `ParameterName` aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="3455f-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="3455f-127">La colonna di restrizione predefinita è ancora disponibile per garantire la compatibilità con le versioni precedenti, ma attualmente è ignorata.</span><span class="sxs-lookup"><span data-stu-id="3455f-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="3455f-128">Per ridurre il rischio di attacchi SQL injection quando si specificano i valori di restrizione, si consiglia di usare query con parametri invece di sostituire le stringhe.</span><span class="sxs-lookup"><span data-stu-id="3455f-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3455f-129">Il numero di elementi nella matrice deve essere inferiore o uguale al numero di restrizioni supportato per la raccolta di schemi specificato, in caso contrario verrà generato un tipo <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="3455f-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="3455f-130">Il numero di restrizioni può essere inferiore al numero massimo consentito.</span><span class="sxs-lookup"><span data-stu-id="3455f-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="3455f-131">Le restrizioni mancanti verranno considerate null (senza restrizioni).</span><span class="sxs-lookup"><span data-stu-id="3455f-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="3455f-132">È possibile eseguire una query su un provider gestito .NET Framework per determinare l'elenco delle restrizioni supportate chiamando il metodo **GetSchema** con il nome della raccolta di schemi delle restrizioni, ovvero "Restrictions".</span><span class="sxs-lookup"><span data-stu-id="3455f-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="3455f-133">In questo modo verrà restituito un oggetto <xref:System.Data.DataTable> con un elenco dei nomi delle raccolte, i nomi delle restrizioni, i valori di restrizione predefiniti e i numeri delle restrizioni.</span><span class="sxs-lookup"><span data-stu-id="3455f-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3455f-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="3455f-134">Example</span></span>  
 <span data-ttu-id="3455f-135">Negli esempi seguenti viene illustrato come utilizzare il <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metodo della .NET Framework provider di dati per la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> per recuperare informazioni sullo schema relative a tutte le tabelle contenute nel database di esempio **AdventureWorks** . e per limitare le informazioni restituite alle sole tabelle nello schema "Sales":</span><span class="sxs-lookup"><span data-stu-id="3455f-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="3455f-136">Restrizioni per gli schemi di SQL Server</span><span class="sxs-lookup"><span data-stu-id="3455f-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="3455f-137">Nelle tabelle seguenti sono incluse le restrizioni per le raccolte di schemi di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3455f-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="3455f-138">Utenti</span><span class="sxs-lookup"><span data-stu-id="3455f-138">Users</span></span>  
  
|<span data-ttu-id="3455f-139">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-139">Restriction Name</span></span>|<span data-ttu-id="3455f-140">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-140">Parameter Name</span></span>|<span data-ttu-id="3455f-141">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-141">Restriction Default</span></span>|<span data-ttu-id="3455f-142">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="3455f-143">User_Name</span></span>|@Name|<span data-ttu-id="3455f-144">name</span><span class="sxs-lookup"><span data-stu-id="3455f-144">name</span></span>|<span data-ttu-id="3455f-145">1</span><span class="sxs-lookup"><span data-stu-id="3455f-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="3455f-146">Database</span><span class="sxs-lookup"><span data-stu-id="3455f-146">Databases</span></span>  
  
|<span data-ttu-id="3455f-147">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-147">Restriction Name</span></span>|<span data-ttu-id="3455f-148">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-148">Parameter Name</span></span>|<span data-ttu-id="3455f-149">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-149">Restriction Default</span></span>|<span data-ttu-id="3455f-150">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-151">NOME</span><span class="sxs-lookup"><span data-stu-id="3455f-151">Name</span></span>|@Name|<span data-ttu-id="3455f-152">Name</span><span class="sxs-lookup"><span data-stu-id="3455f-152">Name</span></span>|<span data-ttu-id="3455f-153">1</span><span class="sxs-lookup"><span data-stu-id="3455f-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="3455f-154">Tabelle</span><span class="sxs-lookup"><span data-stu-id="3455f-154">Tables</span></span>  
  
|<span data-ttu-id="3455f-155">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-155">Restriction Name</span></span>|<span data-ttu-id="3455f-156">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-156">Parameter Name</span></span>|<span data-ttu-id="3455f-157">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-157">Restriction Default</span></span>|<span data-ttu-id="3455f-158">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-159">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-160">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-161">1</span><span class="sxs-lookup"><span data-stu-id="3455f-161">1</span></span>|  
|<span data-ttu-id="3455f-162">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-162">Owner</span></span>|@Owner|<span data-ttu-id="3455f-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-164">2</span><span class="sxs-lookup"><span data-stu-id="3455f-164">2</span></span>|  
|<span data-ttu-id="3455f-165">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-165">Table</span></span>|@Name|<span data-ttu-id="3455f-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-166">TABLE_NAME</span></span>|<span data-ttu-id="3455f-167">3</span><span class="sxs-lookup"><span data-stu-id="3455f-167">3</span></span>|  
|<span data-ttu-id="3455f-168">TableType</span><span class="sxs-lookup"><span data-stu-id="3455f-168">TableType</span></span>|@TableType|<span data-ttu-id="3455f-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3455f-169">TABLE_TYPE</span></span>|<span data-ttu-id="3455f-170">4</span><span class="sxs-lookup"><span data-stu-id="3455f-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3455f-171">Colonne</span><span class="sxs-lookup"><span data-stu-id="3455f-171">Columns</span></span>  
  
|<span data-ttu-id="3455f-172">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-172">Restriction Name</span></span>|<span data-ttu-id="3455f-173">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-173">Parameter Name</span></span>|<span data-ttu-id="3455f-174">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-174">Restriction Default</span></span>|<span data-ttu-id="3455f-175">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-176">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-177">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-178">1</span><span class="sxs-lookup"><span data-stu-id="3455f-178">1</span></span>|  
|<span data-ttu-id="3455f-179">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-179">Owner</span></span>|@Owner|<span data-ttu-id="3455f-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-181">2</span><span class="sxs-lookup"><span data-stu-id="3455f-181">2</span></span>|  
|<span data-ttu-id="3455f-182">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-182">Table</span></span>|@Table|<span data-ttu-id="3455f-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-183">TABLE_NAME</span></span>|<span data-ttu-id="3455f-184">3</span><span class="sxs-lookup"><span data-stu-id="3455f-184">3</span></span>|  
|<span data-ttu-id="3455f-185">Colonna</span><span class="sxs-lookup"><span data-stu-id="3455f-185">Column</span></span>|@Column|<span data-ttu-id="3455f-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-186">COLUMN_NAME</span></span>|<span data-ttu-id="3455f-187">4</span><span class="sxs-lookup"><span data-stu-id="3455f-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="3455f-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="3455f-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="3455f-189">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-189">Restriction Name</span></span>|<span data-ttu-id="3455f-190">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-190">Parameter Name</span></span>|<span data-ttu-id="3455f-191">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-191">Restriction Default</span></span>|<span data-ttu-id="3455f-192">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-193">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-194">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-195">1</span><span class="sxs-lookup"><span data-stu-id="3455f-195">1</span></span>|  
|<span data-ttu-id="3455f-196">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-196">Owner</span></span>|@Owner|<span data-ttu-id="3455f-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-198">2</span><span class="sxs-lookup"><span data-stu-id="3455f-198">2</span></span>|  
|<span data-ttu-id="3455f-199">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-199">Table</span></span>|@Table|<span data-ttu-id="3455f-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-200">TABLE_NAME</span></span>|<span data-ttu-id="3455f-201">3</span><span class="sxs-lookup"><span data-stu-id="3455f-201">3</span></span>|  
|<span data-ttu-id="3455f-202">Colonna</span><span class="sxs-lookup"><span data-stu-id="3455f-202">Column</span></span>|@Column|<span data-ttu-id="3455f-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-203">COLUMN_NAME</span></span>|<span data-ttu-id="3455f-204">4</span><span class="sxs-lookup"><span data-stu-id="3455f-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3455f-205">Visualizzazioni</span><span class="sxs-lookup"><span data-stu-id="3455f-205">Views</span></span>  
  
|<span data-ttu-id="3455f-206">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-206">Restriction Name</span></span>|<span data-ttu-id="3455f-207">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-207">Parameter Name</span></span>|<span data-ttu-id="3455f-208">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-208">Restriction Default</span></span>|<span data-ttu-id="3455f-209">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-210">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-211">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-212">1</span><span class="sxs-lookup"><span data-stu-id="3455f-212">1</span></span>|  
|<span data-ttu-id="3455f-213">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-213">Owner</span></span>|@Owner|<span data-ttu-id="3455f-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-215">2</span><span class="sxs-lookup"><span data-stu-id="3455f-215">2</span></span>|  
|<span data-ttu-id="3455f-216">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-216">Table</span></span>|@Table|<span data-ttu-id="3455f-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-217">TABLE_NAME</span></span>|<span data-ttu-id="3455f-218">3</span><span class="sxs-lookup"><span data-stu-id="3455f-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="3455f-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="3455f-219">ViewColumns</span></span>  
  
|<span data-ttu-id="3455f-220">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-220">Restriction Name</span></span>|<span data-ttu-id="3455f-221">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-221">Parameter Name</span></span>|<span data-ttu-id="3455f-222">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-222">Restriction Default</span></span>|<span data-ttu-id="3455f-223">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-224">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-225">VIEW_CATALOG</span></span>|<span data-ttu-id="3455f-226">1</span><span class="sxs-lookup"><span data-stu-id="3455f-226">1</span></span>|  
|<span data-ttu-id="3455f-227">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-227">Owner</span></span>|@Owner|<span data-ttu-id="3455f-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="3455f-229">2</span><span class="sxs-lookup"><span data-stu-id="3455f-229">2</span></span>|  
|<span data-ttu-id="3455f-230">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-230">Table</span></span>|@Table|<span data-ttu-id="3455f-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-231">VIEW_NAME</span></span>|<span data-ttu-id="3455f-232">3</span><span class="sxs-lookup"><span data-stu-id="3455f-232">3</span></span>|  
|<span data-ttu-id="3455f-233">Colonna</span><span class="sxs-lookup"><span data-stu-id="3455f-233">Column</span></span>|@Column|<span data-ttu-id="3455f-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-234">COLUMN_NAME</span></span>|<span data-ttu-id="3455f-235">4</span><span class="sxs-lookup"><span data-stu-id="3455f-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3455f-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3455f-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3455f-237">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-237">Restriction Name</span></span>|<span data-ttu-id="3455f-238">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-238">Parameter Name</span></span>|<span data-ttu-id="3455f-239">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-239">Restriction Default</span></span>|<span data-ttu-id="3455f-240">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-241">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="3455f-243">1</span><span class="sxs-lookup"><span data-stu-id="3455f-243">1</span></span>|  
|<span data-ttu-id="3455f-244">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-244">Owner</span></span>|@Owner|<span data-ttu-id="3455f-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="3455f-246">2</span><span class="sxs-lookup"><span data-stu-id="3455f-246">2</span></span>|  
|<span data-ttu-id="3455f-247">Name</span><span class="sxs-lookup"><span data-stu-id="3455f-247">Name</span></span>|@Name|<span data-ttu-id="3455f-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="3455f-249">3</span><span class="sxs-lookup"><span data-stu-id="3455f-249">3</span></span>|  
|<span data-ttu-id="3455f-250">Parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-250">Parameter</span></span>|@Parameter|<span data-ttu-id="3455f-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-251">PARAMETER_NAME</span></span>|<span data-ttu-id="3455f-252">4</span><span class="sxs-lookup"><span data-stu-id="3455f-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3455f-253">Procedure</span><span class="sxs-lookup"><span data-stu-id="3455f-253">Procedures</span></span>  
  
|<span data-ttu-id="3455f-254">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-254">Restriction Name</span></span>|<span data-ttu-id="3455f-255">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-255">Parameter Name</span></span>|<span data-ttu-id="3455f-256">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-256">Restriction Default</span></span>|<span data-ttu-id="3455f-257">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-258">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="3455f-260">1</span><span class="sxs-lookup"><span data-stu-id="3455f-260">1</span></span>|  
|<span data-ttu-id="3455f-261">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-261">Owner</span></span>|@Owner|<span data-ttu-id="3455f-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="3455f-263">2</span><span class="sxs-lookup"><span data-stu-id="3455f-263">2</span></span>|  
|<span data-ttu-id="3455f-264">Name</span><span class="sxs-lookup"><span data-stu-id="3455f-264">Name</span></span>|@Name|<span data-ttu-id="3455f-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="3455f-266">3</span><span class="sxs-lookup"><span data-stu-id="3455f-266">3</span></span>|  
|<span data-ttu-id="3455f-267">Type</span><span class="sxs-lookup"><span data-stu-id="3455f-267">Type</span></span>|@Type|<span data-ttu-id="3455f-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3455f-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="3455f-269">4</span><span class="sxs-lookup"><span data-stu-id="3455f-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="3455f-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="3455f-270">IndexColumns</span></span>  
  
|<span data-ttu-id="3455f-271">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-271">Restriction Name</span></span>|<span data-ttu-id="3455f-272">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-272">Parameter Name</span></span>|<span data-ttu-id="3455f-273">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-273">Restriction Default</span></span>|<span data-ttu-id="3455f-274">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-275">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="3455f-276">db_name()</span></span>|<span data-ttu-id="3455f-277">1</span><span class="sxs-lookup"><span data-stu-id="3455f-277">1</span></span>|  
|<span data-ttu-id="3455f-278">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-278">Owner</span></span>|@Owner|<span data-ttu-id="3455f-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="3455f-279">user_name()</span></span>|<span data-ttu-id="3455f-280">2</span><span class="sxs-lookup"><span data-stu-id="3455f-280">2</span></span>|  
|<span data-ttu-id="3455f-281">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-281">Table</span></span>|@Table|<span data-ttu-id="3455f-282">o.name</span><span class="sxs-lookup"><span data-stu-id="3455f-282">o.name</span></span>|<span data-ttu-id="3455f-283">3</span><span class="sxs-lookup"><span data-stu-id="3455f-283">3</span></span>|  
|<span data-ttu-id="3455f-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="3455f-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="3455f-285">x.name</span><span class="sxs-lookup"><span data-stu-id="3455f-285">x.name</span></span>|<span data-ttu-id="3455f-286">4</span><span class="sxs-lookup"><span data-stu-id="3455f-286">4</span></span>|  
|<span data-ttu-id="3455f-287">Colonna</span><span class="sxs-lookup"><span data-stu-id="3455f-287">Column</span></span>|@Column|<span data-ttu-id="3455f-288">c.name</span><span class="sxs-lookup"><span data-stu-id="3455f-288">c.name</span></span>|<span data-ttu-id="3455f-289">5</span><span class="sxs-lookup"><span data-stu-id="3455f-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3455f-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="3455f-290">Indexes</span></span>  
  
|<span data-ttu-id="3455f-291">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-291">Restriction Name</span></span>|<span data-ttu-id="3455f-292">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-292">Parameter Name</span></span>|<span data-ttu-id="3455f-293">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-293">Restriction Default</span></span>|<span data-ttu-id="3455f-294">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-295">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="3455f-296">db_name()</span></span>|<span data-ttu-id="3455f-297">1</span><span class="sxs-lookup"><span data-stu-id="3455f-297">1</span></span>|  
|<span data-ttu-id="3455f-298">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-298">Owner</span></span>|@Owner|<span data-ttu-id="3455f-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="3455f-299">user_name()</span></span>|<span data-ttu-id="3455f-300">2</span><span class="sxs-lookup"><span data-stu-id="3455f-300">2</span></span>|  
|<span data-ttu-id="3455f-301">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-301">Table</span></span>|@Table|<span data-ttu-id="3455f-302">o.name</span><span class="sxs-lookup"><span data-stu-id="3455f-302">o.name</span></span>|<span data-ttu-id="3455f-303">3</span><span class="sxs-lookup"><span data-stu-id="3455f-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="3455f-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="3455f-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="3455f-305">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-305">Restriction Name</span></span>|<span data-ttu-id="3455f-306">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-306">Parameter Name</span></span>|<span data-ttu-id="3455f-307">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-307">Restriction Default</span></span>|<span data-ttu-id="3455f-308">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="3455f-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="3455f-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="3455f-310">assemblies.name</span></span>|<span data-ttu-id="3455f-311">1</span><span class="sxs-lookup"><span data-stu-id="3455f-311">1</span></span>|  
|<span data-ttu-id="3455f-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="3455f-312">udt_name</span></span>|@UDTName|<span data-ttu-id="3455f-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="3455f-313">types.assembly_class</span></span>|<span data-ttu-id="3455f-314">2</span><span class="sxs-lookup"><span data-stu-id="3455f-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="3455f-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="3455f-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="3455f-316">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-316">Restriction Name</span></span>|<span data-ttu-id="3455f-317">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-317">Parameter Name</span></span>|<span data-ttu-id="3455f-318">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-318">Restriction Default</span></span>|<span data-ttu-id="3455f-319">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-320">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="3455f-322">1</span><span class="sxs-lookup"><span data-stu-id="3455f-322">1</span></span>|  
|<span data-ttu-id="3455f-323">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-323">Owner</span></span>|@Owner|<span data-ttu-id="3455f-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="3455f-325">2</span><span class="sxs-lookup"><span data-stu-id="3455f-325">2</span></span>|  
|<span data-ttu-id="3455f-326">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-326">Table</span></span>|@Table|<span data-ttu-id="3455f-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-327">TABLE_NAME</span></span>|<span data-ttu-id="3455f-328">3</span><span class="sxs-lookup"><span data-stu-id="3455f-328">3</span></span>|  
|<span data-ttu-id="3455f-329">Name</span><span class="sxs-lookup"><span data-stu-id="3455f-329">Name</span></span>|@Name|<span data-ttu-id="3455f-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="3455f-331">4</span><span class="sxs-lookup"><span data-stu-id="3455f-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="3455f-332">Restrizioni per gli schemi di SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="3455f-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="3455f-333">Nelle tabelle seguenti sono incluse le restrizioni per le raccolte di schemi di SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3455f-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="3455f-334">Queste restrizioni sono valide a partire dalla versione 3.5 SP1 di .NET Framework e da SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="3455f-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="3455f-335">Le restrizioni non sono supportate nelle versioni precedenti di .NET Framework e di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3455f-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="3455f-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="3455f-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="3455f-337">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-337">Restriction Name</span></span>|<span data-ttu-id="3455f-338">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-338">Parameter Name</span></span>|<span data-ttu-id="3455f-339">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-339">Restriction Default</span></span>|<span data-ttu-id="3455f-340">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-341">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-342">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-343">1</span><span class="sxs-lookup"><span data-stu-id="3455f-343">1</span></span>|  
|<span data-ttu-id="3455f-344">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-344">Owner</span></span>|@Owner|<span data-ttu-id="3455f-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-346">2</span><span class="sxs-lookup"><span data-stu-id="3455f-346">2</span></span>|  
|<span data-ttu-id="3455f-347">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-347">Table</span></span>|@Table|<span data-ttu-id="3455f-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-348">TABLE_NAME</span></span>|<span data-ttu-id="3455f-349">3</span><span class="sxs-lookup"><span data-stu-id="3455f-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="3455f-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="3455f-350">AllColumns</span></span>  
  
|<span data-ttu-id="3455f-351">Nome della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-351">Restriction Name</span></span>|<span data-ttu-id="3455f-352">Nome parametro</span><span class="sxs-lookup"><span data-stu-id="3455f-352">Parameter Name</span></span>|<span data-ttu-id="3455f-353">Impostazione predefinita della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-353">Restriction Default</span></span>|<span data-ttu-id="3455f-354">Numero della restrizione</span><span class="sxs-lookup"><span data-stu-id="3455f-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3455f-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="3455f-355">Catalog</span></span>|@Catalog|<span data-ttu-id="3455f-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3455f-356">TABLE_CATALOG</span></span>|<span data-ttu-id="3455f-357">1</span><span class="sxs-lookup"><span data-stu-id="3455f-357">1</span></span>|  
|<span data-ttu-id="3455f-358">Proprietario</span><span class="sxs-lookup"><span data-stu-id="3455f-358">Owner</span></span>|@Owner|<span data-ttu-id="3455f-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3455f-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="3455f-360">2</span><span class="sxs-lookup"><span data-stu-id="3455f-360">2</span></span>|  
|<span data-ttu-id="3455f-361">Tabella</span><span class="sxs-lookup"><span data-stu-id="3455f-361">Table</span></span>|@Table|<span data-ttu-id="3455f-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-362">TABLE_NAME</span></span>|<span data-ttu-id="3455f-363">3</span><span class="sxs-lookup"><span data-stu-id="3455f-363">3</span></span>|  
|<span data-ttu-id="3455f-364">Colonna</span><span class="sxs-lookup"><span data-stu-id="3455f-364">Column</span></span>|@Column|<span data-ttu-id="3455f-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3455f-365">COLUMN_NAME</span></span>|<span data-ttu-id="3455f-366">4</span><span class="sxs-lookup"><span data-stu-id="3455f-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3455f-367">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3455f-367">See also</span></span>

- [<span data-ttu-id="3455f-368">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3455f-368">ADO.NET Overview</span></span>](ado-net-overview.md)
