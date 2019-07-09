---
title: Problemi noti e considerazioni in LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: d7d87a3e95cf66efb91b71f6ff3c7c9bb1fbb311
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662141"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="8ae48-102">Problemi noti e considerazioni in LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8ae48-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="8ae48-103">Questa sezione vengono fornite informazioni sui problemi noti con LINQ alle query di entità.</span><span class="sxs-lookup"><span data-stu-id="8ae48-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="8ae48-104">Query LINQ che non possono essere memorizzati nella cache</span><span class="sxs-lookup"><span data-stu-id="8ae48-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="8ae48-105">Perdita di informazioni di ordinamento</span><span class="sxs-lookup"><span data-stu-id="8ae48-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="8ae48-106">Interi senza segno non è supportati</span><span class="sxs-lookup"><span data-stu-id="8ae48-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="8ae48-107">Errori di conversione tipo</span><span class="sxs-lookup"><span data-stu-id="8ae48-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="8ae48-108">Riferimento alle variabili Non scalari non supportate</span><span class="sxs-lookup"><span data-stu-id="8ae48-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="8ae48-109">Query nidificata potrebbe non riuscire con SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="8ae48-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="8ae48-110">Proiezione di un tipo anonimo</span><span class="sxs-lookup"><span data-stu-id="8ae48-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="8ae48-111">Query LINQ che non possono essere memorizzate nella cache</span><span class="sxs-lookup"><span data-stu-id="8ae48-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="8ae48-112">A partire da .NET Framework 4.5, le query LINQ to Entities vengono memorizzate nella cache automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8ae48-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="8ae48-113">Tuttavia, le query LINQ to Entities che applicano l'operatore `Enumerable.Contains` alle raccolte in memoria non vengono memorizzate automaticamente nella cache.</span><span class="sxs-lookup"><span data-stu-id="8ae48-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="8ae48-114">Inoltre, la parametrizzazione delle raccolte in memoria nelle query LINQ compilate non è consentita.</span><span class="sxs-lookup"><span data-stu-id="8ae48-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="8ae48-115">Perdita delle informazioni di ordinamento</span><span class="sxs-lookup"><span data-stu-id="8ae48-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="8ae48-116">Proiezione di colonne in un tipo anonimo causerà informazioni di ordinamento andranno persi in alcune query eseguite su un database di SQL Server 2005 impostato su un livello di compatibilità pari a "80".</span><span class="sxs-lookup"><span data-stu-id="8ae48-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="8ae48-117">Questo avviene quando un nome di colonna nell'elenco di ordinamento corrisponde a un nome di colonna nel selettore, come illustrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="8ae48-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="8ae48-118">Mancato supporto degli Unsigned Integer</span><span class="sxs-lookup"><span data-stu-id="8ae48-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="8ae48-119">Specificare un tipo unsigned integer in una query LINQ to Entities non è supportata perché il [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] non supporta interi senza segno.</span><span class="sxs-lookup"><span data-stu-id="8ae48-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="8ae48-120">Se si specifica un unsigned integer, un <xref:System.ArgumentException> verrà generata l'eccezione durante la conversione di espressioni di query, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="8ae48-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="8ae48-121">In questo esempio viene eseguita una query per un ordine con ID 48000.</span><span class="sxs-lookup"><span data-stu-id="8ae48-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="8ae48-122">Errori di conversione dei tipi</span><span class="sxs-lookup"><span data-stu-id="8ae48-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="8ae48-123">In Visual Basic quando una proprietà è mappata a una colonna di tipo bit SQL Server con un valore 1 usando la funzione `CByte`, viene generato un evento <xref:System.Data.SqlClient.SqlException> con un messaggio di errore di overflow aritmetico.</span><span class="sxs-lookup"><span data-stu-id="8ae48-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="8ae48-124">Nell'esempio seguente viene eseguita una query sulla colonna `Product.MakeFlag` nel database di esempio AdventureWorks e viene generata un'eccezione quando viene eseguita un'iterazione dei risultati della query.</span><span class="sxs-lookup"><span data-stu-id="8ae48-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="8ae48-125">Riferimento a variabili non scalari non supportato</span><span class="sxs-lookup"><span data-stu-id="8ae48-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="8ae48-126">Il riferimento in una query a variabili non scalari, ad esempio un'entità, non è supportato.</span><span class="sxs-lookup"><span data-stu-id="8ae48-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="8ae48-127">Durante l'esecuzione di una query di questo tipo, viene generata un'eccezione <xref:System.NotSupportedException>, seguita dal messaggio "Impossibile creare un valore di costante di tipo `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="8ae48-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="8ae48-128">In questo contesto solo supportati solo i tipi primitivi ('ad esempio Int32, String e GUID')".</span><span class="sxs-lookup"><span data-stu-id="8ae48-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ae48-129">Il riferimento a una raccolta di variabili scalari supportato.</span><span class="sxs-lookup"><span data-stu-id="8ae48-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="8ae48-130">Errori di esecuzione di query annidate con SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="8ae48-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="8ae48-131">Con SQL Server 2000, è possibile che le query LINQ to Entities non vengano eseguite correttamente se producono query Transact-SQL annidate con tre o più livelli di profondità.</span><span class="sxs-lookup"><span data-stu-id="8ae48-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="8ae48-132">Proiezione in un tipo anonimo</span><span class="sxs-lookup"><span data-stu-id="8ae48-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="8ae48-133">Se si definisce il percorso iniziale della query per includere gli oggetti correlati tramite il metodo <xref:System.Data.Objects.ObjectQuery%601.Include%2A> su <xref:System.Data.Objects.ObjectQuery%601> e si usa quindi LINQ per proiettare gli oggetti restituiti in un tipo anonimo, gli oggetti specificati nel metodo di inclusione non vengono inclusi nei risultati della query.</span><span class="sxs-lookup"><span data-stu-id="8ae48-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="8ae48-134">Per ottenere oggetti correlati, non proiettare i tipi restituiti in un tipo anonimo.</span><span class="sxs-lookup"><span data-stu-id="8ae48-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="8ae48-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8ae48-135">See also</span></span>

- [<span data-ttu-id="8ae48-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8ae48-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
