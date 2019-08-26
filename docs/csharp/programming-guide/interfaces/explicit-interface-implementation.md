---
title: Implementazione esplicita dell'interfaccia - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589226"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="6542a-102">Implementazione esplicita dell'interfaccia (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="6542a-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="6542a-103">Se [class](../../language-reference/keywords/class.md) implementa due interfacce che contengono un membro con la stessa firma e quest'ultimo viene implementato nella classe, entrambe le interfacce useranno il membro come propria implementazione.</span><span class="sxs-lookup"><span data-stu-id="6542a-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="6542a-104">Nell'esempio seguente tutte le chiamate a `Paint` richiamano lo stesso metodo.</span><span class="sxs-lookup"><span data-stu-id="6542a-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="6542a-105">Se tuttavia i due membri di [interface](../../language-reference/keywords/interface.md) non eseguono la stessa funzione, l'implementazione di una o di entrambe le interfacce potrebbe non risultare corretta.</span><span class="sxs-lookup"><span data-stu-id="6542a-105">If the two [interface](../../language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="6542a-106">È possibile implementare un membro di interfaccia in modo esplicito, ovvero creando un membro di classe che viene chiamato solo tramite l'interfaccia e che è specifico di tale interfaccia.</span><span class="sxs-lookup"><span data-stu-id="6542a-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="6542a-107">Per questa operazione è necessario assegnare al membro di classe il nome dell'interfaccia seguito da un punto.</span><span class="sxs-lookup"><span data-stu-id="6542a-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="6542a-108">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6542a-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="6542a-109">Il membro di classe `IControl.Paint` è disponibile solo tramite l'interfaccia`IControl` e `ISurface.Paint` è disponibile solo tramite `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="6542a-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="6542a-110">Entrambe le implementazioni del metodo sono separate e nessuna delle due è disponibile direttamente nella classe.</span><span class="sxs-lookup"><span data-stu-id="6542a-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="6542a-111">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6542a-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="6542a-112">L'implementazione esplicita viene usata anche per risolvere i casi in cui due interfacce dichiarano ognuna membri diversi con lo stesso nome, ad esempio una proprietà e un metodo:</span><span class="sxs-lookup"><span data-stu-id="6542a-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="6542a-113">Per implementare entrambe le interfacce, una classe deve usare l'implementazione esplicita per la proprietà P o il metodo P oppure per entrambi, in modo da evitare un errore del compilatore.</span><span class="sxs-lookup"><span data-stu-id="6542a-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="6542a-114">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6542a-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="6542a-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6542a-115">See also</span></span>

- [<span data-ttu-id="6542a-116">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="6542a-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6542a-117">Classi e struct</span><span class="sxs-lookup"><span data-stu-id="6542a-117">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="6542a-118">Interfacce</span><span class="sxs-lookup"><span data-stu-id="6542a-118">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="6542a-119">Ereditarietà</span><span class="sxs-lookup"><span data-stu-id="6542a-119">Inheritance</span></span>](../classes-and-structs/inheritance.md)
