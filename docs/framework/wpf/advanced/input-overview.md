---
title: Cenni preliminari sull'input
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: defce7949bff47ef109e81d03894b13d95ba4c3d
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238501"
---
# <a name="input-overview"></a>Cenni preliminari sull'input
<a name="introduction"></a> Il [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sottosistema fornisce un'API potente per ottenere input da un'ampia gamma di dispositivi, tra cui il mouse, tastiera, tocco e stilo. Questo argomento descrive i servizi forniti da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e illustra l'architettura dei sistemi di input.

<a name="input_api"></a>
## <a name="input-api"></a>API di input
 L'esposizione di API è disponibile in classi basi dell'elemento di input primaria: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, e <xref:System.Windows.FrameworkContentElement>.  Per altre informazioni sugli elementi di base, vedere [Cenni preliminari sugli elementi di base](base-elements-overview.md).  Queste classi forniscono funzionalità per gli eventi di input correlati, ad esempio, a pressioni di tasti, pulsanti del mouse, rotellina del mouse, movimento del mouse, gestione dello stato attivo, stato mouse capture e altro. Collocando l'API di input negli elementi di base, invece di considerare tutti gli eventi di input come servizio, l'architettura di input consente gli eventi di input per essere originato da un particolare oggetto nell'interfaccia utente e per supportare uno schema di routing dell'evento in base al quale più di un elemento ha un opp ortunity per gestire un evento di input. A molti eventi di input è associata una coppia di eventi.  Ad esempio, la chiave di evento di selezione è associata il <xref:System.Windows.Input.Keyboard.KeyDown> e <xref:System.Windows.Input.Keyboard.PreviewKeyDown> eventi.  La differenza tra questi eventi consiste nel modo in cui ne viene eseguito il routing all'elemento di destinazione.  Gli eventi di anteprima scendono lungo l'albero degli elementi (tunneling), dall'elemento radice all'elemento di destinazione.  Gli eventi di bubbling invece salgono dall'elemento di destinazione all'elemento radice.  Il routing degli eventi in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] è illustrato in modo più dettagliato più avanti in questo articolo e nell'articolo [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Classi Keyboard e Mouse
 Oltre alle API l'input per le classi di elementi di base, il <xref:System.Windows.Input.Keyboard> classi e <xref:System.Windows.Input.Mouse> classi forniscono API aggiuntive per l'uso di input del mouse e tastiera.

 Esempi di input dell'API per il <xref:System.Windows.Input.Keyboard> classe sono il <xref:System.Windows.Input.Keyboard.Modifiers%2A> proprietà, che restituisce il <xref:System.Windows.Input.ModifierKeys> attualmente premuti e il <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metodo, che determina se una chiave specificata viene premuta.

 L'esempio seguente usa il <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metodo per determinare se un <xref:System.Windows.Input.Key> è nello stato premuto.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Esempi di input dell'API per il <xref:System.Windows.Input.Mouse> classe vengono <xref:System.Windows.Input.Mouse.MiddleButton%2A>, che ottiene lo stato del pulsante centrale del mouse, e <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, che ottiene l'elemento il puntatore del mouse è attualmente posizionato.

 L'esempio seguente determina se il <xref:System.Windows.Input.Mouse.LeftButton%2A> del passaggio del mouse si trova il <xref:System.Windows.Input.MouseButtonState.Pressed> dello stato.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 Il <xref:System.Windows.Input.Mouse> e <xref:System.Windows.Input.Keyboard> classi vengono analizzate più dettagliatamente nel corso dell'articolo.

