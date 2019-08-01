---
title: Utilizzo di spazi dei nomi globali (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710375"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="85a84-102">Utilizzo di spazi dei nomi globali (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="85a84-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="85a84-103">Una delle funzionalità chiave dei valori letterali XML in Visual Basic è la possibilità di dichiarare gli spazi dei nomi XML utilizzando `Imports` l'istruzione.</span><span class="sxs-lookup"><span data-stu-id="85a84-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="85a84-104">Tramite questa funzionalità, è possibile dichiarare uno spazio dei nomi XML che usa un prefisso oppure uno spazio dei nomi XML predefinito.</span><span class="sxs-lookup"><span data-stu-id="85a84-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="85a84-105">Questa funzionalità risulta utile in due situazioni.</span><span class="sxs-lookup"><span data-stu-id="85a84-105">This capability is useful in two situations.</span></span> <span data-ttu-id="85a84-106">Innanzitutto gli spazi dei nomi dichiarati in valori letterali XML non vengono trasferiti nelle espressioni incorporate.</span><span class="sxs-lookup"><span data-stu-id="85a84-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="85a84-107">La dichiarazione di spazi dei nomi globali riduce il numero di operazioni che è necessario eseguire per usare le espressioni incorporate con gli spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="85a84-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="85a84-108">In secondo luogo, è necessario dichiarare spazi dei nomi globali al fine di usare gli spazi dei nomi con le proprietà XML.</span><span class="sxs-lookup"><span data-stu-id="85a84-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="85a84-109">È possibile dichiarare spazi dei nomi globali a livello di progetto</span><span class="sxs-lookup"><span data-stu-id="85a84-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="85a84-110">oppure a livello di modulo. In quest'ultimo caso gli spazi dei nomi eseguono l'override di quelli a livello di progetto.</span><span class="sxs-lookup"><span data-stu-id="85a84-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="85a84-111">Infine è possibile eseguire l'override degli spazi dei nomi globali in un valore letterale XML.</span><span class="sxs-lookup"><span data-stu-id="85a84-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="85a84-112">Quando si usano i valori letterali o le proprietà XML incluse negli spazi dei nomi dichiarati a livello globale, è possibile visualizzare il nome espanso dei valori letterali o delle proprietà XML passandovi sopra con il mouse in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85a84-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="85a84-113">Il nome espanso verrà visualizzato in una descrizione comandi.</span><span class="sxs-lookup"><span data-stu-id="85a84-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="85a84-114">È possibile ottenere un oggetto <xref:System.Xml.Linq.XNamespace> che corrisponde a uno spazio dei nomi globale usando il metodo `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="85a84-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="85a84-115">Esempi di spazi dei nomi globali</span><span class="sxs-lookup"><span data-stu-id="85a84-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="85a84-116">Nell'esempio seguente viene dichiarato uno spazio dei nomi globale predefinito usando l'istruzione `Imports`, quindi viene usato un valore letterale XML per inizializzare un oggetto <xref:System.Xml.Linq.XElement> in tale spazio dei nomi:</span><span class="sxs-lookup"><span data-stu-id="85a84-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="85a84-117">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="85a84-118">Nell'esempio seguente viene dichiarato uno spazio dei nomi globale con un prefisso, quindi viene usato un valore letterale XML per inizializzare un elemento:</span><span class="sxs-lookup"><span data-stu-id="85a84-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="85a84-119">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="85a84-120">Spazi dei nomi globali ed espressioni incorporate</span><span class="sxs-lookup"><span data-stu-id="85a84-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="85a84-121">Gli spazi dei nomi dichiarati in valori letterali XML non vengono trasferiti nelle espressioni incorporate.</span><span class="sxs-lookup"><span data-stu-id="85a84-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="85a84-122">Nell'esempio seguente viene dichiarato uno spazio dei nomi predefinito.</span><span class="sxs-lookup"><span data-stu-id="85a84-122">The following example declares a default namespace.</span></span> <span data-ttu-id="85a84-123">Viene quindi usata un'espressione incorporata per l'elemento `Child`.</span><span class="sxs-lookup"><span data-stu-id="85a84-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="85a84-124">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="85a84-125">Si noti che l'XML risultante include una dichiarazione di uno spazio dei nomi predefinito, per cui l'elemento `Child` non è incluso in alcuno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="85a84-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="85a84-126">È possibile ridichiarare lo spazio dei nomi nell'espressione incorporata, come segue:</span><span class="sxs-lookup"><span data-stu-id="85a84-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="85a84-127">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="85a84-128">Questa operazione è, tuttavia, piuttosto complessa. Un approccio più efficace è costituito dall'utilizzo dello spazio dei nomi predefinito globale,</span><span class="sxs-lookup"><span data-stu-id="85a84-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="85a84-129">che consente di usare valori letterali XML senza dichiarare spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="85a84-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="85a84-130">L'XML risultante si troverà nello spazio dei nomi predefinito dichiarato a livello globale.</span><span class="sxs-lookup"><span data-stu-id="85a84-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="85a84-131">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="85a84-132">Utilizzo degli spazi dei nomi con proprietà XML</span><span class="sxs-lookup"><span data-stu-id="85a84-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="85a84-133">Se si usa un albero XML incluso in uno spazio dei nomi e si usano proprietà XML, è necessario usare uno spazio dei nomi globale in modi che anche le proprietà XML saranno incluse nello spazio dei nomi corretto.</span><span class="sxs-lookup"><span data-stu-id="85a84-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="85a84-134">Nell'esempio seguente viene dichiarato un albero XML in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="85a84-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="85a84-135">Viene quindi stampato il conteggio degli elementi `Child`.</span><span class="sxs-lookup"><span data-stu-id="85a84-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="85a84-136">L'esempio indica che non sono presenti elementi `Child`.</span><span class="sxs-lookup"><span data-stu-id="85a84-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="85a84-137">L'output è il seguente:</span><span class="sxs-lookup"><span data-stu-id="85a84-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="85a84-138">Se tuttavia viene dichiarato uno spazio dei nomi globale predefinito, sia i valori letterali XML che la proprietà XML si trovano nello spazio dei nomi globale predefinito:</span><span class="sxs-lookup"><span data-stu-id="85a84-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="85a84-139">L'esempio indica che è presente un unico elemento `Child`.</span><span class="sxs-lookup"><span data-stu-id="85a84-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="85a84-140">L'output è il seguente:</span><span class="sxs-lookup"><span data-stu-id="85a84-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="85a84-141">Se si dichiara uno spazio dei nomi globale che ha un prefisso, è possibile usare il prefisso per i valori letterali e le proprietà XML:</span><span class="sxs-lookup"><span data-stu-id="85a84-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="85a84-142">XNamespace e spazi dei nomi globali</span><span class="sxs-lookup"><span data-stu-id="85a84-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="85a84-143">È possibile ottenere un oggetto <xref:System.Xml.Linq.XNamespace> usando il metodo `GetXmlNamespace`:</span><span class="sxs-lookup"><span data-stu-id="85a84-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="85a84-144">Questo esempio produce il seguente output:</span><span class="sxs-lookup"><span data-stu-id="85a84-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="85a84-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="85a84-145">See also</span></span>

- [<span data-ttu-id="85a84-146">Panoramica degli spazi dei nomi (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85a84-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
