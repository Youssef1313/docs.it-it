---
title: Livelli di rendering della grafica
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: b5bedae16a6c53aebf4d577b8cd812da992106f2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629905"
---
# <a name="graphics-rendering-tiers"></a>Livelli di rendering della grafica
Un livello di rendering definisce un livello di prestazioni e funzionalità hardware grafiche per un dispositivo che esegue un'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Hardware grafico  
 Le funzionalità dell'hardware grafico che hanno effetto sui livelli di rendering sono:  
  
- **RAM video** La quantità di memoria video sull'hardware grafico determina le dimensioni e il numero di buffer che possono essere usati per la composizione della grafica.  
  
- **Pixel shader** Un pixel shader è una funzione di elaborazione grafica che calcola gli effetti sui singoli pixel. A seconda della risoluzione della grafica visualizzata, potrebbe essere necessario elaborare diversi milioni di pixel per ogni fotogramma visualizzato.  
  
- **Vertex shader** Un vertex shader è una funzione di elaborazione grafica che esegue operazioni matematiche sui dati dei vertici dell'oggetto.  
  
- **Supporto per più trame** Il supporto per più trame è la possibilità di applicare due o più trame distinte durante un'operazione di fusione su un oggetto grafico 3D. Il grado di supporto per più trame è determinato dal numero di unità a più trame nell'hardware grafico.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Definizioni dei livelli di rendering  
 Le funzionalità dell'hardware grafico determinano la capacità di rendering di un'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il sistema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definisce tre livelli di rendering:  
  
- **Livello di rendering 0** Nessuna accelerazione hardware grafico. Tutte le funzionalità grafiche usano l'accelerazione software. Il livello della versione di DirectX è inferiore alla versione 9,0.  
  
- **Livello di rendering 1** Alcune funzionalità grafiche usano l'accelerazione hardware grafico. Il livello della versione di DirectX è maggiore o uguale alla versione 9,0.  
  
- **Livello di rendering 2** La maggior parte delle funzionalità grafiche usa l'accelerazione hardware grafico. Il livello della versione di DirectX è maggiore o uguale alla versione 9,0.  
  
 La <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> proprietà consente di recuperare il livello di rendering in fase di esecuzione dell'applicazione. Il livello di rendering consente di determinare se il dispositivo supporta determinate funzionalità grafiche con accelerazione hardware. L'applicazione può quindi usare percorsi di codice diversi in fase di esecuzione a seconda del livello di rendering supportato dal dispositivo.  
  
### <a name="rendering-tier-0"></a>Livello di rendering 0  
 Il valore 0 del livello di rendering indica che l'accelerazione hardware grafico non è disponibile per l'applicazione sul dispositivo. A questo livello, si deve presupporre che il rendering tutta la grafica verrà eseguito dal software senza accelerazione hardware. Questa funzionalità del livello corrisponde a una versione di DirectX inferiore a 9,0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Livello di rendering 1 e livello di rendering 2  
  
> [!NOTE]
>  A partire da .NET Framework 4, il livello di rendering 1 è stato ridefinito in modo da includere solo hardware grafico che supporta DirectX 9,0 o versione successiva. L'hardware grafico che supporta DirectX 7 o 8 è ora definito come livello di rendering 0.  
  
 Il valore 1 o 2 del livello di rendering indica che la maggior parte delle funzionalità grafiche di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] userà l'accelerazione hardware se le risorse di sistema necessarie sono disponibili e non sono state esaurite. Corrisponde a una versione di DirectX maggiore o uguale a 9,0.  
  
 La tabella seguente illustra le differenze dei requisiti di hardware grafico tra il livello di rendering 1 e livello di rendering 2:  
  
