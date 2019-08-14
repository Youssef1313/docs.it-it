---
title: 'Procedura: Trovare discendenti con un nome di elemento specifico (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: dbb955697e4d4b0ed5aad9c00c37e73bbd32b7b4
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709944"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="8e21c-102">Procedura: Trovare discendenti con un nome di elemento specifico (C#)</span><span class="sxs-lookup"><span data-stu-id="8e21c-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="8e21c-103">Talvolta si desidera individuare tutti i discendenti con un determinato nome.</span><span class="sxs-lookup"><span data-stu-id="8e21c-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="8e21c-104">È possibile scrivere codice per scorrere tutti i discendenti, tuttavia è più agevole usare l'asse <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e21c-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e21c-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e21c-105">Example</span></span>  
 <span data-ttu-id="8e21c-106">Nell'esempio seguente è illustrato come individuare discendenti in base al nome dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="8e21c-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="8e21c-107">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="8e21c-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="8e21c-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="8e21c-108">Example</span></span>  
 <span data-ttu-id="8e21c-109">Nell'esempio seguente è illustrata la stessa query per XML in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="8e21c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8e21c-110">Per altre informazioni, vedere [Panoramica degli spazi dei nomi (LINQ to XML)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8e21c-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="8e21c-111">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="8e21c-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e21c-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8e21c-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
