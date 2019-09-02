---
title: Concatenamento di operatori di query standard (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204213"
---
# <a name="chaining-standard-query-operators-together-c"></a>Concatenamento di operatori di query standard (C#)
Questo è l'argomento finale nell'[Esercitazione: Concatenamento di query (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 È anche possibile concatenare gli operatori di query standard. Ad esempio, è possibile inserire l'operatore <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> che opera anch'esso in modo lazy. Questo operatore non materializza nessun risultato intermedio.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene chiamato il metodo <xref:System.Linq.Enumerable.Where%2A> prima della chiamata a `ConvertCollectionToUpperCase`. Il metodo <xref:System.Linq.Enumerable.Where%2A> opera quasi esattamente allo stesso modo dei metodi lazy usati negli esempi precedenti di questa esercitazione, ovvero `ConvertCollectionToUpperCase` e `AppendString`.  
  
 La differenza è che in questo caso il metodo <xref:System.Linq.Enumerable.Where%2A> scorre la raccolta di origine, determina che il primo elemento non passa il predicato, quindi ottiene l'elemento successivo, che invece passa. Infine restituisce il secondo elemento.  
  
 Tuttavia, l'idea di base è la stessa: le raccolte intermedie vengono materializzate solo se è necessario.  
  
 Quando si usano le espressioni di query, vengono convertite in chiamate agli operatori di query standard e si applicano gli stessi principi.  
  
 Tutti gli esempi di questa sezione in cui vengono eseguite query su documenti Office Open XML si basano sullo stesso principio. Le idee di esecuzione posticipata e valutazione lazy sono alcuni dei concetti fondamentali che è necessario comprendere per usare LINQ e LINQ to XML in modo efficace.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Questo esempio produce il seguente output:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
