---
title: Utilizzo degli oggetti DrawingVisual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962836"
---
# <a name="using-drawingvisual-objects"></a>Utilizzo degli oggetti DrawingVisual
In questo argomento viene fornita una panoramica su come <xref:System.Windows.Media.DrawingVisual> utilizzare gli oggetti a livello di oggetto visivo.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Oggetto DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> È una classe di disegno semplificata utilizzata per il rendering di forme, immagini o testo. Questa classe è considerata semplice perché non offre la gestione di layout o eventi, con un conseguente aumento delle prestazioni. Per questo motivo, i disegni sono ideali per sfondi e ClipArt.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Contenitore host di DrawingVisual  
 Per usare <xref:System.Windows.Media.DrawingVisual> gli oggetti, è necessario creare un contenitore host per gli oggetti. L'oggetto contenitore host deve derivare dalla <xref:System.Windows.FrameworkElement> classe, che fornisce il layout e il supporto per la gestione <xref:System.Windows.Media.DrawingVisual> degli eventi che la classe non dispone di. Tramite l'oggetto contenitore host non vengono visualizzate proprietà visibili, poiché lo scopo principale di questo oggetto è quello di contenere oggetti figlio. Tuttavia, la <xref:System.Windows.UIElement.Visibility%2A> proprietà del contenitore host deve essere impostata su <xref:System.Windows.Visibility.Visible>; in caso contrario, nessuno degli elementi figlio sarà visibile.  
  
 Quando si crea un oggetto contenitore host per oggetti visivi, è necessario archiviare i riferimenti agli oggetti visivi <xref:System.Windows.Media.VisualCollection>in un oggetto. Usare il <xref:System.Windows.Media.VisualCollection.Add%2A> metodo per aggiungere un oggetto visivo al contenitore host. Nell'esempio seguente viene creato un oggetto contenitore host e tre oggetti visivi vengono aggiunti a <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Per l'esempio di codice completo dal quale è stato estratto l'esempio di codice precedente, vedere [Hit Test Using DrawingVisuals Sample (Esempio di Hit Test mediante DrawingVisual)](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Creazione di oggetti DrawingVisual  
 Quando si crea un <xref:System.Windows.Media.DrawingVisual> oggetto, il contenuto non viene disegnato. È possibile aggiungere contenuto di testo, grafica o immagine recuperando l'oggetto <xref:System.Windows.Media.DrawingContext> e creandone il contenuto. Una <xref:System.Windows.Media.DrawingContext> viene restituita chiamando il <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodo di un <xref:System.Windows.Media.DrawingVisual> oggetto.  
  
 Per creare un rettangolo in <xref:System.Windows.Media.DrawingContext>, utilizzare il <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metodo dell' <xref:System.Windows.Media.DrawingContext> oggetto. Sono disponibili metodi simili per disegnare altri tipi di contenuto. Al termine della creazione del contenuto in <xref:System.Windows.Media.DrawingContext>, chiamare il <xref:System.Windows.Media.DrawingContext.Close%2A> metodo per chiudere <xref:System.Windows.Media.DrawingContext> e salvare in modo permanente il contenuto.  
  
 Nell'esempio seguente viene creato un <xref:System.Windows.Media.DrawingVisual> oggetto e viene disegnato un rettangolo nel relativo. <xref:System.Windows.Media.DrawingContext>  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Creazione di override per i membri FrameworkElement  
 L'oggetto contenitore host è responsabile della gestione della raccolta di oggetti visivi. A tale scopo, è necessario che il contenitore host implementi <xref:System.Windows.FrameworkElement> gli override del membro per la classe derivata.  
  
 L'elenco seguente descrive due membri per i quali è necessario eseguire l'override:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Restituisce un elemento figlio in corrispondenza dell'indice specificato dalla raccolta di elementi figlio.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Ottiene il numero di elementi figlio visivi in questo elemento.  
  
 Nell'esempio seguente vengono implementate le sostituzioni <xref:System.Windows.FrameworkElement> per i due membri.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Supporto per l'hit testing  
 L'oggetto contenitore host può fornire la gestione degli eventi anche se non visualizza alcuna proprietà visibile, ma la relativa <xref:System.Windows.UIElement.Visibility%2A> proprietà deve essere impostata su <xref:System.Windows.Visibility.Visible>. Ciò consente di creare una routine di gestione degli eventi per il contenitore host in grado di intercettare eventi del mouse, ad esempio il rilascio del pulsante sinistro del mouse. La routine di gestione degli eventi può quindi implementare l'hit test richiamando il <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodo. Il <xref:System.Windows.Media.HitTestResultCallback> parametro del metodo fa riferimento a una procedura definita dall'utente che è possibile usare per determinare l'azione risultante di un hit test.  
  
 Nell'esempio seguente il supporto per l'hit testing viene implementato per l'oggetto contenitore host e i relativi elementi figlio.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Cenni preliminari sul rendering della grafica WPF](wpf-graphics-rendering-overview.md)
- [Hit testing a livello visivo](hit-testing-in-the-visual-layer.md)
