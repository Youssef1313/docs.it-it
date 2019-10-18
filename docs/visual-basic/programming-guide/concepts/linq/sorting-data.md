---
title: Ordinamento dei dati (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f8b1734597efa3134c95c9764bad7f79fd3cf1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524074"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="ef96a-102">Ordinamento dei dati (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef96a-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="ef96a-103">Un'operazione di ordinamento consente di ordinare gli elementi di una sequenza in base a uno o più attributi.</span><span class="sxs-lookup"><span data-stu-id="ef96a-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="ef96a-104">Il primo criterio di ordinamento consente di applicare un ordinamento principale agli elementi.</span><span class="sxs-lookup"><span data-stu-id="ef96a-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="ef96a-105">Specificando un secondo criterio di ordinamento, è possibile ordinare gli elementi all'interno di ogni gruppo di ordinamento principale.</span><span class="sxs-lookup"><span data-stu-id="ef96a-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="ef96a-106">La figura seguente illustra i risultati di un'operazione di ordinamento alfabetico in una sequenza di caratteri.</span><span class="sxs-lookup"><span data-stu-id="ef96a-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Immagine che illustra un'operazione di ordinamento alfabetico.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="ef96a-108">La sezione seguente elenca i metodi dell'operatore query standard che ordina i dati.</span><span class="sxs-lookup"><span data-stu-id="ef96a-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="ef96a-109">Metodi</span><span class="sxs-lookup"><span data-stu-id="ef96a-109">Methods</span></span>

|<span data-ttu-id="ef96a-110">Nome metodo</span><span class="sxs-lookup"><span data-stu-id="ef96a-110">Method Name</span></span>|<span data-ttu-id="ef96a-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ef96a-111">Description</span></span>|<span data-ttu-id="ef96a-112">Visual Basic sintassi delle espressioni di query</span><span class="sxs-lookup"><span data-stu-id="ef96a-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ef96a-113">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="ef96a-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="ef96a-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ef96a-114">OrderBy</span></span>|<span data-ttu-id="ef96a-115">Ordina i valori in ordine crescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ef96a-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="ef96a-116">OrderByDescending</span></span>|<span data-ttu-id="ef96a-117">Ordina i valori in ordine decrescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ef96a-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ef96a-118">ThenBy</span></span>|<span data-ttu-id="ef96a-119">Esegue un ordinamento secondario crescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ef96a-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="ef96a-120">ThenByDescending</span></span>|<span data-ttu-id="ef96a-121">Esegue un ordinamento secondario decrescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ef96a-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="ef96a-122">Reverse</span></span>|<span data-ttu-id="ef96a-123">Inverte l'ordine degli elementi in una Collection.</span><span class="sxs-lookup"><span data-stu-id="ef96a-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="ef96a-124">Non applicabile.</span><span class="sxs-lookup"><span data-stu-id="ef96a-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ef96a-125">Esempi di sintassi delle espressioni di query</span><span class="sxs-lookup"><span data-stu-id="ef96a-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="ef96a-126">Esempi di ordinamento primario</span><span class="sxs-lookup"><span data-stu-id="ef96a-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="ef96a-127">Ordinamento primario crescente</span><span class="sxs-lookup"><span data-stu-id="ef96a-127">Primary Ascending Sort</span></span>

<span data-ttu-id="ef96a-128">Nell'esempio seguente viene illustrato come usare la clausola `Order By` in una query LINQ per ordinare le stringhe in una matrice in base alla lunghezza di stringa, in ordine crescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a><span data-ttu-id="ef96a-129">Ordinamento primario decrescente</span><span class="sxs-lookup"><span data-stu-id="ef96a-129">Primary Descending Sort</span></span>

<span data-ttu-id="ef96a-130">Nell'esempio seguente viene illustrato come usare la clausola `Order By Descending` in una query LINQ per ordinare le stringhe in base alla prima lettera, in ordine decrescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a><span data-ttu-id="ef96a-131">Esempi di ordinamento secondario</span><span class="sxs-lookup"><span data-stu-id="ef96a-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="ef96a-132">Ordinamento secondario crescente</span><span class="sxs-lookup"><span data-stu-id="ef96a-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="ef96a-133">Nell'esempio seguente viene illustrato come usare la clausola `Order By` in una query LINQ per eseguire un ordinamento primario e secondario delle stringhe in una matrice.</span><span class="sxs-lookup"><span data-stu-id="ef96a-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="ef96a-134">Le stringhe vengono ordinate prima in base alla lunghezza e poi in base alla prima lettera della stringa, in ordine crescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a><span data-ttu-id="ef96a-135">Ordinamento secondario in ordine decrescente</span><span class="sxs-lookup"><span data-stu-id="ef96a-135">Secondary Descending Sort</span></span>

<span data-ttu-id="ef96a-136">L'esempio seguente illustra come usare la clausola `Order By Descending` in una query LINQ per eseguire un ordinamento primario, in ordine crescente, e un ordinamento secondario, in ordine decrescente.</span><span class="sxs-lookup"><span data-stu-id="ef96a-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="ef96a-137">Le stringhe vengono ordinate principalmente in base alla lunghezza e poi in base alla prima lettera della stringa.</span><span class="sxs-lookup"><span data-stu-id="ef96a-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a><span data-ttu-id="ef96a-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ef96a-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ef96a-139">Panoramica degli operatori query standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef96a-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ef96a-140">Clausola Order By</span><span class="sxs-lookup"><span data-stu-id="ef96a-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ef96a-141">Procedura: Ordinare i risultati di query</span><span class="sxs-lookup"><span data-stu-id="ef96a-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="ef96a-142">Procedura: ordinare o filtrare i dati di testo in base a qualsiasi parola o campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef96a-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
