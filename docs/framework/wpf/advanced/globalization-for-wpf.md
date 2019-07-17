---
title: Globalizzazione per WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 46e7d9caf0bdf0be25a4ac76e96fe04d0e131ed1
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238584"
---
# <a name="globalization-for-wpf"></a>Globalizzazione per WPF
In questo argomento introduce i problemi che è opportuno tenere presenti durante la scrittura [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applicazioni per il mercato globale. Gli elementi di programmazione di globalizzazione sono definiti nella [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] in `System.Globalization`.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizzazione XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] basa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] e sfrutta i vantaggi del supporto per la globalizzazione definito nel [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specifica. Le sezioni seguenti descrivono alcune [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funzionalità che è necessario essere consapevoli di.

<a name="char_reference"></a>
### <a name="character-references"></a>Riferimenti ai caratteri
Un riferimento a carattere offre unità di codice UTF16 del particolare [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] carattere rappresentato, decimale o esadecimale. Nell'esempio seguente illustra un riferimento a carattere decimale per l'ALFABETO COPTO COPTO o 'Ϩ':

```
&#1000;
```

Nell'esempio seguente illustra un riferimento a un carattere esadecimale. Si noti che lo ha un **x** davanti al carattere esadecimale.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Codifica
 Le codifiche supportate da [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vengono [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 e UTF-8. L'istruzione encoding è all'inizio del [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] documento. Se non esiste alcun attributo di codifica né un ordine dei byte, il parser userà il valore predefinito UTF-8. UTF-8 e UTF-16 sono i tipi di codifica preferiti. UTF-7 non è supportato. Nell'esempio seguente viene illustrato come specificare una codifica UTF-8 in un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Attributo Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] viene utilizzato [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) per rappresentare l'attributo language dell'elemento.  Per sfruttare il <xref:System.Globalization.CultureInfo> (classe), il valore dell'attributo language deve essere uno dei nomi delle impostazioni cultura predefiniti da <xref:System.Globalization.CultureInfo>. [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) è ereditabile nell'albero di elementi (in base alle regole XML, non necessariamente a causa dell'ereditarietà della proprietà di dipendenza) e il valore predefinito è una stringa vuota se non viene assegnato in modo esplicito.

 L'attributo language è molto utile per specificare le lingue regionali. Il francese, ad esempio, ha ortografia, vocabolario e pronuncia diversi in Francia, Quebec, Belgio e Svizzera. Anche il cinese, giapponese e coreano condividono punti di codice in [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ma gli ideogrammi sono diversi e usano i tipi di carattere completamente diversi.

 Quanto segue [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] riportato viene utilizzato il `fr-CA` attributo di linguaggio per specificare la lingua francese canadese.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] supporta tutte [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funzionalità, inclusi i surrogati. Fino a quando il set di caratteri può essere mappato a [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], è supportato. GB18030, ad esempio, introduce alcuni caratteri con mapping all'estensione A e B per cinese, giapponese e coreano e le coppie di surrogati, quindi è completamente supportato. Oggetto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazione può usare <xref:System.Globalization.StringInfo> per modificare le stringhe senza sapere se hanno coppie di surrogati o caratteri combinati.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Progettazione di un'interfaccia utente internazionale con XAML
 Questa sezione vengono descritte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funzionalità che è opportuno considerare quando si scrive un'applicazione.

<a name="intl_text"></a>
### <a name="international-text"></a>Testo internazionale
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] include l'elaborazione predefinita per i sistemi di scrittura di tutti i Microsoft .NET Framework è supportato.

 Sono attualmente supportati gli script seguenti:

- Arabo

- Bengali

- Devanagari

- Cirillico

- Greco

- Gujarati

- Gurmukhi

- Ebraico

- Script ideografici

- Kannada

- Lao

- Latino

- Malayalam

- Mongolo

- Odia

- Siriaco

- Tamil

- Telugu

- Thaana

- Thailandese*

- Tibetano

 *In questa versione sono supportate la visualizzazione e la modifica del testo in thailandese. L'interruzione parole non è supportata.

 Non sono attualmente supportati gli script seguenti:

- Khmer

- Antico hangul coreano

- Myanmar

- Singalese

 Supporto di motori di tutto il sistema di scrittura [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] i tipi di carattere. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] i tipi di carattere può includere il [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelle layout che consentono agli autori del tipo di carattere di progettare meglio ottimale caratteri tipografici e internazionali. Il [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelle dei layout del tipo di carattere contengono informazioni sulle sostituzioni, sul posizionamento dei glifi, giustificazione e posizionamento della linea di base, consentendo alle applicazioni di elaborazione del testo di migliorare il layout del testo.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tipi di carattere consentono la gestione dell'icona grande set mediante [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] codifica. Tale codifica consente un esteso supporto internazionale, oltre alle varianti dei glifi tipografici.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] il rendering del testo è alimentato dalle [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] tecnologia sub-pixel che supporta l'indipendenza della risoluzione. Questo migliora considerevolmente la leggibilità e consente di supportare documenti in stile rivista di qualità elevata per tutti gli script.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Layout internazionale
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un modo molto pratico per supportare layout orizzontali, bidirezionale e verticali. Nel framework di presentazione di <xref:System.Windows.FrameworkElement.FlowDirection%2A> proprietà può essere utilizzata per definire il layout. I modelli di direzione del flusso sono:

- *LeftToRight*: layout orizzontale per latino, lingue dell'Asia orientale e così via.

- *RightToLeft*: bidirezionale per arabo, ebraico e così via.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Sviluppo di applicazioni localizzabili
 Quando si scrive un'applicazione per il consumo globale, è opportuno ricordare che l'applicazione deve essere localizzabile. Gli argomenti seguenti illustrano alcune importanti considerazioni.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interfaccia utente multilingue
 Interfacce utente multilingue (MUI) è un [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] supporto per il cambio [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] da una lingua a altra. Oggetto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazione usa il modello di assembly per il supporto MUI. Un'applicazione contiene assembly indipendenti dalla lingua, ma anche assembly di risorse satellite dipendenti dalla lingua. Il punto di ingresso è un file EXE gestito nell'assembly principale.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] caricatore di risorse consente di sfruttare il [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]di resource manager per supportare la ricerca delle risorse e del fallback. Gli assembly satellite di più lingue usano lo stesso assembly principale. L'assembly di risorse che viene caricata varia a seconda di <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> del thread corrente.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interfaccia utente localizzabile
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le applicazioni utilizzano [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per definire le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consente agli sviluppatori di specificare una gerarchia di oggetti con un set di proprietà e una logica. L'uso primario di [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste nello sviluppare [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazioni ma consente di specificare una gerarchia di qualsiasi [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] oggetti. Usano la maggior parte degli sviluppatori [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] per specificare della propria applicazione [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e usare un linguaggio di programmazione come c# per rispondere all'interazione dell'utente.

 Dal punto di vista della risorsa, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file progettato per descrivere un dipendente dalla lingua [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] è un elemento risorsa e pertanto il formato di distribuzione finale deve essere localizzabile per supportare le lingue internazionali. In quanto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] non può gestire eventi molti [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applicazioni contengono blocchi di codice per eseguire questa operazione. Per altre informazioni, vedere [Cenni preliminari su XAML (WPF)](xaml-overview-wpf.md). Codice viene rimosso e compilato in file binari diversi quando un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file è suddiviso in token nel modulo BAML di XAML. Il formato BAML dei file XAML, le immagini e altri tipi di oggetti risorsa gestita vengono incorporati nell'assembly di risorse satellite, che può essere localizzato in altre lingue, o nell'assembly principale quando la localizzazione non è necessaria.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le applicazioni supportano tutte le [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] risorse tra le tabelle di stringhe, immagini e così via.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Compilazione di applicazioni localizzabili
 Localizzare significa adattare un' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a impostazioni cultura diverse. Per rendere un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazioni localizzabili, gli sviluppatori devono compilare tutte le risorse localizzabili in un assembly di risorse. L'assembly di risorse viene localizzato in lingue diverse e il code-behind Usa l'API Gestione risorse da caricare. Uno dei file richiesti per un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazione è un file di progetto (proj). Tutte le risorse usate nell'applicazione devono essere incluse nel file di progetto. L'esempio seguente da un file con estensione csproj illustra come effettuare questa operazione.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Usare una risorsa nell'applicazione crea un'istanza di un <xref:System.Resources.ResourceManager> e caricare la risorsa da usare. Nell'esempio riportato di seguito viene illustrato come procedere.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Uso di ClickOnce con applicazioni localizzate
 ClickOnce è una nuova tecnologia di distribuzione di Windows Form che verrà rilasciato con Visual Studio 2005. che consente l'installazione e l'aggiornamento di applicazioni Web. Quando un'applicazione distribuita con ClickOnce è localizzata, può essere visualizzata solo nelle impostazioni cultura localizzate. Ad esempio, se un'applicazione distribuita è localizzata in giapponese, può essere visualizzato solo nella versione giapponese [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] non su Windows in lingua inglese. Ciò costituisce un problema perché è uno scenario comune per gli utenti giapponesi eseguire una versione inglese di Windows.

 Per risolvere il problema, è necessario impostare l'attributo di fallback su una lingua neutra. Uno sviluppatore di applicazioni può facoltativamente rimuovere risorse dall'assembly principale e specificare che le risorse sono disponibili in un assembly satellite corrispondente a impostazioni cultura specifiche. A questo scopo, utilizzare il <xref:System.Resources.NeutralResourcesLanguageAttribute>. Il costruttore del <xref:System.Resources.NeutralResourcesLanguageAttribute> classe ha due firme, uno che accetta un <xref:System.Resources.UltimateResourceFallbackLocation> parametro per specificare il percorso in cui il <xref:System.Resources.ResourceManager> deve estrarre le risorse di fallback: assembly principale o in assembly satellite. L'esempio seguente mostra come usare l'attributo. Per il percorso di fallback finale, il codice fa in modo che il <xref:System.Resources.ResourceManager> per cercare le risorse nella sottodirectory "de" della directory dell'assembly attualmente in esecuzione.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Vedere anche

- [Panoramica della globalizzazione e localizzazione WPF](wpf-globalization-and-localization-overview.md)
