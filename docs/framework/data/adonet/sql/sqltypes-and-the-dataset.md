---
title: SqlTypes e DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791495"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="efdfb-102">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="efdfb-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="efdfb-103">In ADO.NET 2.0 è stato introdotto il supporto migliorato per i tipi per `DataSet` tramite lo spazio dei nomi  <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="efdfb-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="efdfb-104">I tipi <xref:System.Data.SqlTypes> sono progettati per fornire tipi di dati con la stessa semantica e la stessa precisione dei tipi di dati di un database di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="efdfb-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="efdfb-105">Ogni tipo di dati in <xref:System.Data.SqlTypes> dispone di un tipo di dati equivalente in SQL Server, con la stessa rappresentazione di dati sottostante.</span><span class="sxs-lookup"><span data-stu-id="efdfb-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="efdfb-106">L'utilizzo di <xref:System.Data.SqlTypes> direttamente in un oggetto <xref:System.Data.DataSet> offre numerosi vantaggi quando si lavora con tipi di dati SQL Server.</span><span class="sxs-lookup"><span data-stu-id="efdfb-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="efdfb-107"><xref:System.Data.SqlTypes> supporta la stessa semantica dei tipi di dati nativi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="efdfb-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="efdfb-108">La specifica di uno degli oggetti <xref:System.Data.SqlTypes> nella definizione di un oggetto <xref:System.Data.DataColumn> elimina la perdita di precisione che può verificarsi in caso di conversione di tipi di dati numerici o decimali in uno dei tipi di dati CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="efdfb-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efdfb-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="efdfb-109">Example</span></span>  
 <span data-ttu-id="efdfb-110">Nell'esempio seguente viene creato un oggetto <xref:System.Data.DataTable>, definendo in modo esplicito i tipi di dati <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> invece dei tipi CLR.</span><span class="sxs-lookup"><span data-stu-id="efdfb-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="efdfb-111">Il codice consente di compilare <xref:System.Data.DataTable> con i dati della tabella Sales.SalesOrderDetail nel database AdventureWorks in SQL Server.</span><span class="sxs-lookup"><span data-stu-id="efdfb-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="efdfb-112">L'output visualizzato nella finestra della console mostra i tipi di dati di ogni colonna e i valori recuperati da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="efdfb-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="efdfb-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="efdfb-113">See also</span></span>

- [<span data-ttu-id="efdfb-114">Mapping dei tipi di dati SQL Server</span><span class="sxs-lookup"><span data-stu-id="efdfb-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="efdfb-115">Configurazione di parametri e tipi di dati dei parametri</span><span class="sxs-lookup"><span data-stu-id="efdfb-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="efdfb-116">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="efdfb-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