|Funzionalità|Livello 1|Livello 2|  
|-------------|------------|------------|  
|Versione DirectX|Deve essere superiore o uguale alla 9.0.|Deve essere superiore o uguale alla 9.0.|  
|RAM video|Deve essere superiore o uguale a 60 MB.|Deve essere superiore o uguale a 120 MB.|  
|Pixel shader|Il livello della versione deve essere superiore o uguale alla 2.0.|Il livello della versione deve essere superiore o uguale alla 2.0.|  
|Vertex shader|Nessun requisito.|Il livello della versione deve essere superiore o uguale alla 2.0.|  
|Unità a più trame|Nessun requisito.|Il numero di unità deve essere superiore o uguale a 4.|  
  
 Le funzionalità e capacità seguenti sono con accelerazione hardware per il livello di rendering 1 e livello di rendering 2:  
  
|Funzionalità|Note|  
|-------------|-----------|  
|Rendering 2D|È supportata la maggior parte del rendering 2D.|  
|Rasterizzazione 3D|È supportata la maggior parte delle rasterizzazioni 3D.|  
|Filtro anisotropico 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prova a usare il filtro anisotropico quando viene eseguito il rendering del contenuto 3D. Il filtro anisotropico consente di migliorare la qualità delle trame di un'immagine su superfici lontane e molto inclinate rispetto alla fotocamera.|  
|Mapping MIP 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prova a usare il mapping MIP quando viene eseguito il rendering del contenuto 3D. Il mapping MIP migliora la qualità del rendering della trama quando una trama occupa un campo di visualizzazione più <xref:System.Windows.Controls.Viewport3D>piccolo in un oggetto.|  
|Sfumature radiali|Sebbene supportato, evitare l'utilizzo di <xref:System.Windows.Media.RadialGradientBrush> su oggetti di grandi dimensioni.|  
|Calcoli per l'illuminazione 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] esegue l'illuminazione per vertice, in cui l'intensità della luce deve essere calcolata in ogni vertice per ogni materiale applicato a un mesh.|  
|Rendering del testo|Il rendering dei tipi di carattere a livello di sub-pixel usa i pixel shader disponibili nell'hardware grafico.|  
  
 Le funzionalità e capacità seguenti sono con accelerazione hardware solo per il livello di rendering 2:  
  
|Funzionalità|Note|  
|-------------|-----------|  
|Anti-aliasing 3D|L'anti-aliasing 3D è supportato solo nei sistemi operativi che supportano Windows Display Driver Model (WDDM), ad esempio [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] e [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Le funzionalità e capacità seguenti sono **senza** accelerazione hardware:  
  
|Funzionalità|Note|  
|-------------|-----------|  
|Contenuti stampati|Il rendering di tutto il contenuto stampato viene eseguito con la pipeline software [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Contenuto rasterizzato che usa<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Qualsiasi contenuto di cui viene eseguito <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> il rendering <xref:System.Windows.Media.Imaging.RenderTargetBitmap>tramite il metodo di.|  
|Contenuto affiancato che usa<xref:System.Windows.Media.TileBrush>|Qualsiasi contenuto affiancato in cui <xref:System.Windows.Media.TileBrush.TileMode%2A> la proprietà <xref:System.Windows.Media.TileBrush> di è impostata su <xref:System.Windows.Media.TileMode.Tile>.|  
|Superfici che superano le dimensioni massime della trama dell'hardware grafico|Per la maggior parte dell'hardware grafico, le superfici di grandi dimensioni sono pari a 2048x2048 o 4096x4096 pixel.|  
|Qualsiasi operazione il cui requisito per la RAM video supera la memoria dell'hardware grafico|È possibile monitorare l'utilizzo della RAM video dell'applicazione usando lo strumento Perforator incluso nella [famiglia di prodotti per l'analisi delle prestazioni WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) in Windows SDK.|  
|Finestre a livelli|Le finestre a livelli consentono alle applicazioni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] di eseguire il rendering del contenuto sullo schermo in una finestra non rettangolare. Nei sistemi operativi che supportano Windows Display Driver Model (WDDM), ad esempio [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] e [!INCLUDE[win7](../../../../includes/win7-md.md)], le finestre a livelli sono con accelerazione hardware. Negli altri sistemi, ad esempio [!INCLUDE[winxp](../../../../includes/winxp-md.md)], il rendering delle finestre a livelli viene eseguito dal software senza accelerazione hardware.<br /><br /> È possibile abilitare le finestre sovrapposte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] in impostando le <xref:System.Windows.Window> proprietà seguenti:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Altre risorse  
 Le risorse seguenti consentono di analizzare le caratteristiche delle prestazioni dell'applicazione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="graphics-rendering-registry-settings"></a>Impostazioni del Registro di sistema per il rendering della grafica  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornisce quattro impostazioni del Registro di sistema per controllare il rendering [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
