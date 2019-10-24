---
title: Matrici come oggetti - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772116"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="b3ed2-102">Matrici come oggetti (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="b3ed2-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="b3ed2-103">In C# le matrici sono in effetti oggetti e non semplicemente aree indirizzabili di memoria contigua come in C e C++.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="b3ed2-104"><xref:System.Array> è il tipo di base astratto di tutti i tipi di matrice.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="b3ed2-105">È possibile utilizzare le proprietà e altri membri della classe che <xref:System.Array> dispone di.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="b3ed2-106">Un esempio è l'uso della proprietà <xref:System.Array.Length%2A> per ottenere la lunghezza di una matrice.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="b3ed2-107">Il codice seguente assegna la lunghezza della matrice `numbers`, ovvero `5`, a una variabile denominata `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="b3ed2-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="b3ed2-108">La classe <xref:System.Array> offre numerosi altri utili metodi e proprietà per l'ordinamento, la ricerca e la copia di matrici.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="b3ed2-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="b3ed2-109">Example</span></span>

<span data-ttu-id="b3ed2-110">Questo esempio usa la proprietà <xref:System.Array.Rank%2A> per visualizzare il numero di dimensioni di una matrice.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="b3ed2-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b3ed2-111">See also</span></span>

- [<span data-ttu-id="b3ed2-112">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="b3ed2-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3ed2-113">Array</span><span class="sxs-lookup"><span data-stu-id="b3ed2-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="b3ed2-114">Matrici unidimensionali</span><span class="sxs-lookup"><span data-stu-id="b3ed2-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="b3ed2-115">Matrici multidimensionali</span><span class="sxs-lookup"><span data-stu-id="b3ed2-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="b3ed2-116">Matrici irregolari</span><span class="sxs-lookup"><span data-stu-id="b3ed2-116">Jagged Arrays</span></span>](./jagged-arrays.md)
