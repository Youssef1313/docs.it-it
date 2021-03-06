---
title: "Procedura: Aggiungere un'animazione a un oggetto lungo un tracciato (animazione Matrix)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 3c90d20cac60004aa9876d9fe8d213d33c5a6883
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651440"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Procedura: Aggiungere un'animazione a un oggetto lungo un tracciato (animazione Matrix)
Questo esempio illustra come usare il <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> classe per animare un oggetto lungo un tracciato definito da un <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente aggiunge un'animazione a un oggetto lungo un tracciato effettuando le operazioni seguenti:  
  
- Si applica un <xref:System.Windows.Media.MatrixTransform> all'oggetto per spostarlo.  
  
- Definisce il percorso utilizzando un <xref:System.Windows.Media.PathGeometry>.  
  
- Crea una <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e lo usa per animare la <xref:System.Windows.Media.Matrix> proprietà del <xref:System.Windows.Media.MatrixTransform>. Il <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> accetta il <xref:System.Windows.Media.PathGeometry> e lo usa per generare <xref:System.Windows.Media.Matrix> valori.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Per l'esempio completo, vedere [esempio di animazione tracciato](https://go.microsoft.com/fwlink/?LinkID=160028). Per altre informazioni sui tracciati geometrici, vedere la [panoramica delle classi Geometry](geometry-overview.md).  
  
## <a name="see-also"></a>Vedere anche

- [Cenni preliminari sull'animazione](animation-overview.md)
- [Path Animation Sample (Esempio di animazione tracciato)](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Procedure relative all'animazione percorso](path-animation-how-to-topics.md)