### <a name="stylus-input"></a>Input dello stilo
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre supporto integrato per la <xref:System.Windows.Input.Stylus>.  Il <xref:System.Windows.Input.Stylus> è un input penna diventato comune con il [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le applicazioni possono trattare lo stilo come un mouse usando il mouse API, ma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] espone anche un'astrazione del dispositivo stilo che usa un modello analogo a tastiera e mouse.  Tutte le API correlate allo stilo contengono la parola "Stylus".

 Dal momento che lo stilo può funzionare come un mouse, le applicazioni che supportano solo l'input del mouse possono comunque ottenere automaticamente un certo livello di supporto dello stilo. Quando lo stilo viene usato in questo modo, l'applicazione può gestire l'evento dello stilo appropriato gestendo l'evento del mouse corrispondente. Inoltre, tramite l'astrazione del dispositivo stilo, sono disponibili anche servizi di livello superiore, come l'input penna.  Per altre informazioni sull'input penna, vedere [Nozioni di base sull'input penna](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Routing di eventi
 Oggetto <xref:System.Windows.FrameworkElement> può contenere altri elementi come elementi figlio nel modello di contenuto, formando un albero degli elementi.  In [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l'elemento padre può partecipare all'input diretto verso i relativi elementi figlio o agli altri discendenti mediante la gestione degli eventi. Ciò risulta particolarmente utile per la creazione di controlli a partire da controlli più piccoli, processo noto come "composizione di controlli" o "composizione". Per altre informazioni sugli alberi degli elementi e sulla loro relazione con le route degli eventi, vedere [Strutture ad albero in WPF](trees-in-wpf.md).

 Il routing degli eventi è il processo di inoltro degli eventi a più elementi, in modo che un oggetto o un elemento specifico lungo la route possa offrire una risposta significativa (tramite la gestione) a un evento che potrebbe essere stato originato da un elemento diverso.  Gli eventi indirizzati usano uno dei tre meccanismi di routing indicati di seguito: diretto, bubbling e tunneling.  Nel routing diretto, l'elemento di origine è l'unico elemento che riceve la notifica e l'evento non viene indirizzato a nessun altro elemento. Tuttavia, l'evento indirizzato tramite routing diretto offre alcune funzionalità aggiuntive che sono disponibili solo per gli eventi indirizzati e non per gli eventi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard. Il bubbling viene eseguito procedendo verso l'alto nell'albero degli elementi, notificando innanzitutto l'elemento che ha originato l'evento, quindi l'elemento padre e così via.  Il tunneling parte dalla radice dell'albero degli elementi e procede verso il basso, terminando con l'elemento di origine.  Per altre informazioni sugli eventi indirizzati, vedere [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md).

 Gli eventi di input [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sono in genere a coppie, costituite da un evento di tunneling e un evento di bubbling.  Gli eventi di tunneling si distinguono da quelli di bubbling tramite il prefisso "Preview".  Ad esempio, <xref:System.Windows.Input.Mouse.PreviewMouseMove> è la versione tunneling di un evento di spostamento del mouse e <xref:System.Windows.Input.Mouse.MouseMove> è la versione di bubbling dell'evento. Questa coppia di eventi è una convenzione implementata a livello di elemento e non è una funzionalità intrinseca del sistema di eventi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Per informazioni dettagliate, vedere la sezione Eventi di input WPF in [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Gestione degli eventi di input
 Per ricevere input su un elemento, un gestore eventi deve essere associato a quel particolare evento.  In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tale associazione è semplice: è sufficiente fare riferimento al nome dell'evento come attributo dell'elemento che rimarrà in ascolto di questo evento.  Si imposta quindi il valore dell'attributo sul nome del gestore eventi definito, in base a un delegato.  Il gestore eventi deve essere scritto in codice, ad esempio c# e può essere incluso in un file code-behind.

 Gli eventi della tastiera si verificano quando il sistema operativo segnala azioni dei tasti eseguite quando lo stato attivo della tastiera è su un elemento. Gli eventi del mouse e dello stilo rientrano ciascuno in due categorie: eventi che segnalano modifiche nella posizione del puntatore rispetto all'elemento ed eventi che segnalano modifiche nello stato dei pulsanti del dispositivo.

### <a name="keyboard-input-event-example"></a>Esempio di evento di input da tastiera
 L'esempio seguente illustra una situazione di ascolto della pressione del tasto freccia SINISTRA.  Oggetto <xref:System.Windows.Controls.StackPanel> viene creato che ha un <xref:System.Windows.Controls.Button>.  Un gestore eventi per l'ascolto di pressione del tasto freccia sinistra è collegato al <xref:System.Windows.Controls.Button> istanza.

 La prima sezione dell'esempio crea il <xref:System.Windows.Controls.StackPanel> e il <xref:System.Windows.Controls.Button> e associa il gestore eventi per il <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 La seconda sezione è scritta nel codice e definisce il gestore eventi.  Quando viene premuto il tasto freccia sinistra e il <xref:System.Windows.Controls.Button> ha lo stato attivo della tastiera, il gestore viene eseguito e il <xref:System.Windows.Controls.Control.Background%2A> colore del <xref:System.Windows.Controls.Button> viene modificato.  Se viene premuto il tasto, ma non è il tasto freccia sinistra, il <xref:System.Windows.Controls.Control.Background%2A> color del <xref:System.Windows.Controls.Button> viene nuovamente impostato su colore iniziale.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Esempio di evento di input del mouse
 Nell'esempio seguente, il <xref:System.Windows.Controls.Control.Background%2A> colore di un <xref:System.Windows.Controls.Button> viene modificato quando il puntatore del mouse viene spostato il <xref:System.Windows.Controls.Button>.  Il <xref:System.Windows.Controls.Control.Background%2A> colore viene ripristinato quando il mouse lascia il <xref:System.Windows.Controls.Button>.

 La prima sezione dell'esempio crea il <xref:System.Windows.Controls.StackPanel> e il <xref:System.Windows.Controls.Button> controllano e associa i gestori eventi per il <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> eventi per il <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 La seconda sezione dell'esempio è scritta nel codice e definisce i gestori eventi.  Quando il mouse viene spostato il <xref:System.Windows.Controls.Button>, il <xref:System.Windows.Controls.Control.Background%2A> colori del <xref:System.Windows.Controls.Button> viene modificato in <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Quando il mouse lascia il <xref:System.Windows.Controls.Button>, il <xref:System.Windows.Controls.Control.Background%2A> colore della <xref:System.Windows.Controls.Button> viene nuovamente impostato su <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Input di testo
 Il <xref:System.Windows.ContentElement.TextInput> evento consente di rimanere in ascolto dell'input di testo in modo indipendente dal dispositivo. La tastiera è il mezzo principale per l'immissione di testo, ma anche i comandi vocali, il riconoscimento della grafia e altri dispositivi di input possono generare input di testo.

 Per l'input di tastiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] invia prima un appropriato <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> eventi. Se non vengono gestiti gli eventi e la chiave è testo anziché (una chiave di controllo, ad esempio le frecce direzionali) o tasti funzione, un <xref:System.Windows.ContentElement.TextInput> viene generato l'evento.  Non ci sono sempre un semplice mapping uno a uno tra <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> e <xref:System.Windows.ContentElement.TextInput> eventi perché più sequenze di tasti può generare un singolo carattere di input di testo e singolo tasto può generare più caratteri stringhe.  Ciò si verifica soprattutto con lingue come il cinese, il giapponese e il coreano che usano [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] per generare le migliaia di caratteri possibili nei corrispondenti alfabeti.

 Quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] invia un <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> evento <xref:System.Windows.Input.KeyEventArgs.Key%2A> è impostato su <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> se le sequenze di tasti possono diventare parte di un <xref:System.Windows.ContentElement.TextInput> evento (se ALT + S è premuto, ad esempio). Ciò consente al codice in un <xref:System.Windows.ContentElement.KeyDown> gestore dell'evento per verificare la presenza <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> e, se trovato, lasciare l'elaborazione per il gestore di generato successivamente <xref:System.Windows.ContentElement.TextInput> evento. In questi casi, le varie proprietà del <xref:System.Windows.Input.TextCompositionEventArgs> argomento può essere utilizzato per determinare le pressioni di tasti originali. Analogamente, se un' [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] è attivo, <xref:System.Windows.Input.Key> ha il valore di <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, e <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> fornisce la pressione di tasto o le sequenze di tasti originali.

 L'esempio seguente definisce un gestore per il <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventi e un gestore per il <xref:System.Windows.UIElement.KeyDown> evento.

 Il primo segmento di codice o markup crea l'interfaccia utente.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Il secondo segmento di codice contiene i gestori eventi.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Poiché gli eventi di input intercetterà la route dell'evento, il <xref:System.Windows.Controls.StackPanel> riceve l'input indipendentemente dall'elemento che ha lo stato attivo della tastiera. Il <xref:System.Windows.Controls.TextBox> controllo riceve una notifica prima e la `OnTextInputKeyDown` gestore viene chiamato solo se il <xref:System.Windows.Controls.TextBox> non ha gestito l'input. Se il <xref:System.Windows.UIElement.PreviewKeyDown> eventi viene usato invece del <xref:System.Windows.UIElement.KeyDown> evento, il `OnTextInputKeyDown` gestore viene chiamato per primo.

 In questo esempio la logica di gestione viene scritta due volte, una per CTRL+O e una per l'evento Click del pulsante. È possibile semplificare questa operazione usando i comandi, invece di gestire direttamente gli eventi di input.  I comandi vengono illustrati in questo articolo e in [Cenni preliminari sull'esecuzione di comandi](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Tocco e manipolazione
 Il nuovo hardware e le nuove API del sistema operativo Windows 7 consentono alle applicazioni di ricevere contemporaneamente input da più tocchi. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consente alle applicazioni di rilevare il tocco e rispondere in un modo simile alle risposte ad altri tipi di input, ad esempio di mouse o tastiera, generando eventi quando si verifica il tocco.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] espone due tipi di eventi quando si verifica il tocco: eventi di tocco ed eventi di manipolazione. Gli eventi di tocco forniscono dati non elaborati relativi a ogni dito appoggiato su un touchscreen e al suo movimento. Gli eventi di manipolazione interpretano l'input come azioni specifiche. Questa sezione illustra entrambi i tipi di eventi.

### <a name="prerequisites"></a>Prerequisiti
 Per sviluppare un'applicazione che risponde al tocco, sono necessari i componenti seguenti.

- Visual Studio 2010.

- Windows 7.

- Un dispositivo, ad esempio un touchscreen, che supporta Windows Touch.

### <a name="terminology"></a>Terminologia
 Quando si parla di tocco, vengono usati i termini seguenti.

- **Tocco** è un tipo di input dell'utente riconosciuto da Windows 7. In genere, il tocco viene generato appoggiando le dita su uno schermo sensibile al tocco. Si noti che dispositivi come i touchpad, diffusi sui computer portatili, non supportano il tocco se il dispositivo si limita a convertire la posizione e il movimento del dito come input del mouse.

- **Multitocco** è un tocco che si verifica in più punti contemporaneamente. Windows 7 e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supportano l'input multitocco. Ogni volta che il tocco viene trattato nella documentazione relativa a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], i concetti illustrati si applicano al multitocco.

- Una **manipolazione** si verifica quando il tocco viene interpretato come azione fisica applicata a un oggetto. In [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gli eventi di manipolazione interpretano l'input come una manipolazione di traslazione, espansione o rotazione.

- Un `touch device` rappresenta un dispositivo che produce un input tocco, ad esempio un singolo dito su un touchscreen.

### <a name="controls-that-respond-to-touch"></a>Controlli che rispondono al tocco
 È possibile scorrere i controlli seguenti trascinando un dito attraverso il controllo, se c'è contenuto non visualizzato.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 Il <xref:System.Windows.Controls.ScrollViewer> definisce il <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> che consente di specificare se Panoramica tramite tocco è abilitata orizzontalmente, verticalmente, entrambe o nessuna delle due proprietà associata. Il <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> proprietà specifica la rapidità di rallentamento dello scorrimento quando l'utente solleva il dito dal touchscreen. Il <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> proprietà associata specifica il rapporto dell'offset per convertire l'offset di manipolazione di scorrimento.

### <a name="touch-events"></a>Eventi di tocco
 Le classi di base <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, e <xref:System.Windows.ContentElement>, definire gli eventi che è possibile sottoscrivere in modo che l'applicazione risponda al tocco. Gli eventi di tocco sono utili quando l'applicazione interpreta il tocco come qualcosa di diverso rispetto alla manipolazione di un oggetto. Un'applicazione che consente a un utente di disegnare con un dito o con più dita deve ad esempio sottoscrivere gli eventi di tocco.

 Tutte tre le classi definiscono gli eventi seguenti, che hanno un comportamento simile, indipendentemente dalla classe che li definisce.

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 Analogamente agli eventi di tastiera e mouse, gli eventi di tocco sono eventi indirizzati. Gli eventi che iniziano con `Preview` sono eventi di tunneling e gli eventi che iniziano con `Touch` sono eventi di bubbling. Per altre informazioni sugli eventi indirizzati, vedere [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md). Quando si gestiscono questi eventi, è possibile ottenere la posizione dell'input, rispetto a qualsiasi elemento chiamando il <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> o <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> (metodo).

 Per comprendere l'interazione tra gli eventi di tocco, si consideri lo scenario in cui un utente appoggia un dito su un elemento, muove il dito all'interno dell'elemento e quindi solleva il dito dall'elemento. La figura seguente illustra l'esecuzione degli eventi di bubbling. Gli eventi di tunneling vengono omessi per maggiore semplicità.

 ![La sequenza di eventi di tocco. ](./media/ndp-touchevents.png "NDP_TouchEvents") eventi di tocco

 L'elenco seguente descrive la sequenza degli eventi della figura precedente.

1. Il <xref:System.Windows.UIElement.TouchEnter> evento si verifica una volta quando l'utente appoggia un dito sull'elemento.

2. Il <xref:System.Windows.UIElement.TouchDown> evento si verifica una volta.

3. Il <xref:System.Windows.UIElement.TouchMove> evento si verifica più volte quando l'utente sposta il dito all'interno dell'elemento.

4. Il <xref:System.Windows.UIElement.TouchUp> evento si verifica una volta quando l'utente solleva il dito dall'elemento.

5. Il <xref:System.Windows.UIElement.TouchLeave> evento si verifica una volta.

 Quando vengono usate più di due dita, gli eventi si verificano per ogni dito.

### <a name="manipulation-events"></a>Eventi di manipolazione
 Per i casi in cui un'applicazione consente all'utente di modificare un oggetto, il <xref:System.Windows.UIElement> classe definisce gli eventi di manipolazione. A differenza degli eventi di tocco che segnalano semplicemente la posizione del tocco, gli eventi di manipolazione segnalano come può essere interpretato l'input. Ci sono tre tipi di manipolazioni: traslazione, espansione e rotazione. L'elenco seguente descrive come richiamare i tre tipi di manipolazioni.

- Appoggiare un dito su un oggetto e muovere il dito sul touchscreen per richiamare una manipolazione di traslazione. Ciò comporta in genere lo spostamento dell'oggetto.

- Appoggiare due dita su un oggetto e avvicinare o allontanare le dita tra loro per richiamare una manipolazione di espansione. Ciò comporta in genere il ridimensionamento dell'oggetto.

- Appoggiare due dita su un oggetto e ruotare le dita una attorno all'altra per richiamare una manipolazione di rotazione. Ciò comporta in genere la rotazione dell'oggetto.

 Si possono verificare più tipi di manipolazioni contemporaneamente.

 Quando gli oggetti rispondono alle manipolazioni, si può fare in modo che sembrino avere un'inerzia. In questo modo, gli oggetti possono simulare il mondo fisico. Ad esempio se si spinge un libro su un tavolo con sufficiente forza, il libro continuerà a muoversi anche dopo che lo si lascia. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consente di simulare questo comportamento generando eventi di manipolazione dopo che le dita dell'utente rilasciano l'oggetto.

 Per informazioni su come creare un'applicazione che consente all'utente di spostare, ridimensionare e ruotare un oggetto, vedere [procedura dettagliata: Creazione della prima applicazione Touch](walkthrough-creating-your-first-touch-application.md).

 Il <xref:System.Windows.UIElement> definisce gli eventi di manipolazione seguenti.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Per impostazione predefinita, un <xref:System.Windows.UIElement> non riceve questi eventi di manipolazione. Per ricevere gli eventi di manipolazione in un <xref:System.Windows.UIElement>, impostare <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> a `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Percorso di esecuzione degli eventi di manipolazione
 Si consideri uno scenario in cui un utente "lancia" un oggetto. L'utente appoggia un dito sull'oggetto, sposta il dito sul touchscreen per un breve tratto e quindi solleva il dito mentre l'oggetto si sta muovendo. Il risultato di questa azione è che l'oggetto si muoverà sotto il dito dell'utente e continuerà a muoversi dopo che l'utente ha sollevato il dito.

 La figura seguente mostra il percorso di esecuzione degli eventi di manipolazione, con informazioni importanti relative a ogni evento.

 ![La sequenza di eventi di manipolazione. ](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") gli eventi di manipolazione

 L'elenco seguente descrive la sequenza degli eventi della figura precedente.

1. Il <xref:System.Windows.UIElement.ManipulationStarting> evento si verifica quando l'utente mette un dito sull'oggetto. Tra le altre cose, questo evento consente di impostare il <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> proprietà. Negli eventi successivi, la posizione della manipolazione sarà relativa al <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. Negli eventi diversi da <xref:System.Windows.UIElement.ManipulationStarting>, questa proprietà è di sola lettura, pertanto la <xref:System.Windows.UIElement.ManipulationStarting> eventi sono l'unica volta che è possibile impostare questa proprietà.

2. Il <xref:System.Windows.UIElement.ManipulationStarted> l'evento. Questo evento segnala l'origine della manipolazione.

3. Il <xref:System.Windows.UIElement.ManipulationDelta> evento si verifica più volte quando sposta le dita un utente su un touchscreen. Il <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> proprietà del <xref:System.Windows.Input.ManipulationDeltaEventArgs> classe segnala se la manipolazione viene interpretata come movimento, espansione o traslazione. In questo contesto si esegue la maggior parte del lavoro di manipolazione di un oggetto.

4. Il <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento si verifica quando le dita dell'utente perdono il contatto con l'oggetto. Questo evento consente di specificare la decelerazione delle manipolazioni durante l'inerzia. In questo modo, l'oggetto può emulare spazi fisici o attribuiti diversi, se si desidera. Si supponga, ad esempio, che l'applicazione includa due oggetti che rappresentano elementi nel mondo fisico e che uno di questi sia più pesante dell'altro. È possibile fare in modo che l'oggetto più pesante rallenti più velocemente rispetto a quello più leggero.

5. Il <xref:System.Windows.UIElement.ManipulationDelta> evento si verifica più volte durante l'inerzia. Si noti che questo evento si verifica quando le dita dell'utente si muovono sul touchscreen e quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simula l'inerzia. In altre parole, <xref:System.Windows.UIElement.ManipulationDelta> si verifica prima e dopo il <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento. Il <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> proprietà report se il <xref:System.Windows.UIElement.ManipulationDelta> evento si verifica durante l'inerzia, pertanto è possibile controllare la proprietà e azioni diverse, a seconda del valore.

6. Il <xref:System.Windows.UIElement.ManipulationCompleted> evento si verifica quando termina la manipolazione e dell'inerzia. Vale a dire, dopo tutti i <xref:System.Windows.UIElement.ManipulationDelta> si verificano eventi, il <xref:System.Windows.UIElement.ManipulationCompleted> evento viene generato per segnalare che la modifica è stata completata.

 Il <xref:System.Windows.UIElement> definisce inoltre la <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> evento. Questo evento si verifica quando la <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> metodo viene chiamato nel <xref:System.Windows.UIElement.ManipulationDelta> evento. Il <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> evento consente alle applicazioni o componenti fornire un feedback visivo quando un oggetto colpisce un confine. Ad esempio, il <xref:System.Windows.Window> classe gestisce il <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> causano la finestra di spostare leggermente quando si incontra il bordo dell'evento.

 È possibile annullare la manipolazione chiamando il <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metodo negli argomenti dell'evento in qualsiasi evento di manipolazione eccetto <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> evento. Quando si chiama <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, gli eventi di manipolazione non vengono più generati e si verificano gli eventi del mouse per il tocco. La tabella seguente descrive la relazione tra il momento in cui viene annullata la manipolazione e gli eventi del mouse che si verificano.

|Evento su cui viene chiamato il metodo Cancel|Eventi del mouse che si verificano per l'input già avvenuto|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> e <xref:System.Windows.UIElement.ManipulationStarted>|Eventi di pressione del pulsante del mouse.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Eventi di pressione del pulsante e di spostamento del mouse.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> e <xref:System.Windows.UIElement.ManipulationCompleted>|Eventi di pressione e rilascio del pulsante e di spostamento del mouse.|

 Si noti che se si chiama <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> quando la manipolazione è nell'inerzia, il metodo restituisce `false` e l'input non genera eventi del mouse.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Relazione tra eventi di tocco e di manipolazione
 Oggetto <xref:System.Windows.UIElement> può sempre ricevere eventi di tocco. Quando la <xref:System.Windows.UIElement.IsManipulationEnabled%2A> è impostata su `true`, un <xref:System.Windows.UIElement> può ricevere eventi di tocco e di manipolazione.  Se il <xref:System.Windows.UIElement.TouchDown> evento non è gestito (vale a dire, il <xref:System.Windows.RoutedEventArgs.Handled%2A> è di proprietà `false`), la logica di manipolazione acquisisce il tocco per l'elemento e genera gli eventi di manipolazione. Se il <xref:System.Windows.RoutedEventArgs.Handled%2A> è impostata su `true` nel <xref:System.Windows.UIElement.TouchDown> evento, la logica di manipolazione non genera eventi di manipolazione. La figura seguente mostra la relazione tra eventi di tocco ed eventi di manipolazione.

 ![Relazione tra gli eventi di tocco e manipolazione](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") gli eventi di tocco e manipolazione

 L'elenco seguente descrive la relazione tra gli eventi di tocco e gli eventi di manipolazione illustrati nella figura precedente.

- Quando il primo dispositivo touch genera un <xref:System.Windows.UIElement.TouchDown> eventi in un <xref:System.Windows.UIElement>, la logica di manipolazione chiama il <xref:System.Windows.UIElement.CaptureTouch%2A> metodo, che genera il <xref:System.Windows.UIElement.GotTouchCapture> evento.

- Quando la <xref:System.Windows.UIElement.GotTouchCapture> si verifica, la logica di manipolazione chiama il <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> metodo, che genera il <xref:System.Windows.UIElement.ManipulationStarting> evento.

- Quando la <xref:System.Windows.UIElement.TouchMove> si verificano gli eventi, la logica di manipolazione genera il <xref:System.Windows.UIElement.ManipulationDelta> eventi che si verificano prima il <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento.

- Quando l'ultimo dispositivo a tocco sull'elemento genera il <xref:System.Windows.UIElement.TouchUp> evento, la logica di manipolazione genera il <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento.

<a name="focus"></a>
## <a name="focus"></a>Stato attivo
 Ci sono due concetti principali relativi allo stato attivo in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: lo stato attivo della tastiera e lo stato attivo logico.

### <a name="keyboard-focus"></a>Stato attivo della tastiera
 Lo stato attivo della tastiera fa riferimento all'elemento che riceve l'input dalla tastiera.  Su un desktop può esserci un solo elemento con lo stato attivo della tastiera.  Nelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l'elemento con lo stato attivo della tastiera avrà <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> impostato su `true`.  Il metodo statico <xref:System.Windows.Input.Keyboard> metodo <xref:System.Windows.Input.Keyboard.FocusedElement%2A> restituisce l'elemento che attualmente ha lo stato attivo della tastiera.

 Lo stato attivo della tastiera può essere ottenuto spostandosi con TAB su un elemento o facendo clic con il mouse su determinati elementi, ad esempio un <xref:System.Windows.Controls.TextBox>.  Lo stato attivo della tastiera può anche essere ottenuto a livello di codice usando il <xref:System.Windows.Input.Keyboard.Focus%2A> metodo su di <xref:System.Windows.Input.Keyboard> classe.  <xref:System.Windows.Input.Keyboard.Focus%2A> è stato effettuato un tentativo di assegnare lo stato attivo della tastiera di elemento specificato.  L'elemento restituito da <xref:System.Windows.Input.Keyboard.Focus%2A> è l'elemento che attualmente ha lo stato attivo della tastiera.

 Affinché un elemento ottenga lo stato attivo della tastiera la <xref:System.Windows.UIElement.Focusable%2A> proprietà e i <xref:System.Windows.UIElement.IsVisible%2A> delle proprietà devono essere impostate su **true**.  Alcune classi, ad esempio <xref:System.Windows.Controls.Panel>, hanno <xref:System.Windows.UIElement.Focusable%2A> impostata su `false` per impostazione predefinita; pertanto, potrebbe essere necessario impostare questa proprietà su `true` se si vuole che l'elemento sia in grado di ottenere lo stato attivo.

 L'esempio seguente usa <xref:System.Windows.Input.Keyboard.Focus%2A> impostare lo stato attivo della tastiera su un <xref:System.Windows.Controls.Button>.  La posizione consigliata per impostare lo stato attivo iniziale in un'applicazione è il <xref:System.Windows.FrameworkElement.Loaded> gestore dell'evento.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Per altre informazioni sullo stato attivo della tastiera, vedere [Cenni preliminari sullo stato attivo](focus-overview.md).

### <a name="logical-focus"></a>Stato attivo logico
 Lo stato attivo logico fa riferimento al <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> nell'ambito di stato attivo.  In un'applicazione possono esserci più elementi con lo stato attivo logico, ma in un determinato ambito di stato attivo può esserci un solo elemento con lo stato attivo logico.

 Ambito di stato attivo è un elemento contenitore che tiene traccia del <xref:System.Windows.Input.FocusManager.FocusedElement%2A> nel relativo ambito.  Quando lo stato attivo lascia un ambito di stato attivo, l'elemento con lo stato attivo perde lo stato attivo della tastiera, ma mantiene quello logico.  Quando lo stato attivo torna nell'ambito di stato attivo, l'elemento con lo stato attivo ottiene nuovamente lo stato attivo della tastiera.  In questo modo, lo stato attivo della tastiera può essere passato tra più ambiti, ma l'elemento con lo stato attivo in un determinato ambito rimane sicuramente tale al ritorno dello stato attivo.

 Un elemento può essere convertito in un ambito di stato attivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] impostando la <xref:System.Windows.Input.FocusManager> proprietà associata <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> al `true`, o nel codice impostando la proprietà associata tramite la <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> (metodo).

 Nell'esempio seguente viene eseguita una <xref:System.Windows.Controls.StackPanel> ambito di stato attivo impostando il <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> proprietà associata.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Le classi nello [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] quali sono gli ambiti di stato attivo per impostazione predefinita viene <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, e <xref:System.Windows.Controls.ContextMenu>.

 Un elemento con lo stato attivo della tastiera avrà anche lo stato attivo logico per l'ambito che a cui appartiene; Pertanto, l'impostazione dello stato attivo su un elemento con la <xref:System.Windows.Input.Keyboard.Focus%2A> metodo su di <xref:System.Windows.Input.Keyboard> classe o le classi di elementi di base tenterà di assegnare l'elemento lo stato attivo della tastiera e lo stato attivo logico.

 Per determinare l'elemento con un ambito, usare <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Per modificare l'elemento con lo stato attivo per un ambito dello stato attivo, usare <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Per altre informazioni sullo stato attivo logico, vedere [Cenni preliminari sullo stato attivo](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Posizione del mouse
 Il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] input API fornisce informazioni utili relativamente agli spazi di coordinate.  Ad esempio, la coordinata `(0,0)` rappresenta la coordinata superiore sinistra, ma di quale elemento dell'albero? Si tratta dell'elemento che costituisce la destinazione dell'input? O dell'elemento a cui è associato il gestore eventi? Oppure di qualche altro elemento? Per evitare confusione, il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] input API è necessario specificare il frame di riferimento quando si lavora con le coordinate ottenute tramite il mouse. Il <xref:System.Windows.Input.Mouse.GetPosition%2A> metodo restituisce la coordinata del puntatore del mouse relativa all'elemento specificato.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Mouse Capture
 I dispositivi di tipo mouse hanno una caratteristica modale specifica nota come mouse capture. Tale caratteristica viene usata per mantenere uno stato di input di transizione all'avvio di un'operazione di trascinamento della selezione, in modo che le altre operazioni che riguardano la posizione su schermo nominale del puntatore del mouse non vengano necessariamente eseguite. Durante il trascinamento, l'utente non può fare clic senza interrompere il trascinamento della selezione, quindi la maggior parte dei segnali di passaggio del mouse risulterà inappropriata quando l'origine del trascinamento mantiene lo stato mouse capture. Il sistema di input espone le API in grado di determinare lo stato mouse capture, nonché API che possono forzare l'acquisizione del mouse in un elemento specifico o cancellare lo stato mouse capture. Per altre informazioni sulle operazioni di trascinamento della selezione, vedere [Cenni preliminari sul trascinamento della selezione](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Comandi
 I comandi consentono la gestione dell'input a un livello più semantico rispetto all'input dei dispositivi.  I comandi sono semplici direttive, come `Cut`, `Copy`, `Paste` o `Open`.  I comandi sono utili per centralizzare la logica di comando.  Lo stesso comando potrebbe essere possibile accedere da un <xref:System.Windows.Controls.Menu>via un <xref:System.Windows.Controls.ToolBar>, o tramite un tasto di scelta rapida. I comandi forniscono anche un meccanismo per disabilitare i controlli quando il comando non è più disponibile.

 <xref:System.Windows.Input.RoutedCommand> è il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementazione di <xref:System.Windows.Input.ICommand>.  Quando un <xref:System.Windows.Input.RoutedCommand> viene eseguita, un' <xref:System.Windows.Input.CommandManager.PreviewExecuted> e un <xref:System.Windows.Input.CommandManager.Executed> sulla destinazione del comando, il tunneling e bubbling attraverso l'albero degli elementi come altri input vengono generati eventi.  Se non è impostata una destinazione del comando, questa sarà rappresentata dall'elemento con lo stato attivo della tastiera.  La logica che esegue il comando è associata a un <xref:System.Windows.Input.CommandBinding>.  Quando un <xref:System.Windows.Input.CommandManager.Executed> evento raggiunge una <xref:System.Windows.Input.CommandBinding> per quel comando specifico, il <xref:System.Windows.Input.ExecutedRoutedEventHandler> sul <xref:System.Windows.Input.CommandBinding> viene chiamato.  Il gestore esegue l'azione del comando.

 Per altre informazioni sui comandi, vedere [Cenni preliminari sull'esecuzione di comandi](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornisce una libreria di comandi comuni che è costituito <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, e <xref:System.Windows.Documents.EditingCommands>, oppure è possibile definire il proprio.

 Nell'esempio seguente viene illustrato come configurare un <xref:System.Windows.Controls.MenuItem> in modo che quando si fa clic su di esso venga richiamato il <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando le <xref:System.Windows.Controls.TextBox>, supponendo che il <xref:System.Windows.Controls.TextBox> ha lo stato attivo della tastiera.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Per altre informazioni sui comandi in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vedere [Cenni preliminari sull'esecuzione di comandi](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Sistema di input ed elementi di base
 Input degli eventi, ad esempio gli eventi associati definiti per il <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, e <xref:System.Windows.Input.Stylus> classi sono generate dal sistema di input e inserite in una determinata posizione nel modello a oggetti basato sull'hit testing di struttura ad albero visuale in fase di esecuzione.

 Tutti gli eventi che <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, e <xref:System.Windows.Input.Stylus> definite come un evento associato viene anche esposto nuovamente dalle classi di elementi di base <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> come nuovo evento indirizzato. Gli eventi indirizzati degli elementi di base vengono generati da classi che gestiscono l'evento associato originale e riutilizzano i dati dell'evento.

 Quando l'evento di input viene associato a un particolare elemento di origine tramite l'implementazione dell'evento di input dei relativi elementi di base, può essere indirizzato lungo la parte restante della route di un evento basata su una combinazione di oggetti albero logico e struttura ad albero visuale ed essere gestito dal codice dell'applicazione.  In generale, è preferibile gestire questi eventi di input correlati ai dispositivi usando gli eventi indirizzati sul <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement>, in quanto è possibile usare più intuitiva sintassi del gestore eventi sia in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e nel codice. È possibile scegliere di gestire invece l'evento associato che ha avviato il processo, ma potrebbero sorgere diversi problemi: l'evento associato potrebbe essere contrassegnato come gestito dalla gestione della classe dell'elemento di base, per cui potrebbe essere necessario usare i metodi della funzione di accesso invece della sintassi dell'evento vera e propria per associare i gestori per gli eventi associati.

<a name="whats_next"></a>
## <a name="whats-next"></a>Argomenti successivi
 A questo punto si conoscono diverse tecniche per la gestione dell'input in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Si dovrebbe anche avere una conoscenza più approfondita dei vari tipi di eventi di input e dei meccanismi degli eventi indirizzati usati in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Sono disponibili risorse aggiuntive che illustrano più dettagliatamente gli elementi del framework [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e il routing degli eventi. Per altre informazioni generali, vedere [Cenni preliminari sull'esecuzione di comandi](commanding-overview.md), [Cenni preliminari sullo stato attivo](focus-overview.md), [Cenni preliminari sugli elementi di base](base-elements-overview.md), [Strutture ad albero in WPF](trees-in-wpf.md) e [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica sullo stato attivo](focus-overview.md)
- [Panoramica sull'esecuzione di comandi](commanding-overview.md)
- [Cenni preliminari sugli eventi indirizzati](routed-events-overview.md)
- [Cenni preliminari sugli elementi di base](base-elements-overview.md)
- [Proprietà](properties-wpf.md)
