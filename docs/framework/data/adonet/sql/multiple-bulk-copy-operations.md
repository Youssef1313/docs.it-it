---
title: Più operazioni di copia di massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 8ee0fdbfc167c819942d8282aca56b7c5168fd87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946856"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="316bc-102">Più operazioni di copia di massa</span><span class="sxs-lookup"><span data-stu-id="316bc-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="316bc-103">È possibile eseguire più operazioni di copia di massa usando una singola istanza di una classe <xref:System.Data.SqlClient.SqlBulkCopy>.</span><span class="sxs-lookup"><span data-stu-id="316bc-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="316bc-104">Se i parametri dell'operazione cambiano tra le copie (ad esempio, il nome della tabella di destinazione), è necessario aggiornarli prima di qualsiasi chiamata successiva a uno dei metodi **WriteToServer** , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="316bc-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="316bc-105">Se non vengono modificati in modo esplicito, tutti i valori delle proprietà rimangono identici a quelli dell'operazione di copia di massa precedente per una determinata istanza.</span><span class="sxs-lookup"><span data-stu-id="316bc-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="316bc-106">L'esecuzione di più operazioni di copia di massa con la stessa istanza di <xref:System.Data.SqlClient.SqlBulkCopy> è generalmente più efficace rispetto all'utilizzo di un'istanza distinta per ogni operazione.</span><span class="sxs-lookup"><span data-stu-id="316bc-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="316bc-107">Se si eseguono diverse operazioni di copia di massa usando lo stesso oggetto <xref:System.Data.SqlClient.SqlBulkCopy>, non vi sono restrizioni sulla corrispondenza o meno tra le informazioni di origine o di destinazione di ciascuna operazione.</span><span class="sxs-lookup"><span data-stu-id="316bc-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="316bc-108">Tuttavia, è necessario verificare che le informazioni di associazione della colonna siano impostate correttamente ogni volta che si scrive sul server.</span><span class="sxs-lookup"><span data-stu-id="316bc-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="316bc-109">Questo esempio non verrà eseguito a meno che non siano state create le tabelle di lavoro come descritto in configurazione di esempio per la [copia bulk](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="316bc-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="316bc-110">Questo codice viene fornito per illustrare la sintassi per l'utilizzo solo di **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="316bc-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="316bc-111">Se la tabella di origine e quella di destinazione risiedono nella stessa istanza di SQL Server, per copiare i dati è più semplice e rapido usare un'istruzione `INSERT … SELECT` Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="316bc-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="316bc-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="316bc-112">See also</span></span>

- [<span data-ttu-id="316bc-113">Operazioni di copia di massa in SQL Server</span><span class="sxs-lookup"><span data-stu-id="316bc-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="316bc-114">Provider gestiti ADO.NET e Centro per sviluppatori di set di dati</span><span class="sxs-lookup"><span data-stu-id="316bc-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
