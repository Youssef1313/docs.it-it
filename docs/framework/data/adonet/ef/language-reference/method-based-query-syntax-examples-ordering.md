---
title: 'Esempi di sintassi delle query basate su metodo: Ordering'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: e10101e2a3534d981b2126884a2a61b411254477
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397324"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="52a0b-102">Esempi di sintassi delle query basate su metodo: Ordering</span><span class="sxs-lookup"><span data-stu-id="52a0b-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="52a0b-103">Negli esempi di questo argomento viene illustrato come utilizzare il <xref:System.Linq.Enumerable.ThenBy%2A> metodo per eseguire query sul [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) utilizzando la sintassi delle query basate su metodo.</span><span class="sxs-lookup"><span data-stu-id="52a0b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="52a0b-104">Il modello Sales di AdventureWorks usato in questi esempi è compilato in base alle tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="52a0b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="52a0b-105">Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`</span><span class="sxs-lookup"><span data-stu-id="52a0b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="52a0b-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="52a0b-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="52a0b-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="52a0b-107">Example</span></span>  
 <span data-ttu-id="52a0b-108">Nell'esempio seguente nella sintassi delle query basate su metodo vengono usati gli oggetti <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenBy%2A> per restituire un elenco di contatti ordinati in base al cognome e quindi al nome.</span><span class="sxs-lookup"><span data-stu-id="52a0b-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="52a0b-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="52a0b-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="52a0b-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="52a0b-110">Example</span></span>  
 <span data-ttu-id="52a0b-111">Nell'esempio seguente vengono usati i metodi <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenByDescending%2A> per eseguire prima l'ordinamento in base al prezzo di listino e quindi per applicare un ordinamento decrescente ai nomi di prodotto.</span><span class="sxs-lookup"><span data-stu-id="52a0b-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="52a0b-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="52a0b-112">See also</span></span>

- [<span data-ttu-id="52a0b-113">Query in LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="52a0b-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
