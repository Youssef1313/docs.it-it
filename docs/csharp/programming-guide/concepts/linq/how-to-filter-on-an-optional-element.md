---
title: 'Procedura: Filtrare in base a un elemento facoltativo (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 403c331787df7eb538302df2ecc332a663e68d71
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593792"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="953d7-102">Procedura: Filtrare in base a un elemento facoltativo (C#)</span><span class="sxs-lookup"><span data-stu-id="953d7-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="953d7-103">Talvolta si desidera filtrare in base a un elemento anche se non si è certi che esista nel documento XML.</span><span class="sxs-lookup"><span data-stu-id="953d7-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="953d7-104">La ricerca deve essere eseguita in modo che se l'elemento specifico non include l'elemento figlio, non viene generata un'eccezione di riferimento null quando si applica un filtro sull'elemento.</span><span class="sxs-lookup"><span data-stu-id="953d7-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="953d7-105">Nell'esempio seguente l'elemento `Child5` non contiene un elemento figlio `Type`, tuttavia la query viene comunque eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="953d7-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="953d7-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="953d7-106">Example</span></span>  
 <span data-ttu-id="953d7-107">In questo esempio viene usato il metodo di estensione <xref:System.Xml.Linq.Extensions.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="953d7-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="953d7-108">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="953d7-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="953d7-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="953d7-109">Example</span></span>  
 <span data-ttu-id="953d7-110">Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="953d7-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="953d7-111">Per altre informazioni, vedere [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="953d7-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="953d7-112">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="953d7-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="953d7-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="953d7-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="953d7-114">Panoramica degli operatori di query standard (C#)</span><span class="sxs-lookup"><span data-stu-id="953d7-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="953d7-115">Operazioni di proiezione (C#)</span><span class="sxs-lookup"><span data-stu-id="953d7-115">Projection Operations (C#)</span></span>](./projection-operations.md)
