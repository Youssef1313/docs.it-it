---
title: 'Procedura: Creare un oggetto Expander con un oggetto ScrollViewer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: ef0bc5d344f7d465de9209708430d3e61d40d4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910793"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Procedura: Creare un oggetto Expander con un oggetto ScrollViewer
In questo esempio viene illustrato come creare un <xref:System.Windows.Controls.Expander> controllo che contiene contenuto complesso, ad esempio un'immagine e testo. L'esempio include anche il contenuto del <xref:System.Windows.Controls.Expander> in un <xref:System.Windows.Controls.ScrollViewer> controllo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come creare un <xref:System.Windows.Controls.Expander>. L'esempio Usa un' <xref:System.Windows.Controls.Primitives.BulletDecorator> controllo, che contiene un'immagine e testo, per definire il <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. Oggetto <xref:System.Windows.Controls.ScrollViewer> controllo fornisce un metodo per scorrere il contenuto espanso.  
  
 Si noti che nell'esempio viene impostato il <xref:System.Windows.FrameworkElement.Height%2A> proprietà il <xref:System.Windows.Controls.ScrollViewer> anziché sul contenuto. Se il <xref:System.Windows.FrameworkElement.Height%2A> è impostato sul contenuto, il <xref:System.Windows.Controls.ScrollViewer> non consente all'utente di scorrere il contenuto. Il <xref:System.Windows.FrameworkElement.Width%2A> è impostata sul <xref:System.Windows.Controls.Expander> controllo e questa impostazione si applica al <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e il contenuto espanso.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Controls.Expander>
- [Panoramica sul controllo Expander](expander-overview.md)
- [Procedure relative alle proprietà](expander-how-to-topics.md)
