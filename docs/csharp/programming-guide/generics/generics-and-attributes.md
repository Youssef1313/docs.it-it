---
title: Generics e attributi - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589633"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="43e58-102">Generics e attributi (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="43e58-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="43e58-103">Gli attributi possono essere applicati a tipi generici allo stesso modo che ai tipi non generici.</span><span class="sxs-lookup"><span data-stu-id="43e58-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="43e58-104">Per altre informazioni sull'applicazione di attributi, vedere [Attributi](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="43e58-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="43e58-105">Gli attributi personalizzati sono consentiti solo per fare riferimento a tipi generici aperti, che sono tipi generici per cui non è specificato alcun argomento tipo, e tipi generici costruiti chiusi, che specificano argomenti per tutti i parametri di tipo.</span><span class="sxs-lookup"><span data-stu-id="43e58-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="43e58-106">Gli esempi seguenti usano questo attributo personalizzato:</span><span class="sxs-lookup"><span data-stu-id="43e58-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="43e58-107">Un attributo può fare riferimento a un tipo generico aperto:</span><span class="sxs-lookup"><span data-stu-id="43e58-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="43e58-108">Specificare più parametri di tipo usando il numero appropriato di virgole.</span><span class="sxs-lookup"><span data-stu-id="43e58-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="43e58-109">In questo esempio `GenericClass2` include due parametri di tipo:</span><span class="sxs-lookup"><span data-stu-id="43e58-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="43e58-110">Un attributo può fare riferimento a un tipo generico costruito chiuso:</span><span class="sxs-lookup"><span data-stu-id="43e58-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="43e58-111">Un attributo che fa riferimento a un parametro di tipo generico provoca un errore in fase di compilazione:</span><span class="sxs-lookup"><span data-stu-id="43e58-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="43e58-112">Un tipo generico non può ereditare da <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="43e58-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="43e58-113">Per ottenere informazioni su un tipo generico o un parametro di tipo in fase di esecuzione, è possibile usare i metodi di <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="43e58-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="43e58-114">Per altre informazioni, vedere [Generics e reflection](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="43e58-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e58-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43e58-115">See also</span></span>

- [<span data-ttu-id="43e58-116">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="43e58-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="43e58-117">Generics</span><span class="sxs-lookup"><span data-stu-id="43e58-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="43e58-118">Attributi</span><span class="sxs-lookup"><span data-stu-id="43e58-118">Attributes</span></span>](../../../standard/attributes/index.md)
