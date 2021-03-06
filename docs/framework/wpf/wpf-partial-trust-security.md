---
title: Sicurezza con attendibilità parziale in WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 907c1f02e07c60ac38c8e09e94fc96ae2573e97c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455312"
---
# <a name="wpf-partial-trust-security"></a>Sicurezza con attendibilità parziale in WPF
<a name="introduction"></a>I n generale, sarebbe opportuno limitare l'accesso diretto alle risorse critiche del sistema da parte delle applicazioni Internet in modo da impedire qualsiasi danno. Per impostazione predefinita, i linguaggi di scripting lato client e HTML non sono in grado di accedere alle risorse di sistema critiche. Poiché le applicazioni ospitate da browser Windows Presentation Foundation (WPF) possono essere avviate dal browser, devono essere conformi a un set di restrizioni simile. Per applicare queste restrizioni, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] si basa sia sulla sicurezza dall'accesso di codice (CAS) che su ClickOnce (vedere [strategia di sicurezza di WPF-sicurezza della piattaforma](wpf-security-strategy-platform-security.md)). Per impostazione predefinita, le applicazioni ospitate da browser richiedono il set di autorizzazioni dell'area Internet, indipendentemente dal fatto che vengano avviate da Internet, dall'Intranet locale o dal computer locale. Le applicazioni in esecuzione con un set di autorizzazioni incompleto vengono definite applicazioni in esecuzione con attendibilità parziale.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] offre un'ampia gamma di supporto per garantire che il maggior numero possibile di funzionalità possa essere usato in modo sicuro con attendibilità parziale e con le autorità di certificazione, fornisce supporto aggiuntivo per la programmazione parzialmente attendibile.  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
- [Supporto con attendibilità parziale della funzionalità WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programmazione con attendibilità parziale](#Partial_Trust_Programming)  
  
- [Gestione delle autorizzazioni](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Supporto con attendibilità parziale della funzionalità WPF  
 Nella tabella seguente sono elencate le funzionalità di alto livello di Windows Presentation Foundation (WPF) che possono essere utilizzate in modo sicuro entro i limiti del set di autorizzazioni dell'area Internet.  
  
 Tabella 1: Funzionalità WPF sicure in attendibilità parziale  
  
|Area funzionalità|Funzionalità|  
|------------------|-------------|  
|Generale|Finestra del browser<br /><br /> Accesso al sito di origine<br /><br /> IsolatedStorage (limite di 512 KB)<br /><br /> Provider UIAutomation<br /><br /> Esecuzione di comandi<br /><br /> Input Method Editor (IME)<br /><br /> Stilo e input penna da tablet<br /><br /> Trascinamento della selezione simulato mediante eventi di acquisizione e spostamento del mouse<br /><br /> OpenFileDialog<br /><br /> Deserializzazione XAML (tramite XamlReader.Load)|  
|Integrazione Web|Finestra di dialogo di download del browser<br /><br /> Navigazione di primo livello avviata dall'utente<br /><br /> Collegamenti mailto:<br /><br /> Parametri URI (Uniform Resource Identifier)<br /><br /> HTTPWebRequest<br /><br /> Contenuto WPF ospitato in IFRAME<br /><br /> Hosting di pagine HTML dello stesso sito usando Frame<br /><br /> Hosting di pagine HTML dello stesso sito usando WebBrowser<br /><br /> Servizi Web (ASMX)<br /><br /> Servizi Web (mediante Windows Communication Foundation)<br /><br /> Scripting<br /><br /> Document Object Model (DOM)|  
|Elementi visivi|2D e 3D<br /><br /> Animazione<br /><br /> Elementi multimediali (sito di origine e tra domini)<br /><br /> Immagini/Audio/Video|  
|Lettura|FlowDocument<br /><br /> Documenti XPS<br /><br /> Tipi di carattere incorporati e di sistema<br /><br /> Caratteri CFF e TrueType|  
|Modifica|Controllo ortografico<br /><br /> RichTextBox<br /><br /> Supporto Appunti per testo non crittografato e input penna<br /><br /> Operazione Incolla avviata dall'utente<br /><br /> Copia di contenuto selezionato|  
|Controlli|Controlli generali|  
  
 Questa tabella illustra le funzionalità di [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] a livello generale. Per informazioni più dettagliate, il Windows SDK documenta le autorizzazioni richieste da ogni membro nel [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Inoltre, per le funzionalità seguenti sono disponibili informazioni più dettagliate sull'esecuzione in situazioni di attendibilità parziale, con alcune considerazioni speciali.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (vedere [Cenni preliminari su XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Popup (vedere <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Trascinamento della selezione (vedere [Cenni preliminari sul trascinamento della selezione](./advanced/drag-and-drop-overview.md)).  
  
- Appunti (vedere <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Creazione di immagini (vedere <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Serializzazione (vedere <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Finestra di dialogo Apri file (vedere <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 Nella tabella seguente vengono descritte le funzionalità di [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] non sicure per l'esecuzione entro i limiti del set di autorizzazioni dell'area Internet.  
  
 Tabella 2: Funzionalità WPF non sicure in attendibilità parziale  
  
|Area funzionalità|Funzionalità|  
|------------------|-------------|  
|Generale|Finestra (finestre e finestre di dialogo definite dall'applicazione)<br /><br /> SaveFileDialog<br /><br /> File system<br /><br /> Accesso al Registro di sistema<br /><br /> Trascinamento e rilascio<br /><br /> Serializzazione XAML (mediante XamlWriter.Save)<br /><br /> Client UIAutomation<br /><br /> Accesso alla finestra di origine (HwndHost)<br /><br /> Supporto vocale completo<br /><br /> Interoperabilità con Windows Form|  
|Elementi visivi|Effetti bitmap<br /><br /> Codifica delle immagini|  
|Modifica|Appunti RTF (Rich-Text Format)<br /><br /> Supporto XAML completo|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programmazione con attendibilità parziale  
 Per le applicazioni XBAP, il codice che supera il set di autorizzazioni predefinito avrà un comportamento diverso a seconda dell'area di sicurezza. In alcuni casi, l'utente riceverà un avviso quando tenta di installare il codice. L'utente potrà scegliere se continuare o annullare l'installazione. La tabella seguente descrive il comportamento dell'applicazione per ogni area di sicurezza e le azioni necessarie relative all'applicazione per acquisire attendibilità totale.  
  
|Area di sicurezza|Comportamento|Ottenere l'attendibilità totale|  
|-------------------|--------------|------------------------|  
|Computer locale|Attendibilità totale automatica|Nessuna azione necessaria.|  
|Intranet e siti attendibili|Richiesta di attendibilità totale|Firma dell'applicazione XBAP con un certificato in modo che l'utente veda l'origine nel prompt.|  
|Internet|Esito negativo con "Attendibilità non concessa"|Firma dell'applicazione XBAP con un certificato.|  
  
> [!NOTE]
> Il comportamento descritto nella tabella precedente è relativo alle applicazioni XBAP con attendibilità totale che non seguono il modello di distribuzione attendibile di ClickOnce.  
  
 In genere, è probabile che il codice che richiede autorizzazioni ulteriori rispetto a quelle consentite sia codice comune condiviso dalle applicazioni autonome e da quelle ospitate dal browser. CA e [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] offrono diverse tecniche per la gestione di questo scenario.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Rilevamento delle autorizzazioni tramite CAS  
 In alcune situazioni è possibile che il codice condiviso negli assembly della libreria venga utilizzato sia dalle applicazioni autonome che dalle applicazioni XBAP. In questi casi, è possibile che il codice esegua funzionalità che potrebbero richiedere un numero di autorizzazioni maggiore rispetto al set assegnato all'applicazione. L'applicazione può rilevare se dispone o meno di una determinata autorizzazione usando Microsoft .NET sicurezza del Framework. In particolare, è possibile verificare se dispone di un'autorizzazione specifica chiamando il metodo <xref:System.Security.CodeAccessPermission.Demand%2A> sull'istanza dell'autorizzazione desiderata. Questa procedura è illustrata nell'esempio seguente, in cui il codice esegue una query per verificare la disponibilità dell'autorizzazione per salvare un file sul disco locale:  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Se un'applicazione non dispone dell'autorizzazione desiderata, la chiamata a <xref:System.Security.CodeAccessPermission.Demand%2A> genererà un'eccezione di sicurezza. In caso contrario, l'autorizzazione è disponibile. `IsPermissionGranted` incapsula questo comportamento e restituisce `true` o `false` in base alle esigenze.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Riduzione normale delle prestazioni della funzionalità  
 La capacità del codice di rilevare le autorizzazioni disponibili risulta particolarmente interessante quando il codice può essere eseguito da aree diverse. Sebbene il rilevamento dell'area sia importante, è meglio fornire un'alternativa all'utente, se possibile. Ad esempio, di solito un'applicazione con attendibilità totale consente agli utenti di creare file in qualsiasi posizione, mentre un'applicazione con attendibilità parziale consente di creare file unicamente in uno spazio di archiviazione isolato. Se il codice per la creazione di un file è contenuto in un assembly condiviso da applicazioni con attendibilità totale (autonome) e applicazioni con attendibilità parziale (ospitate dal browser) e si vuole che entrambi i tipi di applicazioni consentano la creazione di file, il codice condiviso dovrà rilevare se viene eseguito in attendibilità parziale o totale prima di creare un file nel percorso appropriato. I due casi sono illustrati nel codice seguente.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 In molte situazioni è possibile trovare un'alternativa all'attendibilità parziale.  
  
 In un ambiente controllato, ad esempio una rete Intranet, è possibile installare Framework gestiti personalizzati attraverso la base client nella Global Assembly Cache (GAC). Queste librerie consentono di eseguire codice che richiede attendibilità totale ed è possibile farvi riferimento da applicazioni che sono consentite solo parzialmente attendibilità usando <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (per altre informazioni, vedere [sicurezza](security-wpf.md) e strategia di sicurezza di [WPF-sicurezza della piattaforma](wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Rilevamento host del browser  
 L'uso di CA per verificare le autorizzazioni è una tecnica adatta quando è necessario verificare l'autorizzazione per ogni singola autorizzazione. Tuttavia, tale tecnica dipende dal rilevamento di eccezioni durante la normale elaborazione, operazione che in genere non è consigliata e che può causare problemi di prestazioni. Se invece l'applicazione browser XAML (XBAP) viene eseguita solo nella sandbox dell'area Internet, è possibile usare la proprietà <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, che restituisce true per le applicazioni browser XAML (XBAPs).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> distingue solo se un'applicazione è in esecuzione in un browser, non con il set di autorizzazioni con cui viene eseguita un'applicazione.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Gestione delle autorizzazioni  
 Per impostazione predefinita, le applicazioni XBAPs vengono eseguite con attendibilità parziale (set di autorizzazioni predefinito dell'area Internet). Tuttavia, a seconda dei requisiti dell'applicazione, questo set predefinito può essere modificato. Se, ad esempio, un'applicazione XBAPs viene avviata da una rete Intranet locale, può usufruire di un set di autorizzazioni più elevato, illustrato nella tabella seguente.  
  
 Tabella 3: Autorizzazioni LocalIntranet e Internet  
  
|Autorizzazioni|Attributo|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Accesso ai server DNS|Yes|No|  
|Variabili di ambiente|Lettura|Yes|No|  
|Finestre di dialogo file|Apri|Yes|Yes|  
|Finestre di dialogo file|Senza restrizioni|Yes|No|  
|Spazio di memorizzazione isolato|Isolamento assembly in base all'utente|Yes|No|  
|Spazio di memorizzazione isolato|Isolamento sconosciuto|Yes|Yes|  
|Spazio di memorizzazione isolato|Quota utenti illimitata|Yes|No|  
|Supporti|Audio, video e immagini sicuri|Yes|Yes|  
|Stampa|Stampa predefinita|Yes|No|  
|Stampa|Stampa sicura|Yes|Yes|  
|Reflection|Emissione|Yes|No|  
|Sicurezza|Esecuzione del codice gestito|Yes|Yes|  
|Sicurezza|Asserzione autorizzazioni concesse|Yes|No|  
|Interfaccia utente|Senza restrizioni|Yes|No|  
|Interfaccia utente|Finestre di primo livello sicure|Yes|Yes|  
|Interfaccia utente|Appunti personali|Yes|Yes|  
|Web browser|Navigazione sicura dei frame in HTML|Yes|Yes|  
  
> [!NOTE]
> L'operazione di taglia e incolla, se avviata dall'utente, è consentita solo con l'attendibilità parziale.  
  
 Per aumentare il numero di autorizzazioni, è necessario modificare le impostazioni del progetto e il manifesto dell'applicazione ClickOnce. Per altre informazioni, vedere [Panoramica delle applicazioni browser XAML di WPF](./app-development/wpf-xaml-browser-applications-overview.md). Anche i seguenti documenti possono rivelarsi utili.  
  
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Sicurezza di applicazioni ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Se l'applicazione XBAP richiede l'attendibilità totale, è possibile utilizzare gli stessi strumenti per aumentare le autorizzazioni richieste. Anche se un'applicazione XBAP riceverà solo l'attendibilità totale se viene installata e avviata dal computer locale, dalla Intranet o da un URL elencato nei siti attendibili o consentiti del browser. Se l'applicazione viene installata dalla Intranet o da un sito attendibile, verrà visualizzato all'utente il prompt standard di ClickOnce con la notifica relativa alle autorizzazioni elevate. L'utente potrà scegliere se continuare o annullare l'installazione.  
  
 In alternativa, è possibile usare il modello di distribuzione attendibile di ClickOnce per una distribuzione con attendibilità totale da qualsiasi area di sicurezza. Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](/visualstudio/deployment/trusted-application-deployment-overview) e [sicurezza](security-wpf.md).  
  
## <a name="see-also"></a>Vedere anche

- [Security](security-wpf.md)
- [Strategia di sicurezza di WPF - Sicurezza della piattaforma](wpf-security-strategy-platform-security.md)
- [Strategia di sicurezza WPF - Progettazione della sicurezza](wpf-security-strategy-security-engineering.md)
