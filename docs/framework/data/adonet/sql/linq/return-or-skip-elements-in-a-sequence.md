---
title: Restituire o ignorare elementi in una sequenza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: e0f2c6300f8dccb8cc316527af9c75f6a40ff2df
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661905"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="436ef-102">Restituire o ignorare elementi in una sequenza</span><span class="sxs-lookup"><span data-stu-id="436ef-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="436ef-103">Usare l'operatore <xref:System.Linq.Queryable.Take%2A> per restituire un numero specificato di elementi in una sequenza e ignorare quindi gli elementi rimanenti.</span><span class="sxs-lookup"><span data-stu-id="436ef-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="436ef-104">Usare l'operatore <xref:System.Linq.Queryable.Skip%2A> per ignorare un numero specificato di elementi in una sequenza, quindi restituire gli elementi rimanenti.</span><span class="sxs-lookup"><span data-stu-id="436ef-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ef-105"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> presentano alcune limitazioni quando vengono usati nelle query su SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="436ef-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="436ef-106">Per altre informazioni, vedere la voce "Skip e Take eccezioni in SQL Server 2000" nella [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="436ef-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="436ef-107">traduce <xref:System.Linq.Queryable.Skip%2A> usando una sottoquery con il codice SQL `NOT EXISTS` clausola.</span><span class="sxs-lookup"><span data-stu-id="436ef-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="436ef-108">Di seguito vengono elencate le limitazioni di questa conversione.</span><span class="sxs-lookup"><span data-stu-id="436ef-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="436ef-109">L'argomento deve essere un set.</span><span class="sxs-lookup"><span data-stu-id="436ef-109">The argument must be a set.</span></span> <span data-ttu-id="436ef-110">I tipi multiset non sono supportati, anche se ordinati.</span><span class="sxs-lookup"><span data-stu-id="436ef-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="436ef-111">La query generata può essere molto più complessa di quella generata per la query di base a cui viene applicato <xref:System.Linq.Queryable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="436ef-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="436ef-112">Questa complessità può provocare una riduzione delle prestazioni o il timeout dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="436ef-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="436ef-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="436ef-113">Example</span></span>  
 <span data-ttu-id="436ef-114">Nell'esempio seguente viene usato `Take` per selezionare i primi cinque dipendenti assunti in `Employees`.</span><span class="sxs-lookup"><span data-stu-id="436ef-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="436ef-115">Notare che la raccolta viene prima ordinata per `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="436ef-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="436ef-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="436ef-116">Example</span></span>  
 <span data-ttu-id="436ef-117">Nell'esempio seguente viene usato <xref:System.Linq.Queryable.Skip%2A> per selezionare tutti i prodotti tranne i 10 più costosi nella tabella `Products`.</span><span class="sxs-lookup"><span data-stu-id="436ef-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="436ef-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="436ef-118">Example</span></span>  
 <span data-ttu-id="436ef-119">Nell'esempio seguente vengono combinati i metodi <xref:System.Linq.Queryable.Skip%2A> e <xref:System.Linq.Queryable.Take%2A> per ignorare i primi 50 record e restituire quindi i 10 successivi.</span><span class="sxs-lookup"><span data-stu-id="436ef-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="436ef-120">Le operazioni <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> sono definite correttamente solo per i set ordinati,</span><span class="sxs-lookup"><span data-stu-id="436ef-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="436ef-121">mentre la semantica per i set non ordinati o i tipi multiset non è definita.</span><span class="sxs-lookup"><span data-stu-id="436ef-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="436ef-122">A causa delle limitazioni relative all'ordinamento in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta di spostare l'ordinamento dell'argomento dell'operatore <xref:System.Linq.Queryable.Take%2A> o <xref:System.Linq.Queryable.Skip%2A> nel risultato dell'operatore.</span><span class="sxs-lookup"><span data-stu-id="436ef-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ef-123">La conversione è diversa per SQL Server 2000 e SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="436ef-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="436ef-124">Se si prevede di usare <xref:System.Linq.Queryable.Skip%2A> con una query di qualsiasi complessità, usare SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="436ef-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="436ef-125">Tenere presente quanto segue [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query per SQL Server 2000:</span><span class="sxs-lookup"><span data-stu-id="436ef-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="436ef-126">sposta l'ordinamento alla fine nel codice SQL, come segue:</span><span class="sxs-lookup"><span data-stu-id="436ef-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="436ef-127">Quando <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> sono concatenati, tutti i tipi di ordinamento specificati devono essere coerenti.</span><span class="sxs-lookup"><span data-stu-id="436ef-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="436ef-128">In caso contrario i risultati non saranno definiti.</span><span class="sxs-lookup"><span data-stu-id="436ef-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="436ef-129">Per gli argomenti di tipo integrale costante non negativi, basati sulla specifica SQL, <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> sono definiti correttamente.</span><span class="sxs-lookup"><span data-stu-id="436ef-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436ef-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="436ef-130">See also</span></span>

- [<span data-ttu-id="436ef-131">Esempi di query</span><span class="sxs-lookup"><span data-stu-id="436ef-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="436ef-132">Conversione dell'operatore query standard</span><span class="sxs-lookup"><span data-stu-id="436ef-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
