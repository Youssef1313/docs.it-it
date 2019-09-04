---
title: Costruzione di tipi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 7113aaf1c2caa982a8ab4751928856c1271570cb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251113"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="83b66-102">Costruzione di tipi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="83b66-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="83b66-103">in sono disponibili tre tipi di costruttori, ovvero costruttori di riga, costruttori di tipi denominati e costruttori di raccolte.</span><span class="sxs-lookup"><span data-stu-id="83b66-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="83b66-104">Costruttori di riga</span><span class="sxs-lookup"><span data-stu-id="83b66-104">Row Constructors</span></span>  
 <span data-ttu-id="83b66-105">I costruttori di riga vengono usati in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per costruire record anonimi e con strutture tipizzate da uno o più valori.</span><span class="sxs-lookup"><span data-stu-id="83b66-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="83b66-106">Il tipo di risultato di un costruttore di riga è un tipo di riga i cui tipi di campo corrispondono ai tipi dei valori usati per costruire la riga.</span><span class="sxs-lookup"><span data-stu-id="83b66-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="83b66-107">L'espressione seguente, ad esempio, costruisce un valore di `Record(a int, b string, c int)`tipo:</span><span class="sxs-lookup"><span data-stu-id="83b66-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="83b66-108">Se non si fornisce un alias per un'espressione in un costruttore di riga, in Entity Framework viene eseguito un tentativo di generarne uno.</span><span class="sxs-lookup"><span data-stu-id="83b66-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="83b66-109">Per ulteriori informazioni, vedere la sezione "regole di aliasing" in [identificatori](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="83b66-109">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="83b66-110">Le regole seguenti riguardano l'uso di alias nelle espressioni in un costruttore di riga:</span><span class="sxs-lookup"><span data-stu-id="83b66-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="83b66-111">Le espressioni in un costruttore ROW non possono fare riferimento ad altri alias nello stesso costruttore.</span><span class="sxs-lookup"><span data-stu-id="83b66-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="83b66-112">Due espressioni nello stesso costruttore di riga non possono avere lo stesso alias.</span><span class="sxs-lookup"><span data-stu-id="83b66-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="83b66-113">Per ulteriori informazioni sui costruttori di riga, vedere [Row](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="83b66-113">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="83b66-114">Costruttori di raccolte</span><span class="sxs-lookup"><span data-stu-id="83b66-114">Collection Constructors</span></span>  
 <span data-ttu-id="83b66-115">I costruttori di raccolte vengono usati in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per creare un'istanza di un multiset da un elenco di valori.</span><span class="sxs-lookup"><span data-stu-id="83b66-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="83b66-116">Tutti i valori nel costruttore devono essere di tipo `T` reciprocamente compatibile e il costruttore produce una raccolta di tipo `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="83b66-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="83b66-117">L'espressione seguente consente ad esempio di creare una raccolta di valori interi:</span><span class="sxs-lookup"><span data-stu-id="83b66-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="83b66-118">I costruttori multiset vuoti non sono supportati perché non è possibile determinare il tipo degli elementi.</span><span class="sxs-lookup"><span data-stu-id="83b66-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="83b66-119">Il codice seguente non è valido:</span><span class="sxs-lookup"><span data-stu-id="83b66-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="83b66-120">Per ulteriori informazioni, vedere [multiset](multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="83b66-120">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="83b66-121">Costruttori di tipi denominati (inizializzatori NamedType)</span><span class="sxs-lookup"><span data-stu-id="83b66-121">Named Type Constructors (NamedType Initializers)</span></span>  
 <span data-ttu-id="83b66-122">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i costruttori di tipi (inizializzatori) possono creare istanze di tipi di entità e di tipi complessi denominati.</span><span class="sxs-lookup"><span data-stu-id="83b66-122">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="83b66-123">L'espressione seguente consente ad esempio di creare un'istanza di un tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="83b66-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="83b66-124">L'espressione seguente consente di creare un'istanza di un tipo complesso.</span><span class="sxs-lookup"><span data-stu-id="83b66-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="83b66-125">L'espressione seguente consente di creare un'istanza di un tipo complesso annidato.</span><span class="sxs-lookup"><span data-stu-id="83b66-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="83b66-126">L'espressione seguente consente di creare un'istanza di un'entità con un tipo complesso annidato.</span><span class="sxs-lookup"><span data-stu-id="83b66-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="83b66-127">Nell'esempio seguente viene illustrato come inizializzare una proprietà di un tipo complesso impostandola su Null.</span><span class="sxs-lookup"><span data-stu-id="83b66-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="83b66-128">Si suppone che gli argomenti del costruttore si trovino nello stesso ordine della dichiarazione degli attributi del tipo.</span><span class="sxs-lookup"><span data-stu-id="83b66-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="83b66-129">Per altre informazioni, vedere [costruttore di tipi denominati](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="83b66-129">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b66-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="83b66-130">See also</span></span>

- [<span data-ttu-id="83b66-131">Riferimento a Entity SQL</span><span class="sxs-lookup"><span data-stu-id="83b66-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="83b66-132">Panoramica di Entity SQL</span><span class="sxs-lookup"><span data-stu-id="83b66-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="83b66-133">Sistema di tipi</span><span class="sxs-lookup"><span data-stu-id="83b66-133">Type System</span></span>](type-system-entity-sql.md)
