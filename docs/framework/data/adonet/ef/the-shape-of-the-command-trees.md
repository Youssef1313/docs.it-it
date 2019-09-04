---
title: Forma degli alberi dei comandi
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248228"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="885c5-102">Forma degli alberi dei comandi</span><span class="sxs-lookup"><span data-stu-id="885c5-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="885c5-103">Il modulo di generazione SQL è responsabile della generazione di una query SQL specifica di back-end basata su una determinata espressione dell'albero dei comandi della query di input.</span><span class="sxs-lookup"><span data-stu-id="885c5-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="885c5-104">Questa sezione descrive le caratteristiche, le proprietà e la forma degli alberi dei comandi di query.</span><span class="sxs-lookup"><span data-stu-id="885c5-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="885c5-105">Panoramica degli alberi dei comandi di query</span><span class="sxs-lookup"><span data-stu-id="885c5-105">Query Command Trees Overview</span></span>

<span data-ttu-id="885c5-106">Un albero dei comandi di query è una rappresentazione del modello a oggetti di una query.</span><span class="sxs-lookup"><span data-stu-id="885c5-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="885c5-107">Tali alberi dei comandi di query hanno due funzioni:</span><span class="sxs-lookup"><span data-stu-id="885c5-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="885c5-108">Esprimere una query di input specificata per [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="885c5-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="885c5-109">Esprimere una query di output specificata per un provider, che descrive una query sul back-end.</span><span class="sxs-lookup"><span data-stu-id="885c5-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="885c5-110">Gli alberi dei comandi di query supportano una semantica più completa rispetto alle query conformi a SQL:1999, che include il supporto per l'uso di raccolte annidate e l'esecuzione di operazioni sui tipi, ad esempio quelle per verificare se un'entità è di un determinato tipo o filtrare i set in base a un tipo.</span><span class="sxs-lookup"><span data-stu-id="885c5-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="885c5-111">La proprietà DBQueryCommandTree.Query è la radice dell'albero delle espressioni che descrive la logica della query.</span><span class="sxs-lookup"><span data-stu-id="885c5-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="885c5-112">La proprietà DBQueryCommandTree.Parameters contiene un elenco di parametri usati nella query.</span><span class="sxs-lookup"><span data-stu-id="885c5-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="885c5-113">L'albero delle espressioni è costituito da oggetti DbExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="885c5-114">Un oggetto DbExpression rappresenta un'attività di calcolo.</span><span class="sxs-lookup"><span data-stu-id="885c5-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="885c5-115">In [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sono disponibili diversi tipi di espressione per la creazione di espressioni di query, incluse costanti, variabili, funzioni, costruttori e operatori relazionali standard come gli operatori di filtro e join.</span><span class="sxs-lookup"><span data-stu-id="885c5-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="885c5-116">Ogni oggetto DbExpression dispone di una proprietà ResultType che rappresenta il tipo del risultato prodotto da tale espressione.</span><span class="sxs-lookup"><span data-stu-id="885c5-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="885c5-117">Questo tipo viene espresso come TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="885c5-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="885c5-118">Forme dell'albero dei comandi di query di output</span><span class="sxs-lookup"><span data-stu-id="885c5-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="885c5-119">Gli alberi dei comandi di query di output rappresentano in modo accurato query SQL relazionali e rispettano regole più rigorose rispetto a quelle applicate agli alberi dei comandi di query.</span><span class="sxs-lookup"><span data-stu-id="885c5-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="885c5-120">Contengono in genere costrutti che vengono convertiti facilmente in SQL.</span><span class="sxs-lookup"><span data-stu-id="885c5-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="885c5-121">Gli alberi dei comandi di input vengono espresse in base al modello concettuale, che supporta proprietà di navigazione, associazioni tra entità ed ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="885c5-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="885c5-122">Gli alberi dei comandi di output vengono espresse in base al modello di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="885c5-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="885c5-123">Diversamente da questi ultimi, gli alberi dei comandi di input consentono di proiettare raccolte annidate.</span><span class="sxs-lookup"><span data-stu-id="885c5-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="885c5-124">Gli alberi dei comandi di query di output vengono compilati usando un subset degli oggetti DbExpression disponibili, che contiene alcune espressioni con un utilizzo limitato.</span><span class="sxs-lookup"><span data-stu-id="885c5-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="885c5-125">Le operazioni sui tipi, ad esempio quelle per verificare se una determinata espressione è di un tipo specifico o filtrare i set in base a un tipo, non sono presenti negli alberi dei comandi di output.</span><span class="sxs-lookup"><span data-stu-id="885c5-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="885c5-126">Negli alberi dei comandi di output solo le espressioni che restituiscono valori booleani vengono usate per le proiezioni e solo per i predicati nelle espressioni che richiedono un predicato, ad esempio un'istruzione Case o per il filtro.</span><span class="sxs-lookup"><span data-stu-id="885c5-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="885c5-127">La radice degli alberi dei comandi di query di output è un oggetto DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="885c5-128">Tipi di espressione non inclusi negli alberi dei comandi di query di output</span><span class="sxs-lookup"><span data-stu-id="885c5-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="885c5-129">I tipi di espressione seguenti non sono validi in un albero dei comandi di query di output e non devono essere gestiti dai provider:</span><span class="sxs-lookup"><span data-stu-id="885c5-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="885c5-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-130">DbDerefExpression</span></span>

- <span data-ttu-id="885c5-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="885c5-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="885c5-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-133">DbIsOfExpression</span></span>

- <span data-ttu-id="885c5-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="885c5-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-135">DbRefExpression</span></span>

- <span data-ttu-id="885c5-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="885c5-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="885c5-138">Restrizioni e note relative alle espressioni</span><span class="sxs-lookup"><span data-stu-id="885c5-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="885c5-139">Molte espressioni possono essere usate solo in modo limitato negli alberi dei comandi di query di output:</span><span class="sxs-lookup"><span data-stu-id="885c5-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="885c5-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-140">DbFunctionExpression</span></span>

<span data-ttu-id="885c5-141">È possibile passare i tipi di funzione seguenti:</span><span class="sxs-lookup"><span data-stu-id="885c5-141">The following function types can be passed:</span></span>

- <span data-ttu-id="885c5-142">Funzioni canoniche riconosciute dallo spazio dei nomi Edm.</span><span class="sxs-lookup"><span data-stu-id="885c5-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="885c5-143">Funzioni di archivio predefinite riconosciute da BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="885c5-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="885c5-144">Funzioni definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="885c5-144">User-defined functions.</span></span>

<span data-ttu-id="885c5-145">Le funzioni canoniche (vedere [funzioni canoniche](./language-reference/canonical-functions.md) per ulteriori informazioni) vengono specificate come [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]parte di e i provider devono fornire implementazioni per le funzioni canoniche basate su tali specifiche.</span><span class="sxs-lookup"><span data-stu-id="885c5-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="885c5-146">Le funzioni di archivio si basano sulle specifiche contenute nel file manifesto del provider corrispondente.</span><span class="sxs-lookup"><span data-stu-id="885c5-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="885c5-147">Le funzioni definite dall'utente si basano sulle specifiche di SSDL.</span><span class="sxs-lookup"><span data-stu-id="885c5-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="885c5-148">Inoltre, le funzioni che includono l'attributo NiladicFunction non dispongono di argomenti e devono essere convertite senza la parentesi finale,</span><span class="sxs-lookup"><span data-stu-id="885c5-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="885c5-149">Ovvero, per  *\<FunctionName*  *\<> anziché FunctionName > ()* .</span><span class="sxs-lookup"><span data-stu-id="885c5-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="885c5-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="885c5-151">DbNewInstanceExpression può essere specificato solo nei due casi seguenti:</span><span class="sxs-lookup"><span data-stu-id="885c5-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="885c5-152">Come proprietà Projection di DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="885c5-153">In questo caso, vengono applicate le restrizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="885c5-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="885c5-154">Il risultato deve essere un tipo di riga.</span><span class="sxs-lookup"><span data-stu-id="885c5-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="885c5-155">I relativi argomenti devono essere espressioni che producono un risultato con un tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="885c5-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="885c5-156">In genere, ogni argomento è un'espressione scalare, ad esempio un oggetto PropertyExpression su un oggetto DbVariableReferenceExpression, una chiamata a una funzione o un calcolo aritmetico di DbPropertyExpression su un oggetto DbVariableReferenceExpression o una chiamata a una funzione.</span><span class="sxs-lookup"><span data-stu-id="885c5-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="885c5-157">È tuttavia possibile specificare un'espressione che rappresenta una subquery scalare anche nell'elenco di argomenti di un oggetto DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="885c5-158">Un'espressione che rappresenta una sottoquery scalare è un albero delle espressioni che rappresenta una sottoquery che restituisce esattamente una riga e una colonna di un tipo primitivo con una radice dell'oggetto DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="885c5-159">Con un tipo restituito di raccolta, nel qual caso definisce una nuova raccolta delle espressioni specificate come argomenti.</span><span class="sxs-lookup"><span data-stu-id="885c5-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="885c5-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="885c5-161">Un oggetto DbVariableReferenceExpression deve essere un elemento figlio del nodo DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="885c5-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-162">DbGroupByExpression</span></span>

<span data-ttu-id="885c5-163">La proprietà Aggregates di un oggetto DbGroupByExpression può presentare solo elementi di tipo DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="885c5-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="885c5-164">Non esistono altri tipi di aggregazione.</span><span class="sxs-lookup"><span data-stu-id="885c5-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="885c5-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-165">DbLimitExpression</span></span>

<span data-ttu-id="885c5-166">La proprietà Limit può essere solo un oggetto DbConstantExpression o DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="885c5-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="885c5-167">Inoltre, la proprietà WithTies è sempre false in .NET Framework 3.5 e versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="885c5-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="885c5-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="885c5-168">DbScanExpression</span></span>

<span data-ttu-id="885c5-169">Quando viene usato negli alberi dei comandi di output, DbScanExpression rappresenta efficacemente un'analisi su una tabella, una vista o una query di archiviazione, rappresentata da EntitySetBase:: target.</span><span class="sxs-lookup"><span data-stu-id="885c5-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="885c5-170">Se la proprietà dei metadati "Defineing query" della destinazione è diversa da null, rappresenta una query, il testo della query per il quale viene fornito nella proprietà dei metadati nel linguaggio o nel dialetto specifico del provider, come specificato nella definizione dello schema dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="885c5-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="885c5-171">In caso contrario, la destinazione rappresenta una tabella o una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="885c5-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="885c5-172">Il prefisso dello schema si trova nella proprietà dei metadati "schema", se non è null; in caso contrario, è il nome del contenitore di entità.</span><span class="sxs-lookup"><span data-stu-id="885c5-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="885c5-173">Il nome della tabella o della vista è la proprietà dei metadati "Table", se non è null; in caso contrario, la proprietà Name della base del set di entità.</span><span class="sxs-lookup"><span data-stu-id="885c5-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="885c5-174">Tutte queste proprietà hanno origine dalla definizione dell'EntitySet corrispondente nel file SSDL (Store Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="885c5-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="885c5-175">Utilizzo dei tipi primitivi</span><span class="sxs-lookup"><span data-stu-id="885c5-175">Using Primitive Types</span></span>

<span data-ttu-id="885c5-176">Quando si fa riferimento ai tipi primitivi negli alberi dei comandi di output, in genere il riferimento è contenuto nei tipi primitivi del modello concettuale.</span><span class="sxs-lookup"><span data-stu-id="885c5-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="885c5-177">Per determinate espressioni, tuttavia, i, provider richiedono il tipo primitivo dell'archivio corrispondente.</span><span class="sxs-lookup"><span data-stu-id="885c5-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="885c5-178">Esempi di tali espressioni includono DbCastExpression e in alcuni casi DbNullExpression, se il provider deve eseguire il cast del valore null al tipo corrispondente.</span><span class="sxs-lookup"><span data-stu-id="885c5-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="885c5-179">In questi casi, i provider devono eseguire il mapping al tipo di provider in base al tipo primitivo e ai relativi facet.</span><span class="sxs-lookup"><span data-stu-id="885c5-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="885c5-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="885c5-180">See also</span></span>

- [<span data-ttu-id="885c5-181">Generazione SQL</span><span class="sxs-lookup"><span data-stu-id="885c5-181">SQL Generation</span></span>](sql-generation.md)
