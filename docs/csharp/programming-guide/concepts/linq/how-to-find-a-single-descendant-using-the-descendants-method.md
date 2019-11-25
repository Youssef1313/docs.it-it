---
title: Come trovare un singolo discendente con il metodo Descendants (C#)
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 59d8cfb93ec527a6ceaa58b422a154e16d712533
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141194"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="81783-102">Come trovare un singolo discendente con il metodo Descendants (C#)</span><span class="sxs-lookup"><span data-stu-id="81783-102">How to find a single descendant using the descendants method (C#)</span></span>
<span data-ttu-id="81783-103">È possibile usare il metodo <xref:System.Xml.Linq.XContainer.Descendants%2A> dell'asse per scrivere rapidamente codice per trovare un singolo elemento con un nome univoco.</span><span class="sxs-lookup"><span data-stu-id="81783-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="81783-104">Questa tecnica è particolarmente utile quando si desidera trovare un particolare discendente con un nome specifico.</span><span class="sxs-lookup"><span data-stu-id="81783-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="81783-105">È possibile scrivere il codice per spostarsi fino all'elemento desiderato, ma risulta in genere più veloce e semplice scrivere il codice usando l'asse <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="81783-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81783-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="81783-106">Example</span></span>  
 <span data-ttu-id="81783-107">In questo esempio viene usato l'operatore di query standard <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="81783-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="81783-108">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="81783-108">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="81783-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="81783-109">Example</span></span>  
 <span data-ttu-id="81783-110">Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="81783-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="81783-111">Per altre informazioni, vedere [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="81783-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="81783-112">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="81783-112">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
