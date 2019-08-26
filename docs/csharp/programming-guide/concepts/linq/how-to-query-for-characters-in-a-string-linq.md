---
title: 'Procedura: Eseguire una query per trovare caratteri in una stringa (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 1212ebcf264aab756eca1acb81ae617c2218a065
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592884"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="01e90-102">Procedura: Eseguire una query per trovare caratteri in una stringa (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="01e90-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="01e90-103">Poiché la classe <xref:System.String> implementa l'interfaccia generica <xref:System.Collections.Generic.IEnumerable%601>, è possibile eseguire una query su qualsiasi stringa come una sequenza di caratteri.</span><span class="sxs-lookup"><span data-stu-id="01e90-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="01e90-104">Tuttavia, questo uso di LINQ non è comune.</span><span class="sxs-lookup"><span data-stu-id="01e90-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="01e90-105">Per le operazioni con criteri di ricerca complessi, usare la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="01e90-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01e90-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="01e90-106">Example</span></span>  
 <span data-ttu-id="01e90-107">Nell'esempio seguente viene eseguita una query su una stringa per determinare il numero di cifre che contiene.</span><span class="sxs-lookup"><span data-stu-id="01e90-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="01e90-108">Si noti che, dopo la prima esecuzione, la query viene "riutilizzata".</span><span class="sxs-lookup"><span data-stu-id="01e90-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="01e90-109">Ciò è possibile perché la query stessa non archivia i risultati effettivi.</span><span class="sxs-lookup"><span data-stu-id="01e90-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="01e90-110">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="01e90-110">Compiling the Code</span></span>  
 <span data-ttu-id="01e90-111">Creare un progetto di applicazione console C# con direttive `using` per gli spazi dei nomi System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="01e90-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e90-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="01e90-112">See also</span></span>

- [<span data-ttu-id="01e90-113">LINQ e stringhe (C#)</span><span class="sxs-lookup"><span data-stu-id="01e90-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="01e90-114">Procedura: Combinare query LINQ con espressioni regolari (C#)</span><span class="sxs-lookup"><span data-stu-id="01e90-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
