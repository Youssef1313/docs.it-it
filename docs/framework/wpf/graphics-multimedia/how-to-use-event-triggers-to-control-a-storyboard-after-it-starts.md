---
title: 'Procedura: Usare i trigger di eventi per controllare uno storyboard in seguito al relativo avvio'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855857"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="e644a-102">Procedura: Usare i trigger di eventi per controllare uno storyboard in seguito al relativo avvio</span><span class="sxs-lookup"><span data-stu-id="e644a-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="e644a-103">Questo esempio Mostra come controllare un oggetto <xref:System.Windows.Media.Animation.Storyboard> dopo l'avvio.</span><span class="sxs-lookup"><span data-stu-id="e644a-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="e644a-104">Per avviare un <xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utilizzando, utilizzare <xref:System.Windows.Media.Animation.BeginStoryboard>, che distribuisce le animazioni agli oggetti e alle proprietà a cui viene aggiunta un'animazione, quindi avvia lo storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="e644a-105">Se si assegna <xref:System.Windows.Media.Animation.BeginStoryboard> un nome specificando la <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> relativa proprietà, lo si imposta come storyboard controllabile.</span><span class="sxs-lookup"><span data-stu-id="e644a-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="e644a-106">È quindi possibile controllare in modo interattivo lo storyboard dopo l'avvio.</span><span class="sxs-lookup"><span data-stu-id="e644a-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="e644a-107">Utilizzare le seguenti azioni storyboard insieme <xref:System.Windows.EventTrigger> agli oggetti per controllare uno storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="e644a-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Sospende lo storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="e644a-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Riprende uno storyboard sospeso.</span><span class="sxs-lookup"><span data-stu-id="e644a-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="e644a-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifica la velocità dello storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="e644a-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Sposta uno storyboard alla fine del periodo di riempimento, se presente.</span><span class="sxs-lookup"><span data-stu-id="e644a-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="e644a-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Arresta lo storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="e644a-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Rimuove lo storyboard, liberando le risorse.</span><span class="sxs-lookup"><span data-stu-id="e644a-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="e644a-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="e644a-114">Example</span></span>

<span data-ttu-id="e644a-115">Nell'esempio seguente vengono utilizzate azioni storyboard controllabili per controllare in modo interattivo uno storyboard.</span><span class="sxs-lookup"><span data-stu-id="e644a-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="e644a-116">Per vedere un esempio di controllo di uno storyboard tramite il codice, vedere [controllare uno storyboard dopo l'avvio usando i metodi interattivi](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e644a-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="e644a-117">Per altri esempi, vedere la [raccolta di esempio Animation](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="e644a-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="e644a-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e644a-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="e644a-119">Controllare uno storyboard in seguito al relativo avvio usando i metodi interattivi</span><span class="sxs-lookup"><span data-stu-id="e644a-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="e644a-120">Cenni preliminari sull'animazione</span><span class="sxs-lookup"><span data-stu-id="e644a-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e644a-121">Cenni preliminari sugli storyboard</span><span class="sxs-lookup"><span data-stu-id="e644a-121">Storyboards Overview</span></span>](storyboards-overview.md)
