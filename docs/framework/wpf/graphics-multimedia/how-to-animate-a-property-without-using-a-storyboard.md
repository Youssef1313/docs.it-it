---
title: "Procedura: Aggiungere un'animazione a una proprietà senza usare uno storyboard"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963016"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Procedura: Aggiungere un'animazione a una proprietà senza usare uno storyboard
Questo esempio illustra un modo per applicare un'animazione a una proprietà senza usare un <xref:System.Windows.Media.Animation.Storyboard>oggetto.  
  
> [!NOTE]
> La funzionalità non è disponibile in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Per informazioni sull'animazione di proprietà in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vedere [animare una proprietà utilizzando uno Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Per applicare un'animazione locale a una proprietà, usare il <xref:System.Windows.UIElement.BeginAnimation%2A> metodo. Questo metodo accetta due parametri: un <xref:System.Windows.DependencyProperty> oggetto che specifica la proprietà a cui aggiungere un'animazione e l'animazione da applicare a tale proprietà.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere un'animazione alla larghezza e al colore di <xref:System.Windows.Controls.Button>sfondo di un oggetto.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Per l' <xref:System.Windows.Media.Animation> animazione di diversi tipi di proprietà è disponibile un'ampia gamma di classi di animazione nello spazio dei nomi. Per altre informazioni sulle proprietà di animazione vedere [Cenni preliminari sull'animazione](animation-overview.md). Per altre informazioni sulle proprietà di dipendenza (il tipo di proprietà che vengono visualizzate in questi esempi) e le relative funzionalità vedere [Cenni preliminari sulle proprietà di dipendenza](../advanced/dependency-properties-overview.md).  
  
 Esistono altri modi per animare senza usare <xref:System.Windows.Media.Animation.Storyboard> oggetti. per altre informazioni, vedere Cenni preliminari sulle tecniche di animazione delle [proprietà](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Cenni preliminari sulle tecniche di animazione delle proprietà](property-animation-techniques-overview.md)
- [Cenni preliminari sull'animazione](animation-overview.md)
