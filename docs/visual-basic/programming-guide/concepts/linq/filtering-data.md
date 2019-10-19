---
title: Filtraggio dei dati (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 27765247daa2155e685b1cd2bfccebb3216ca672
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582441"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="18f00-102">Filtraggio dei dati (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f00-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="18f00-103">Il filtro si riferisce all'operazione in base alla quale il set di risultati viene limitato in modo da contenere solo gli elementi che corrispondono a una condizione specificata.</span><span class="sxs-lookup"><span data-stu-id="18f00-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="18f00-104">È anche noto come selezione.</span><span class="sxs-lookup"><span data-stu-id="18f00-104">It is also known as selection.</span></span>

<span data-ttu-id="18f00-105">Nella figura seguente vengono illustrati i risultati del filtro di una sequenza di caratteri.</span><span class="sxs-lookup"><span data-stu-id="18f00-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="18f00-106">Il predicato per l'operazione di filtro specifica che il carattere deve essere 'A'.</span><span class="sxs-lookup"><span data-stu-id="18f00-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagramma che illustra un'operazione di filtro LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="18f00-108">La sezione seguente elenca i metodi dell'operatore query standard che esegue la selezione.</span><span class="sxs-lookup"><span data-stu-id="18f00-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="18f00-109">Metodi</span><span class="sxs-lookup"><span data-stu-id="18f00-109">Methods</span></span>

|<span data-ttu-id="18f00-110">Nome metodo</span><span class="sxs-lookup"><span data-stu-id="18f00-110">Method Name</span></span>|<span data-ttu-id="18f00-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="18f00-111">Description</span></span>|<span data-ttu-id="18f00-112">Visual Basic sintassi delle espressioni di query</span><span class="sxs-lookup"><span data-stu-id="18f00-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="18f00-113">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="18f00-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="18f00-114">OfType</span><span class="sxs-lookup"><span data-stu-id="18f00-114">OfType</span></span>|<span data-ttu-id="18f00-115">Seleziona i valori, a seconda della loro capacità di eseguire il cast a un tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="18f00-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="18f00-116">Non applicabile.</span><span class="sxs-lookup"><span data-stu-id="18f00-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="18f00-117">Dove</span><span class="sxs-lookup"><span data-stu-id="18f00-117">Where</span></span>|<span data-ttu-id="18f00-118">Seleziona i valori che si basano su una funzione di predicato.</span><span class="sxs-lookup"><span data-stu-id="18f00-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="18f00-119">Esempi di sintassi delle espressioni di query</span><span class="sxs-lookup"><span data-stu-id="18f00-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="18f00-120">Nell'esempio seguente viene usato il `Where` per filtrare da una matrice le stringhe con una lunghezza specifica.</span><span class="sxs-lookup"><span data-stu-id="18f00-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="18f00-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="18f00-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="18f00-122">Panoramica degli operatori query standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f00-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="18f00-123">Clausola Where</span><span class="sxs-lookup"><span data-stu-id="18f00-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="18f00-124">Procedura: Filtrare i risultati di una query</span><span class="sxs-lookup"><span data-stu-id="18f00-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="18f00-125">Procedura: eseguire una query sui metadati di un assembly tramite reflection (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f00-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="18f00-126">Procedura: eseguire una query per i file con un nome o un attributo specificato (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f00-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="18f00-127">Procedura: ordinare o filtrare i dati di testo in base a qualsiasi parola o campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f00-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
