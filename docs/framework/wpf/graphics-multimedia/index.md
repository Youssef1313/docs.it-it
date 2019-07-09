---
title: Grafica e funzionalità multimediali
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: a770bcbbc8ac553c55e9dda5097abec8790182e5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663727"
---
# <a name="graphics-and-multimedia"></a>Grafica e funzionalità multimediali

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornisce supporto per funzionalità multimediali, grafica vettoriale, animazione e composizione del contenuto, rendendo più semplice per gli sviluppatori compilare il contenuto e le interfacce utente interessanti. Tramite [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], è possibile creare grafica vettoriale o animazioni complesse e integrare file multimediali nelle applicazioni.

Questo argomento presenta le funzionalità di grafica, di animazione e di file multimediali di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], che consentono di aggiungere elementi grafici, effetti di transizione, audio e video alle applicazioni.

> [!NOTE]
> L'uso di tipi WPF in un servizio Windows è fortemente sconsigliato. Se si tenta di usare tipi WPF in un servizio Windows, è possibile che tale servizio non funzioni come previsto.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Novità di grafica e funzionalità multimediali in WPF 4

Sono state apportate diverse modifiche correlate agli elementi grafici e alle animazioni.

- Arrotondamento del layout

  Quando il bordo di un oggetto cade al centro del pixel di un dispositivo, il sistema grafico indipendente da DPI può creare elementi di rendering, ad esempio bordi sfocati o semitrasparenti. Le versioni precedenti di WPF includevano lo snapping dei pixel per gestire questa situazione. In Silverlight 2 è stato introdotto l'arrotondamento del layout, che è un altro modo per spostare gli elementi in modo che i bordi rientrino nei limiti dei pixel intero. WPF supporta ora l'arrotondamento del layout con il <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> proprietà associata in <xref:System.Windows.FrameworkElement>.

- Composizione memorizzata nella cache

  Con la nuova <xref:System.Windows.Media.BitmapCache> e <xref:System.Windows.Media.BitmapCacheBrush> classi, è possibile memorizzare nella cache un aspetto complesso della struttura ad albero visuale come bitmap e migliorare notevolmente il tempo di rendering. La bitmap risponderà all'input dell'utente, ad esempio i clic del mouse, e sarà possibile disegnarla su altri elementi esattamente come con un pennello.

- Supporto Pixel Shader 3

  WPF 4 si basa sul <xref:System.Windows.Media.Effects.ShaderEffect> supporto introdotto in WPF 3.5 SP1, consentendo alle applicazioni di scrivere effetti usando Pixel Shader (PS) versione 3.0. Il modello di shader PS 3.0 è più avanzato rispetto a PS 2.0 e rende disponibile un maggior numero di effetti nell'hardware supportato.

- Funzioni di interpolazione

  È possibile migliorare le animazioni con funzioni di interpolazione che forniscono il controllo del comportamento delle animazioni. Ad esempio, è possibile applicare un <xref:System.Windows.Media.Animation.ElasticEase> per un'animazione per conferire un effetto molla l'animazione. Per altre informazioni, vedere i tipi di interpolazione nel <xref:System.Windows.Media.Animation> dello spazio dei nomi.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafica e rendering

WPF include il supporto per gli elementi grafici 2D di qualità elevata. La funzionalità include pennelli, geometrie, immagini, forme e trasformazioni. Per altre informazioni, vedere [Grafica](graphics.md). Il rendering degli elementi grafici è basato sul <xref:System.Windows.Media.Visual> classe. La struttura degli oggetti visivi sullo schermo è descritta dalla struttura ad albero visuale. Per altre informazioni, vedere [Cenni preliminari sul rendering della grafica WPF](wpf-graphics-rendering-overview.md).

### <a name="2-d-shapes"></a>Forme 2D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornisce una libreria di comunemente usate, disegnate da vettori forme 2D, quali rettangoli ed ellissi, come illustrato di seguito.

