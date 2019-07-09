---
title: 'Procedura: Applicare un disegno a un modello tridimensionale'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662808"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="ba942-102">Procedura: Applicare un disegno a un modello tridimensionale</span><span class="sxs-lookup"><span data-stu-id="ba942-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="ba942-103">In questo esempio viene illustrato come utilizzare un <xref:System.Windows.Media.DrawingBrush> come il <xref:System.Windows.Media.Media3D.Material> applicato a un modello 3D.</span><span class="sxs-lookup"><span data-stu-id="ba942-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="ba942-104">Il codice seguente definisce una <xref:System.Windows.Media.DrawingGroup> come contenuto di un <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="ba942-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="ba942-105">Il <xref:System.Windows.Media.DrawingBrush> viene impostato come i <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> proprietà del <xref:System.Windows.Media.Media3D.DiffuseMaterial> applicata a un piano 3D.</span><span class="sxs-lookup"><span data-stu-id="ba942-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>  
  
 <span data-ttu-id="ba942-106">**Nota:** È spesso consigliabile definire gli oggetti complessi e valori, ad esempio il disegno sotto come le risorse che possono essere riutilizzate e semplificano il codice.</span><span class="sxs-lookup"><span data-stu-id="ba942-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="ba942-107">Visualizzare [risorse XAML](../advanced/xaml-resources.md) per altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="ba942-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="ba942-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="ba942-108">Example</span></span>  
 <span data-ttu-id="ba942-109">Il codice seguente illustra l'intero esempio.</span><span class="sxs-lookup"><span data-stu-id="ba942-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ba942-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ba942-110">See also</span></span>

- [<span data-ttu-id="ba942-111">Risorse XAML</span><span class="sxs-lookup"><span data-stu-id="ba942-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="ba942-112">Creare una scena tridimensionale</span><span class="sxs-lookup"><span data-stu-id="ba942-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ba942-113">Cenni preliminari sugli oggetti Drawing</span><span class="sxs-lookup"><span data-stu-id="ba942-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="ba942-114">Panoramica sulla grafica tridimensionale</span><span class="sxs-lookup"><span data-stu-id="ba942-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