|Impostazione|DESCRIZIONE|  
|-------------|-----------------|  
|**Opzione di disabilitazione dell'accelerazione hardware**|Specifica se l'accelerazione hardware deve essere abilitata.|  
|**Valore massimo di multicampionamento**|Specifica il grado di campionamento multiplo per l'anti-aliasing del contenuto 3D.|  
|**Impostazione Data driver video necessaria**|Specifica se il sistema disabilita l'accelerazione hardware per i driver rilasciati prima di novembre 2004.|  
|**Opzione per l'uso di unità di rasterizzazione dei riferimenti**|Specifica se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve usare l'unità di rasterizzazione dei riferimenti.|  
  
 A queste impostazioni è possibile accedere tramite qualsiasi utilità di configurazione esterna che possa fare riferimento alle impostazioni del Registro di sistema di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Per creare o modificare queste impostazioni, è possibile accedere ai valori direttamente usando l'editor del Registro di sistema di [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Per altre informazioni, vedere [Impostazioni del Registro di sistema per il rendering della grafica](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Strumenti per la profilatura delle prestazioni WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] include una suite di strumenti per la profilatura delle prestazioni che consentono di analizzare il comportamento dell'applicazione in fase di esecuzione e di determinare i tipi di ottimizzazioni delle prestazioni che è possibile applicare. La tabella seguente elenca gli strumenti di profilatura delle prestazioni inclusi nello strumento [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)], WPF Performance Suite:  
  
|Strumento|Descrizione|  
|----------|-----------------|  
|Perforator|Da usare per l'analisi del comportamento di rendering.|  
|Visual Profiler|Da usare per la profilatura dell'uso dei servizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], come gestione del layout e degli eventi, per gli elementi nella struttura ad albero visuale.|  
  
 WPF Performance Suite offre una visualizzazione grafica avanzata dei dati sulle prestazioni. Per altre informazioni sugli strumenti per le prestazioni WPF, vedere [Famiglia di prodotti per l'analisi delle prestazioni WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Strumento di diagnostica DirectX  
 Lo strumento di diagnostica DirectX, Dxdiag. exe, è progettato per semplificare la risoluzione dei problemi correlati a DirectX. La cartella di installazione predefinita per lo strumento di diagnostica DirectX è la seguente:  
  
 `~\Windows\System32`  
  
 Quando si esegue lo strumento di diagnostica DirectX, la finestra principale contiene un set di schede che consentono di visualizzare e diagnosticare le informazioni correlate a DirectX. Ad esempio, la scheda **sistema** fornisce informazioni di sistema sul computer e specifica la versione di DirectX installata nel computer.  
  
 ![Screenshot Strumento]di diagnostica DirectX(./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Finestra principale dello strumento di diagnostica DirectX  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Ottimizzazione delle prestazioni di applicazioni WPF](optimizing-wpf-application-performance.md)
- [Famiglia di prodotti per l'analisi delle prestazioni WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Impostazioni del Registro di sistema per il rendering della grafica](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Suggerimenti sulle animazioni](../graphics-multimedia/animation-tips-and-tricks.md)
