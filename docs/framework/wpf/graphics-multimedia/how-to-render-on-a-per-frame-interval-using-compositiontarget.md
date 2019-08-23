---
title: "Procedura: Eseguire il rendering in un intervallo per frame usando l'oggetto CompositionTarget"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956989"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Procedura: Eseguire il rendering in un intervallo per frame usando l'oggetto CompositionTarget
Il motore delle animazioni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre molte funzionalità per la creazione di animazioni basate su fotogrammi. Esistono tuttavia scenari di applicazione in cui è necessario un controllo con granularità più fine sul rendering per fotogramma. L' <xref:System.Windows.Media.CompositionTarget> oggetto fornisce la possibilità di creare animazioni personalizzate basate su un callback per frame.  
  
 <xref:System.Windows.Media.CompositionTarget>è una classe statica che rappresenta l'area di visualizzazione in cui viene disegnata l'applicazione. L' <xref:System.Windows.Media.CompositionTarget.Rendering> evento viene generato ogni volta che viene disegnata la scena dell'applicazione. La frequenza dei fotogrammi di rendering è il numero di volte al secondo in cui viene disegnata la scena.  
  
> [!NOTE]
> Per un esempio di codice completo <xref:System.Windows.Media.CompositionTarget>che usa, vedere [uso dell'esempio CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Esempio  
 L' <xref:System.Windows.Media.CompositionTarget.Rendering> evento viene generato durante [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] il processo di rendering. Nell'esempio seguente viene illustrato come registrare un <xref:System.EventHandler> delegato nel metodo statico <xref:System.Windows.Media.CompositionTarget.Rendering> in <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 È possibile usare il metodo del gestore eventi di rendering per creare il contenuto del disegno personalizzato. Questo metodo del gestore eventi viene chiamato una volta per ogni fotogramma. Ogni volta che [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] esegue il marshalling dei dati di rendering salvati in modo permanente nella struttura ad albero visuale sul grafico della scena di composizione, viene chiamato il metodo del gestore eventi. Il metodo del gestore eventi viene chiamato anche se le modifiche alla struttura ad albero visuale forzano aggiornamenti al grafico della scena di composizione. Si noti che il metodo del gestore eventi verrà chiamato dopo l'elaborazione del layout. È tuttavia possibile modificare il layout nel metodo del gestore eventi, ovvero il layout verrà ulteriormente elaborato prima del rendering.  
  
 Nell'esempio seguente viene illustrato come è possibile fornire un disegno personalizzato <xref:System.Windows.Media.CompositionTarget> in un metodo del gestore eventi. In questo caso, il colore di sfondo di <xref:System.Windows.Controls.Canvas> viene disegnato con un valore di colore basato sulla posizione della coordinata del mouse. Se si sposta il mouse all'interno <xref:System.Windows.Controls.Canvas>di, il colore di sfondo cambia. Viene anche calcolata la frequenza media dei fotogrammi in base al tempo trascorso e al numero totale dei fotogrammi sottoposti a rendering.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Si potrebbe rilevare che un disegno personalizzato procede a velocità diverse in computer diversi. Questo avviene poiché il disegno personalizzato dipende dalla frequenza dei fotogrammi. A seconda del sistema in esecuzione e del carico di lavoro del sistema, l' <xref:System.Windows.Media.CompositionTarget.Rendering> evento può essere chiamato un numero diverso di volte al secondo. Per informazioni su come determinare le prestazioni e le funzionalità hardware grafiche per un dispositivo che esegue un'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vedere [Livelli di rendering della grafica](../advanced/graphics-rendering-tiers.md).  
  
 L'aggiunta o la rimozione <xref:System.EventHandler> di un delegato di rendering durante l'attivazione dell'evento verrà posticipata fino al termine dell'attivazione dell'evento. Questo è coerente con la <xref:System.MulticastDelegate>modalità di gestione degli eventi basati su in Common Language Runtime (CLR). Si noti anche che gli eventi di rendering non verranno necessariamente chiamati in un ordine particolare. Se si dispone di <xref:System.EventHandler> più delegati che si basano su un particolare ordine, <xref:System.Windows.Media.CompositionTarget.Rendering> è necessario registrare un singolo evento e multiplexare i delegati nell'ordine corretto.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Media.CompositionTarget>
- [Cenni preliminari sul rendering della grafica WPF](wpf-graphics-rendering-overview.md)
