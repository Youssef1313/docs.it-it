---
title: Esempio di esecuzione posticipata (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: e0bb7f3d125cc48607a534e2c24cbf7083353945
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583327"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="1904e-102">Esempio di esecuzione posticipata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1904e-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="1904e-103">In questo argomento vengono illustrati gli effetti dell'esecuzione posticipata e della valutazione lazy sulle query LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="1904e-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="1904e-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="1904e-104">Example</span></span>

<span data-ttu-id="1904e-105">Nell'esempio seguente è illustrato l'ordine di esecuzione quando si usa un metodo di estensione basato su esecuzione posticipata.</span><span class="sxs-lookup"><span data-stu-id="1904e-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="1904e-106">Viene dichiarata una matrice di tre stringhe.</span><span class="sxs-lookup"><span data-stu-id="1904e-106">The example declares an array of three strings.</span></span> <span data-ttu-id="1904e-107">Viene quindi scorsa la raccolta restituita da `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="1904e-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="1904e-108">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="1904e-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="1904e-109">Si noti che quando si scorre la raccolta restituita da `ConvertCollectionToUpperCase`, ogni elemento viene recuperato dalla matrice di stringhe di origine e viene convertito in lettere maiuscole prima del recupero dell'elemento successivo.</span><span class="sxs-lookup"><span data-stu-id="1904e-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="1904e-110">L'intera matrice di stringhe non viene convertita in lettere maiuscole prima dell'elaborazione nel ciclo `foreach` di `Main` di ogni elemento della raccolta restituita.</span><span class="sxs-lookup"><span data-stu-id="1904e-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1904e-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1904e-111">See also</span></span>

- [<span data-ttu-id="1904e-112">Esercitazione: esecuzione posticipata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1904e-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
