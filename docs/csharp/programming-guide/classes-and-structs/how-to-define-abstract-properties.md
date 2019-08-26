---
title: 'Procedura: Definire proprietà astratte - Guida per programmatori C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: fae526f5dcd452fbc381ee86c892b72e61956f0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596863"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="e6b15-102">Procedura: Definire proprietà astratte (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="e6b15-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="e6b15-103">L'esempio seguente mostra come definire proprietà di tipo [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="e6b15-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="e6b15-104">La dichiarazione di una proprietà astratta non fornisce un'implementazione delle funzioni di accesso della proprietà. Dichiara che la classe supporta le proprietà, ma l'implementazione delle funzioni di accesso viene demandata alle classi derivate.</span><span class="sxs-lookup"><span data-stu-id="e6b15-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="e6b15-105">L'esempio seguente illustra come implementare le proprietà astratte ereditate da una classe di base.</span><span class="sxs-lookup"><span data-stu-id="e6b15-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="e6b15-106">L'esempio include tre file, ognuno dei quali viene compilato singolarmente e al cui assembly risultante viene fatto riferimento nella compilazione successiva:</span><span class="sxs-lookup"><span data-stu-id="e6b15-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="e6b15-107">abstractshape.cs: classe `Shape` che contiene una proprietà `Area` astratta.</span><span class="sxs-lookup"><span data-stu-id="e6b15-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="e6b15-108">shapes.cs: sottoclassi della classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="e6b15-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="e6b15-109">shapetest.cs: programma di test per la visualizzazione delle aree di alcuni oggetti derivati da `Shape`.</span><span class="sxs-lookup"><span data-stu-id="e6b15-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="e6b15-110">Per compilare l'esempio, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="e6b15-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="e6b15-111">Verrà creato il file eseguibile shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="e6b15-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b15-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="e6b15-112">Example</span></span>  
 <span data-ttu-id="e6b15-113">Questo file dichiara la classe `Shape` che contiene la proprietà `Area` del tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="e6b15-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="e6b15-114">I modificatori della proprietà vengono inseriti nella dichiarazione della proprietà stessa.</span><span class="sxs-lookup"><span data-stu-id="e6b15-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="e6b15-115">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="e6b15-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="e6b15-116">Quando si dichiara una proprietà astratta, come `Area` in questo esempio, è sufficiente indicare le funzioni di accesso disponibili per la proprietà, senza implementarle.</span><span class="sxs-lookup"><span data-stu-id="e6b15-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="e6b15-117">In questo esempio è disponibile solo una funzione di accesso [get](../../language-reference/keywords/get.md), quindi la proprietà è di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="e6b15-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b15-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="e6b15-118">Example</span></span>  
 <span data-ttu-id="e6b15-119">Il codice seguente mostra tre sottoclassi di `Shape` e il modo in cui eseguono l'override della proprietà `Area` per fornire la propria implementazione.</span><span class="sxs-lookup"><span data-stu-id="e6b15-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="e6b15-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="e6b15-120">Example</span></span>  
 <span data-ttu-id="e6b15-121">Il codice seguente mostra un programma di test che crea diversi oggetti derivati da `Shape` e stampa le relative aree.</span><span class="sxs-lookup"><span data-stu-id="e6b15-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b15-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e6b15-122">See also</span></span>

- [<span data-ttu-id="e6b15-123">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="e6b15-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6b15-124">Classi e struct</span><span class="sxs-lookup"><span data-stu-id="e6b15-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e6b15-125">Classi e membri delle classi astratte e sealed</span><span class="sxs-lookup"><span data-stu-id="e6b15-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="e6b15-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e6b15-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="e6b15-127">Procedura: Creare e usare assembly dalla riga di comando</span><span class="sxs-lookup"><span data-stu-id="e6b15-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
