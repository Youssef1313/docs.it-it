---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 711fbdc2d51177037cf349150c3431de14b11974
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833786"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="cf13c-102">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cf13c-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="cf13c-103">Specifica i gruppi nei quali devono essere inseriti gli oggetti restituiti da un'espressione ([SELECT](select-entity-sql.md)) di query.</span><span class="sxs-lookup"><span data-stu-id="cf13c-103">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf13c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cf13c-104">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf13c-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="cf13c-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="cf13c-106">Qualsiasi espressione di query valida sulla quale viene eseguito il raggruppamento.</span><span class="sxs-lookup"><span data-stu-id="cf13c-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="cf13c-107">`expression` può essere una proprietà o un'espressione non di aggregazione che fa riferimento a una proprietà restituita dalla clausola FROM.</span><span class="sxs-lookup"><span data-stu-id="cf13c-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="cf13c-108">Ogni espressione in una clausola GROUP BY deve restituire un tipo che può essere confrontato per verificare l'uguaglianza.</span><span class="sxs-lookup"><span data-stu-id="cf13c-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="cf13c-109">Questi tipi sono in genere tipi primitivi scalari ad esempio numeri, stringhe e date.</span><span class="sxs-lookup"><span data-stu-id="cf13c-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="cf13c-110">Non è possibile eseguire un raggruppamento in base a una raccolta.</span><span class="sxs-lookup"><span data-stu-id="cf13c-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf13c-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="cf13c-111">Remarks</span></span>  
 <span data-ttu-id="cf13c-112">Se nella clausola SELECT sono incluse funzioni di aggregazione \<select list >, GROUP BY calcola un valore di riepilogo per ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="cf13c-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="cf13c-113">Quando si specifica GROUP BY, è necessario che l'elenco GROUP BY includa ogni nome di proprietà di qualsiasi espressione non di aggregazione nell'elenco di selezione oppure che l'espressione GROUP BY corrisponda esattamente all'espressione dell'elenco di selezione.</span><span class="sxs-lookup"><span data-stu-id="cf13c-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf13c-114">Se la clausola ORDER BY non viene specificata, i gruppi restituiti dalla clausola GROUP BY non sono in un ordine preciso.</span><span class="sxs-lookup"><span data-stu-id="cf13c-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="cf13c-115">Per specificare un particolare ordinamento dei dati, è consigliabile usare sempre la clausola ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="cf13c-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="cf13c-116">Quando una clausola GROUP BY viene specificata, in modo esplicito o implicito (ad esempio da una clausola HAVING nella query), l'ambito corrente viene nascosto e viene introdotto un nuovo ambito.</span><span class="sxs-lookup"><span data-stu-id="cf13c-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="cf13c-117">La clausola SELECT, la clausola HAVING e la clausola ORDER BY non potranno più fare riferimento ai nomi di elementi specificati nella clausola FROM.</span><span class="sxs-lookup"><span data-stu-id="cf13c-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="cf13c-118">È possibile fare riferimento solo alle espressioni di raggruppamento stesse.</span><span class="sxs-lookup"><span data-stu-id="cf13c-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="cf13c-119">A tale scopo, è possibile assegnare nuovi nomi (alias) a ogni espressione di raggruppamento.</span><span class="sxs-lookup"><span data-stu-id="cf13c-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="cf13c-120">Se per un'espressione di raggruppamento non viene specificato alcun alias, in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] viene eseguito un tentativo di generarne uno usando le regole di generazione di alias, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="cf13c-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="cf13c-121">Le espressioni nella clausola GROUP BY non possono fare riferimento a nomi definiti in precedenza nella stessa clausola GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="cf13c-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="cf13c-122">Oltre ai nomi dei raggruppamenti, nella clausola SELECT, nella clausola HAVING e nella clausola ORDER BY è possibile specificare anche aggregazioni.</span><span class="sxs-lookup"><span data-stu-id="cf13c-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="cf13c-123">Un'aggregazione contiene un'espressione valutata per ogni elemento del gruppo.</span><span class="sxs-lookup"><span data-stu-id="cf13c-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="cf13c-124">L'operatore di aggregazione riduce i valori di tutte queste espressioni, in genere, ma non sempre, in un singolo valore.</span><span class="sxs-lookup"><span data-stu-id="cf13c-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="cf13c-125">L'espressione di aggregazione può fare riferimento ai nomi degli elementi originali visibili nell'ambito padre o ai nuovi nomi introdotti dalla clausola GROUP BY stessa.</span><span class="sxs-lookup"><span data-stu-id="cf13c-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="cf13c-126">Sebbene le aggregazioni siano presenti nella clausola SELECT, nella clausola HAVING e nella clausola ORDER BY, vengono effettivamente valutate nello stesso ambito delle espressioni di raggruppamento, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="cf13c-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="cf13c-127">In questa query viene usata la clausola GROUP BY per produrre un rapporto del costo di tutti i prodotti ordinati, suddiviso in base al prodotto.</span><span class="sxs-lookup"><span data-stu-id="cf13c-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="cf13c-128">Viene assegnato il nome `name` al prodotto come parte dell'espressione di raggruppamento, quindi viene fatto riferimento a tale nome nell'elenco SELECT.</span><span class="sxs-lookup"><span data-stu-id="cf13c-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="cf13c-129">Viene inoltre specificata la funzione `sum` di aggregazione nell'elenco SELECT, che fa riferimento internamente al prezzo e alla quantità della riga dell'ordine.</span><span class="sxs-lookup"><span data-stu-id="cf13c-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="cf13c-130">Ogni espressione chiave GROUP BY deve includere almeno un riferimento all'ambito di input:</span><span class="sxs-lookup"><span data-stu-id="cf13c-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="cf13c-131">Per un esempio dell'uso di GROUP BY, vedere [HAVING](having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cf13c-131">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf13c-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="cf13c-132">Example</span></span>  
 <span data-ttu-id="cf13c-133">Nella query Entity SQL seguente viene usato l'operatore GROUP BY per specificare i gruppi in cui gli oggetti vengono restituiti da una query.</span><span class="sxs-lookup"><span data-stu-id="cf13c-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="cf13c-134">La query è basata sul modello Sales di AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cf13c-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cf13c-135">Per compilare ed eseguire questa query, effettuare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cf13c-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cf13c-136">Attenersi alla procedura descritta in [procedura: eseguire una query che restituisce i risultati di PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cf13c-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="cf13c-137">Passare la query seguente come argomento al metodo `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="cf13c-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="cf13c-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf13c-138">See also</span></span>

- [<span data-ttu-id="cf13c-139">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cf13c-139">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="cf13c-140">Espressioni di query</span><span class="sxs-lookup"><span data-stu-id="cf13c-140">Query Expressions</span></span>](query-expressions-entity-sql.md)