![Diagramma che mostra ellissi e rettangoli.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Queste forme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intrinseche non sono solo forme: sono elementi programmabili che implementano molte delle funzionalità tipiche dei controlli più comuni, che includono l'input della tastiera e del mouse. Nell'esempio seguente viene illustrato come gestire le <xref:System.Windows.UIElement.MouseUp> eventi generati facendo un <xref:System.Windows.Shapes.Ellipse> elemento.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

Nella figura seguente viene illustrato l'output del markup e code-behind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] precedente.

![Una finestra di messaggio che informa che "You clicked the ellipse!"](./media/index/messagebox-text-output.png)

Per altre informazioni, vedere [Panoramica degli oggetti Shape e sulle funzionalità di disegno di base di WPF](shapes-and-basic-drawing-in-wpf-overview.md). Per un esempio introduttivo, vedere [Esempio di elementi forma](https://go.microsoft.com/fwlink/?LinkID=160037).

### <a name="2-d-geometries"></a>Geometrie 2D

Quando le forme che il 2D [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] offre non sono sufficienti, è possibile usare [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supportano per geometrie e tracciati per crearne una propria. La figura seguente mostra come usare le geometrie per creare forme, ad esempio un pennello da disegno e per ritagliare altri elementi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

![Screenshot che illustra come è possibile usare le geometrie per creare forme.](./media/index/use-geometries-create-shapes.png)

Per altre informazioni, vedere [Cenni preliminari sulle classi Geometry](geometry-overview.md). Per un esempio introduttivo, vedere [Esempio di geometrie](https://go.microsoft.com/fwlink/?LinkID=159989).

### <a name="2-d-effects"></a>Effetti 2D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornisce una libreria di classi 2D che è possibile usare per creare una varietà di effetti. La funzionalità di rendering 2D del [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] offre la possibilità di disegnare [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementi con sfumature, bitmap, disegni e video; e di modificarli mediante rotazione, ridimensionamento e inclinazione. La figura seguente fornisce un esempio dei molti effetti che è possibile ottenere usando i pennelli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

![Figura che illustra le diverse pennelli WPF e gli elementi di disegno.](./media/index/brushes-paint-elements.png)

Per altre informazioni, vedere [Panoramica dei pennelli di WPF](wpf-brushes-overview.md). Per un esempio introduttivo, vedere [Esempio di pennelli](https://go.microsoft.com/fwlink/?LinkID=159973).

<a name="rendering"></a>

## <a name="3-d-rendering"></a>Rendering 3D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornisce un set di funzionalità di rendering 3D che si integrano con il supporto di grafica 2D in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in ordine per poter creare layout più interessanti, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]e visualizzazione dei dati. A un'estremità dello spettro, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consente di eseguire il rendering di immagini 2D su superfici di forme 3D che illustra la figura seguente.

![Screenshot di un esempio che Mostra forme 3D con diverse trame.](./media/index/visual-three-dimensional-shape.png)

Per altre informazioni, vedere [Panoramica della grafica tridimensionale](3-d-graphics-overview.md). Per un esempio introduttivo, vedere [Esempio di solidi 3D](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animazione

Usare l'animazione per applicare ai controlli e agli elementi gli effetti di ingrandimento, tremolio, rotazione e dissolvenza, nonché per creare interessanti transizioni tra le pagine e altro ancora. Poiché [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consente di animare la maggior parte delle proprietà, non solo è possibile animare la maggior parte degli oggetti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ma è anche possibile usare [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] per animare oggetti personalizzati creati.

![Screenshot di un cubo animato.](./media/index/animate-custom-objects.png)

Per altre informazioni, vedere [Panoramica dell'animazione](animation-overview.md). Per un esempio introduttivo, vedere [Raccolta di esempi di animazioni](https://go.microsoft.com/fwlink/?LinkID=159969).

<a name="media"></a>

## <a name="media"></a>Supporti

Immagini, video e audio sono supporti multimediali per trasmettere informazioni ed esperienze utente.

### <a name="images"></a>Immagini

Le immagini, tra cui le icone, gli sfondi e le parti di animazioni, sono un componente fondamentale della maggior parte delle applicazioni. Poiché spesso è necessario usare le immagini, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consente di usarle in vari modi. La figura seguente mostra uno dei vari modi.

![Screenshot di esempio Styling](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Per altre informazioni, vedere [Panoramica della creazione dell'immagine](imaging-overview.md).

### <a name="video-and-audio"></a>Video e audio

Una caratteristica fondamentale delle funzionalità grafiche di [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consiste nel fornire il supporto nativo per l'uso di contenuti multimediali, inclusi video e audio. L'esempio seguente illustra come inserire un lettore multimediale in un'applicazione.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> è in grado di riprodurre video e audio ed è sufficientemente estensibile per consentire la creazione di custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].

Per altre informazioni, vedere [Panoramica delle funzionalità multimediali](multimedia-overview.md).

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Grafica bidimensionale e creazione di immagini](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Cenni preliminari sugli oggetti Shape e sulle funzionalità di disegno di base di WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Cenni sul disegno con colori a tinta unita e sfumature](painting-with-solid-colors-and-gradients-overview.md)
- [Disegnare con oggetti Image, Drawing e Visual](painting-with-images-drawings-and-visuals.md)
- [Animazione e temporizzazione procedure](animation-and-timing-how-to-topics.md)
- [Panoramica sulla grafica tridimensionale](3-d-graphics-overview.md)
- [Panoramica delle funzionalità multimediali](multimedia-overview.md)
