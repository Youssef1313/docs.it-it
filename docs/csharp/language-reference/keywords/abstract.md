---
title: abstract - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 3a4d29ae4814ccceb7b405d9c1749150059a24a0
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859587"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="32013-102">abstract (Riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="32013-102">abstract (C# Reference)</span></span>
<span data-ttu-id="32013-103">Il modificatore `abstract` indica che l'oggetto in fase di modifica ha un'implementazione mancante o incompleta.</span><span class="sxs-lookup"><span data-stu-id="32013-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="32013-104">Il modificatore abstract può essere usato con classi, metodi, proprietà, indicizzatori ed eventi.</span><span class="sxs-lookup"><span data-stu-id="32013-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="32013-105">Usare il modificatore `abstract` in una dichiarazione di classe per indicare che una classe verrà usata solo come classe di base per altre classi e che non verrà creata un'istanza relativamente alla stessa.</span><span class="sxs-lookup"><span data-stu-id="32013-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="32013-106">I membri contrassegnati come astratti devono essere implementati da classi non astratte che derivano dalla classe astratta.</span><span class="sxs-lookup"><span data-stu-id="32013-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="32013-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="32013-107">Example</span></span>  
 <span data-ttu-id="32013-108">In questo esempio, la classe `Square` deve eseguire un'implementazione di `GetArea` poiché deriva da `Shape`:</span><span class="sxs-lookup"><span data-stu-id="32013-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="32013-109">Le classi astratte hanno le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="32013-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="32013-110">Non è possibile creare un'istanza di una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="32013-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="32013-111">Una classe astratta può contenere funzioni di accesso e metodi astratti.</span><span class="sxs-lookup"><span data-stu-id="32013-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="32013-112">Non è possibile modificare una classe astratta con il modificatore [sealed](../../../csharp/language-reference/keywords/sealed.md) perché i due modificatori hanno significati opposti.</span><span class="sxs-lookup"><span data-stu-id="32013-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="32013-113">Il modificatore `sealed` impedisce a una classe che venga ereditata e il modificatore `abstract` richiede una classe da ereditare.</span><span class="sxs-lookup"><span data-stu-id="32013-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="32013-114">Una classe non astratta derivata da una classe astratta deve includere implementazioni effettive di tutte le funzioni di accesso e di tutti i metodi astratti ereditati.</span><span class="sxs-lookup"><span data-stu-id="32013-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="32013-115">Usare il modificatore `abstract` in una dichiarazione di metodo o proprietà per indicare che il metodo o proprietà non contiene implementazioni.</span><span class="sxs-lookup"><span data-stu-id="32013-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="32013-116">I metodi astratti hanno le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="32013-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="32013-117">Un metodo astratto è implicitamente un metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="32013-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="32013-118">Le dichiarazioni di metodi astratti sono consentite solo in classi astratte.</span><span class="sxs-lookup"><span data-stu-id="32013-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="32013-119">Poiché una dichiarazione di un metodo astratto non offre alcuna implementazione effettiva, non c'è nessun corpo del metodo. La dichiarazione del metodo termina semplicemente con un punto e virgola e non ci sono parentesi graffe ({ }) dopo la firma.</span><span class="sxs-lookup"><span data-stu-id="32013-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="32013-120">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="32013-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="32013-121">L'implementazione viene specificata tramite l'[override](../../../csharp/language-reference/keywords/override.md) di un metodo, che è un membro di una classe non astratta.</span><span class="sxs-lookup"><span data-stu-id="32013-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="32013-122">Non è possibile usare il modificatore [static](../../../csharp/language-reference/keywords/static.md) o [virtual](../../../csharp/language-reference/keywords/virtual.md) in una dichiarazione di un metodo astratto.</span><span class="sxs-lookup"><span data-stu-id="32013-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="32013-123">Le proprietà astratte si comportano come i metodi astratti, ad eccezione delle differenze nella sintassi di dichiarazione e di chiamata.</span><span class="sxs-lookup"><span data-stu-id="32013-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="32013-124">Non è possibile usare il modificatore `abstract` su una proprietà static.</span><span class="sxs-lookup"><span data-stu-id="32013-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="32013-125">Una proprietà astratta ereditata può essere sottoposta a override in una classe derivata includendo una dichiarazione di proprietà che usa il modificatore di [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="32013-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="32013-126">Per altre informazioni sulle classi astratte, vedere [Classi e membri delle classi astratte e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="32013-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="32013-127">Una classe astratta deve specificare l'implementazione per tutti i membri di interfaccia.</span><span class="sxs-lookup"><span data-stu-id="32013-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="32013-128">Una classe astratta che implementa un'interfaccia può eseguire il mapping dei metodi di interfaccia su metodi astratti.</span><span class="sxs-lookup"><span data-stu-id="32013-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="32013-129">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="32013-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="32013-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="32013-130">Example</span></span>  
 <span data-ttu-id="32013-131">In questo esempio, la classe `DerivedClass` è derivata da una classe di base astratta `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="32013-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="32013-132">La classe astratta contiene un metodo astratto, `AbstractMethod`, e due proprietà astratte, `X` e `Y`.</span><span class="sxs-lookup"><span data-stu-id="32013-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="32013-133">Nell'esempio precedente, se si prova a creare un'istanza della classe astratta tramite un'istruzione simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="32013-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="32013-134">si ottiene un messaggio di errore che informa che il compilatore non può creare un'istanza della classe astratta "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="32013-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="32013-135">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="32013-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32013-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="32013-136">See also</span></span>

- [<span data-ttu-id="32013-137">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="32013-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="32013-138">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="32013-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="32013-139">Modificatori</span><span class="sxs-lookup"><span data-stu-id="32013-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="32013-140">virtual</span><span class="sxs-lookup"><span data-stu-id="32013-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="32013-141">override</span><span class="sxs-lookup"><span data-stu-id="32013-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="32013-142">Parole chiave di C#</span><span class="sxs-lookup"><span data-stu-id="32013-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
