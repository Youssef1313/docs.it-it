---
title: Ambiti dei nomi XAML WPF
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917331"
---
# <a name="wpf-xaml-namescopes"></a>Ambiti dei nomi XAML WPF
Un ambito dei nomi XAML è un concetto che identifica gli oggetti definiti in XAML. I nomi in un ambito dei nomi XAML possono essere usati per stabilire relazioni tra i nomi definiti da XAML degli oggetti e i rispettivi equivalenti di istanza in un albero di oggetti. In genere gli ambiti dei nomi nel codice gestito [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vengono creati durante il caricamento degli elementi radice delle singole pagine XAML per un'applicazione XAML. I NameScope XAML come oggetto di programmazione sono definiti dall' <xref:System.Windows.Markup.INameScope> interfaccia e vengono implementati anche dalla classe <xref:System.Windows.NameScope>pratica.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Ambiti dei nomi in applicazioni XAML caricate  
 In un più ampio contesto di programmazione o informatico i concetti di programmazione includono spesso il principio di identificatore o nome univoco, che può essere usato per accedere a un oggetto. Per i sistemi che usano identificatori o nomi, l'ambito dei nomi definisce i limiti entro i quali un processo o una tecnica individuerà se è necessario un oggetto con tale nome oppure i limiti entro i quali viene applicata l'univocità dei nomi di identificazione. Questi principi generali si applicano agli ambiti dei nomi XAML. In WPF gli ambiti dei nomi XAML vengono creati nell'elemento radice per una pagina XAML quando questa viene caricata. Ogni nome specificato nella pagina XAML che inizia in corrispondenza della radice della pagina viene aggiunto a un ambito dei nomi XAML pertinente.  
  
 In XAML WPF gli elementi che sono elementi radice comuni (ad esempio <xref:System.Windows.Controls.Page>, e <xref:System.Windows.Window>) controllano sempre un ambito dei nomi XAML. Se un elemento, ad <xref:System.Windows.FrameworkElement> esempio <xref:System.Windows.FrameworkContentElement> o, è l'elemento radice della pagina nel markup, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] un processore <xref:System.Windows.Controls.Page> aggiunge <xref:System.Windows.Controls.Page> una radice in modo implicito affinché possa fornire un NameScope XAML funzionante.  
  
> [!NOTE]
> Le azioni di compilazione di WPF creano un ambito dei nomi XAML per una produzione XAML anche se non è definito alcun attributo `Name` o `x:Name` in alcun elemento nel markup [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Se si prova a usare lo stesso nome due volte in un ambito dei nomi XAML, viene generata un'eccezione. Per codice XAML WPF che include code-behind e che fa parte di un'applicazione compilata, l'eccezione viene generata in fase di compilazione dalle azioni di compilazione di WPF, quando viene creata la classe generata per la pagina durante la compilazione iniziale del markup. Per codice XAML non compilato dal markup tramite alcuna azione di compilazione, potrebbero essere generate eccezioni correlate a problemi dell'ambito dei nomi XAML durante il caricamento di XAML. I progettisti XAML possono anche prevedere i problemi relativi all'ambito dei nomi XAML in fase di progettazione.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Aggiunta di oggetti all'albero di oggetti di runtime  
 Il momento in cui XAML viene analizzato rappresenta il momento in cui viene creato e definito un ambito dei nomi XAML WPF. Se si aggiunge un oggetto a un albero di oggetti in un momento successivo all'analisi del codice XAML che ha prodotto l'albero, un valore `Name` o `x:Name` nel nuovo oggetto non aggiorna automaticamente le informazioni in un ambito dei nomi XAML. Per aggiungere un nome per un oggetto in un NameScope XAML WPF dopo il caricamento di XAML, è necessario chiamare l'implementazione appropriata <xref:System.Windows.Markup.INameScope.RegisterName%2A> di nell'oggetto che definisce l'ambito dei nomi XAML, che in genere è la radice della pagina XAML. Se il nome non è registrato, non è possibile fare riferimento all'oggetto aggiunto tramite un metodo come <xref:System.Windows.FrameworkElement.FindName%2A>e non è possibile usare tale nome per la destinazione dell'animazione.  
  
 Lo scenario più comune per gli sviluppatori di applicazioni è che verrà <xref:System.Windows.FrameworkElement.RegisterName%2A> usato per registrare i nomi nell'ambito dei nomi XAML nella radice corrente della pagina. <xref:System.Windows.FrameworkElement.RegisterName%2A>fa parte di uno scenario importante per gli storyboard destinati a oggetti per le animazioni. Per altre informazioni, vedere [Cenni preliminari sugli storyboard](../graphics-multimedia/storyboards-overview.md).  
  
 Se si chiama <xref:System.Windows.FrameworkElement.RegisterName%2A> su un oggetto diverso dall'oggetto che definisce l'ambito dei nomi XAML, il nome viene ancora registrato nell'ambito dei nomi XAML in cui è contenuto l'oggetto chiamante, come se fosse <xref:System.Windows.FrameworkElement.RegisterName%2A> stato chiamato sull'oggetto NameScope XAML che definisce l'oggetto.  
  
### <a name="xaml-namescopes-in-code"></a>Ambiti dei nomi XAML nel codice  
 È possibile creare e quindi usare ambiti dei nomi XAML nel codice. Le API e i concetti interessati dalla creazione di ambiti dei nomi XAML sono gli stessi, anche per l'utilizzo di codice puro, perché il processore XAML per [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa questi concetti e API quando elabora il codice XAML stesso. I concetti e le API hanno prevalentemente lo scopo di trovare oggetti in base al nome all'interno di un albero di oggetti definito parzialmente o interamente in XAML.  
  
 Per le applicazioni create a livello di codice e non da codice XAML caricato, l'oggetto che definisce un ambito dei nomi <xref:System.Windows.Markup.INameScope>XAML deve implementare o <xref:System.Windows.FrameworkElement> essere <xref:System.Windows.FrameworkContentElement> una classe o derivata per supportare la creazione di un ambito dei nomi XAML nel relativo istanze.  
  
 Inoltre, per qualsiasi elemento che non viene caricato ed elaborato da un processore XAML, l'ambito dei nomi XAML per l'oggetto non viene creato o inizializzato per impostazione predefinita. È necessario creare un nuovo ambito dei nomi XAML per qualsiasi oggetto in cui si intende successivamente registrare nomi. Per creare un ambito dei nomi XAML, chiamare il <xref:System.Windows.NameScope.SetNameScope%2A> metodo statico. Specificare l'oggetto di cui sarà proprietario come `dependencyObject` parametro e una nuova <xref:System.Windows.NameScope.%23ctor%2A> chiamata al `value` costruttore come parametro.  
  
 Se l'oggetto specificato come `dependencyObject` per <xref:System.Windows.NameScope.SetNameScope%2A> non <xref:System.Windows.FrameworkElement> è un' <xref:System.Windows.Markup.INameScope> implementazione o <xref:System.Windows.FrameworkContentElement>, la chiamata <xref:System.Windows.FrameworkElement.RegisterName%2A> su qualsiasi elemento figlio non avrà alcun effetto. Se non è possibile creare in modo esplicito il nuovo ambito dei nomi XAML <xref:System.Windows.FrameworkElement.RegisterName%2A> , le chiamate a genereranno un'eccezione.  
  
 Per un esempio dell'uso di API di ambito dei nomi XAML nel codice, vedere [Definire un ambito dei nomi](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Ambiti dei nomi XAML in stili e modelli  
 Gli stili e i modelli in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettono di riutilizzare e riapplicare contenuto in modo diretto. Tuttavia, stili e modelli potrebbero includere anche elementi con nomi XAML definiti a livello del modello. Questo stesso modello potrebbe essere usato più volte in una pagina. Per questo motivo, gli stili e i modelli definiscono entrambi ambiti dei nomi XAML propri, indipendentemente dalla posizione in un albero di oggetti in cui viene applicato lo stile o il modello.  
  
 Si consideri l'esempio seguente:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Qui viene applicato lo stesso modello a due diversi pulsanti. Se i modelli non avessero ambiti dei nomi XAML discreti, il nome `TheBorder` usato nel modello causerebbe un conflitto di nomi nell'ambito dei nomi XAML. Poiché la creazione di ogni istanza del modello ha un ambito dei nomi XAML proprio, in questo esempio l'ambito dei nomi di ogni modello di cui è stata creata un'istanza contiene esattamente un solo nome.  
  
 Anche gli stili definiscono un ambito dei nomi XAML proprio, per lo più in modo che alle parti degli storyboard possano essere assegnati nomi specifici. Questi nomi permettono comportamenti specifici dei controlli destinati a elementi con questi nomi, anche se il modello è stato ridefinito come parte della personalizzazione del controllo.  
  
 A causa della presenza di ambiti dei nomi XAML separati, la ricerca di elementi denominati in un modello è più complessa rispetto all'individuazione di un elemento denominato senza modello in una pagina. Per prima cosa è necessario determinare il modello applicato, ottenendo il <xref:System.Windows.Controls.Control.Template%2A> valore della proprietà del controllo a cui è applicato il modello. Chiamare quindi la versione del modello di <xref:System.Windows.FrameworkTemplate.FindName%2A>, passando il controllo in cui è stato applicato il modello come secondo parametro.  
  
 Se si è un autore del controllo e si genera una convenzione in cui un particolare elemento denominato in un modello applicato è la destinazione per un comportamento definito dal controllo stesso, è possibile usare il <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodo dal codice di implementazione del controllo. Il <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodo è protetto, quindi solo l'autore del controllo può accedervi.  
  
 Se si lavora da un modello ed è necessario ottenere l'ambito dei nomi XAML in cui viene applicato il modello, ottenere il valore di <xref:System.Windows.FrameworkElement.TemplatedParent%2A>e quindi chiamare. <xref:System.Windows.FrameworkElement.FindName%2A> Un esempio di questa situazione è quando si scrive l'implementazione del gestore eventi in cui l'evento verrà generato da un elemento in un modello applicato.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Ambiti dei nomi XAML e API correlate ai nomi  
 <xref:System.Windows.FrameworkElement>dispone <xref:System.Windows.FrameworkElement.FindName%2A>di <xref:System.Windows.FrameworkElement.RegisterName%2A> metodi <xref:System.Windows.FrameworkElement.UnregisterName%2A> , e. Se l'oggetto in cui vengono chiamati questi metodi è proprietario di un ambito dei nomi XAML, i metodi chiamano nei metodi dell'ambito dei nomi XAML pertinente. In caso contrario, l'elemento padre viene controllato per verificare se è proprietario di un ambito dei nomi XAML e questo processo continua in modo ricorsivo fino a quando non viene trovato un ambito dei nomi XAML. A causa del comportamento del processore XAML, esiste sicuramente un ambito dei nomi XAML nella radice. <xref:System.Windows.FrameworkContentElement>ha comportamenti analoghi, ad eccezione del fatto che <xref:System.Windows.FrameworkContentElement> nessun ambito dei nomi XAML. I metodi sono presenti <xref:System.Windows.FrameworkContentElement> in in modo che le chiamate possano essere successivamente trasmesse a <xref:System.Windows.FrameworkElement> un elemento padre.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>viene utilizzato per eseguire il mapping di un nuovo ambito dei nomi XAML a un oggetto esistente. È possibile chiamare <xref:System.Windows.NameScope.SetNameScope%2A> più volte per reimpostare o cancellare l'ambito dei nomi XAML, ma questo non è un utilizzo comune. Inoltre, <xref:System.Windows.NameScope.GetNameScope%2A> non viene in genere utilizzato dal codice.  
  
### <a name="xaml-namescope-implementations"></a>Implementazioni di ambiti dei nomi XAML  
 Le classi seguenti implementano <xref:System.Windows.Markup.INameScope> direttamente:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>non usa nomi o ambiti dei nomi XAML; USA invece chiavi, perché si tratta di un'implementazione del dizionario. L'unico motivo per <xref:System.Windows.ResourceDictionary> cui <xref:System.Windows.Markup.INameScope> implementa è la possibilità di generare eccezioni al codice utente che consentono di chiarire la distinzione tra un vero e proprio <xref:System.Windows.ResourceDictionary> ambito dei nomi XAML e il modo in cui gestisce le chiavi e di assicurare che gli ambiti dei nomi XAML non vengano applicati a un <xref:System.Windows.ResourceDictionary> per elementi padre.  
  
 <xref:System.Windows.FrameworkTemplate>e <xref:System.Windows.Style> implementano <xref:System.Windows.Markup.INameScope> tramite definizioni esplicite dell'interfaccia. Le implementazioni esplicite consentono a questi ambiti dei nomi XAML di comportarsi convenzionalmente quando <xref:System.Windows.Markup.INameScope> si accede tramite l'interfaccia, ovvero come gli ambiti dei [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nomi XAML vengono comunicati dai processi interni. Tuttavia, le definizioni esplicite dell'interfaccia non fanno parte della superficie API <xref:System.Windows.FrameworkTemplate> convenzionale <xref:System.Windows.Style>di e, perché raramente è necessario chiamare <xref:System.Windows.Markup.INameScope> direttamente i <xref:System.Windows.FrameworkTemplate> metodi <xref:System.Windows.Style> in e direttamente e usare invece altre API ad esempio <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Le classi seguenti definiscono il proprio ambito dei nomi XAML, usando <xref:System.Windows.NameScope?displayProperty=nameWithType> la classe helper e connettendosi all'implementazione dell'ambito dei nomi <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> XAML tramite la proprietà associata:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Vedere anche

- [Spazi dei nomi XAML e mapping dello spazio dei nomi per XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [Direttiva x:Name](../../xaml-services/x-name-directive.md)
