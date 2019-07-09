---
title: 'Procedura: Inclinare un elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664081"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="eff70-102">Procedura: Inclinare un elemento</span><span class="sxs-lookup"><span data-stu-id="eff70-102">How to: Skew an Element</span></span>
<span data-ttu-id="eff70-103">In questo esempio viene illustrato come utilizzare un <xref:System.Windows.Media.SkewTransform> per inclinare un elemento.</span><span class="sxs-lookup"><span data-stu-id="eff70-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="eff70-104">L'inclinazione, nota anche come distorsione, è una trasformazione che adatta lo spazio delle coordinate in modo non uniforme.</span><span class="sxs-lookup"><span data-stu-id="eff70-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="eff70-105">Un utilizzo tipico di un <xref:System.Windows.Media.SkewTransform> è la simulazione della profondità 3D negli oggetti 2D.</span><span class="sxs-lookup"><span data-stu-id="eff70-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="eff70-106">Usare la <xref:System.Windows.Media.SkewTransform.CenterX%2A> e <xref:System.Windows.Media.SkewTransform.CenterY%2A> le proprietà per specificare il centro di punto del <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="eff70-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="eff70-107">Usare la <xref:System.Windows.Media.SkewTransform.AngleX%2A> e <xref:System.Windows.Media.SkewTransform.AngleY%2A> proprietà per specificare l'angolo di inclinazione dell'asse x e y e per inclinare il sistema di coordinate lungo questi assi.</span><span class="sxs-lookup"><span data-stu-id="eff70-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="eff70-108">Per stimare l'effetto di una trasformazione di inclinazione, considerare che <xref:System.Windows.Media.SkewTransform.AngleX%2A> inclina i valori dell'asse x rispetto al sistema di coordinate originale.</span><span class="sxs-lookup"><span data-stu-id="eff70-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="eff70-109">Pertanto, se un <xref:System.Windows.Media.SkewTransform.AngleX%2A> pari a 30, l'asse y ruota di 30 gradi attraverso l'origine e inclina i valori x-di 30 gradi da tale origine.</span><span class="sxs-lookup"><span data-stu-id="eff70-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="eff70-110">Analogamente, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> pari a 30 inclina i valori y della forma di 30 gradi dall'origine.</span><span class="sxs-lookup"><span data-stu-id="eff70-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="eff70-111">Si noti che non si tratta dello stesso effetto ottenuto traslando (spostando) il sistema di coordinate di 30 gradi nell'asse x o y.</span><span class="sxs-lookup"><span data-stu-id="eff70-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="eff70-112">L'esempio seguente applica un'inclinazione orizzontale di 45 gradi a un <xref:System.Windows.Shapes.Rectangle> da un punto centrale di (0,0).</span><span class="sxs-lookup"><span data-stu-id="eff70-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff70-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="eff70-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="eff70-114">L'esempio seguente applica un'inclinazione orizzontale di 45 gradi a un <xref:System.Windows.Shapes.Rectangle> da un punto centrale di (25,25).</span><span class="sxs-lookup"><span data-stu-id="eff70-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="eff70-115">L'esempio seguente applica un'inclinazione verticale di 45 gradi a un <xref:System.Windows.Shapes.Rectangle> da un punto centrale di (25,25).</span><span class="sxs-lookup"><span data-stu-id="eff70-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="eff70-116">La figura seguente illustra le diverse inclinazioni usate in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="eff70-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="eff70-117">![Esempi di SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="eff70-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="eff70-118">I tre esempi SkewTransform illustrati</span><span class="sxs-lookup"><span data-stu-id="eff70-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="eff70-119">Per l'esempio completo, vedere [2-D Transforms Sample (Esempio di trasformazioni 2D)](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="eff70-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff70-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eff70-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="eff70-121">Cenni preliminari sulle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="eff70-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="eff70-122">Procedure relative alle proprietà</span><span class="sxs-lookup"><span data-stu-id="eff70-122">How-to Topics</span></span>](transformations-how-to-topics.md)
