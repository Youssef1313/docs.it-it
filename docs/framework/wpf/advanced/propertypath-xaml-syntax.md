---
title: Sintassi XAML di PropertyPath
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 5dc8fc8c43e43691c46ad84379fe2bcb23987667
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660791"
---
# <a name="propertypath-xaml-syntax"></a>Sintassi XAML di PropertyPath

Il <xref:System.Windows.PropertyPath> oggetto supporta un inline complessa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintassi per l'impostazione di varie proprietà che accettano il <xref:System.Windows.PropertyPath> tipo come relativo valore. Questo argomento viene descritta la <xref:System.Windows.PropertyPath> sintassi quando viene applicato a tipi di sintassi di associazione e l'animazione.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Uso di PropertyPath

<xref:System.Windows.PropertyPath> è un oggetto comune usato in diverse [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funzionalità. Nonostante l'uso comune <xref:System.Windows.PropertyPath> per comunicare informazioni sul percorso di proprietà, gli utilizzi per ogni area funzionale in cui <xref:System.Windows.PropertyPath> viene usato come tipo variano. È quindi più pratico documentare le sintassi per ogni funzionalità.

In primo luogo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Usa <xref:System.Windows.PropertyPath> descrivono i percorsi del modello a oggetti per attraversare le proprietà di un'origine dati oggetto di descrizione al percorso di destinazione per le animazioni mirate.

Alcune proprietà di stile e del modello, ad esempio <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> accettano un nome completo della proprietà in apparenza è analogo a un <xref:System.Windows.PropertyPath>. Ma ciò non costituisce un vero e proprio <xref:System.Windows.PropertyPath>; si tratta invece di un qualified *proprietario. proprietà* stringa dell'utilizzo del formato è abilitata per l'applicazione WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processore in combinazione con il convertitore di tipi per <xref:System.Windows.DependencyProperty>.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath per gli oggetti nel data binding

Il data binding è una funzionalità di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] che consente di eseguire il binding al valore di destinazione di qualsiasi proprietà di dipendenza. L'origine di tale data binding non deve però essere necessariamente una proprietà di dipendenza, ma può essere qualsiasi tipo di proprietà riconosciuto dal provider di dati applicabile. I percorsi delle proprietà vengono usati in particolare per le <xref:System.Windows.Data.ObjectDataProvider>, che viene usato per ottenere origini di associazione da [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] oggetti e le relative proprietà.

Si noti che per il data binding [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] non usa <xref:System.Windows.PropertyPath>, perché non usa <xref:System.Windows.Data.Binding.Path%2A> nel <xref:System.Windows.Data.Binding>. Usare invece <xref:System.Windows.Data.Binding.XPath%2A> e specificare la sintassi XPath valida nel [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] dei dati. <xref:System.Windows.Data.Binding.XPath%2A> viene anche specificato come stringa, ma non è documentata in questa sede. visualizzare [associare a dati XML tramite un oggetto XMLDataProvider e query XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Per comprendere i percorsi delle proprietà nel data binding bisogna considerare che è possibile scegliere come destinazione del binding un singolo valore di proprietà oppure è possibile eseguire il binding a proprietà di destinazione che accettano elenchi o raccolte. Se si desidera associare le raccolte, ad esempio associa un <xref:System.Windows.Controls.ListBox> che verrà espanso a seconda del numero di elementi dati presenti nella raccolta, quindi il percorso della proprietà deve fare riferimento all'oggetto raccolta e non singoli elementi della raccolta. Il motore di associazione di dati corrisponderà alla raccolta usata come origine dati per il tipo della destinazione del binding automaticamente, determinando un comportamento come il popolamento in un <xref:System.Windows.Controls.ListBox> con una matrice di elementi.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Singola proprietà sull'oggetto immediato come contesto dati

```xml
<Binding Path="propertyName" .../>
```

*propertyName* deve essere risolto nel nome di una proprietà che è nell'attuale <xref:System.Windows.FrameworkElement.DataContext%2A> per un <xref:System.Windows.Data.Binding.Path%2A> utilizzo. Se il binding aggiorna l'origine, tale proprietà deve essere di lettura/scrittura e l'oggetto di origine deve essere modificabile.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Singolo indicizzatore sull'oggetto immediato come contesto dati

```xml
<Binding Path="[key]" .../>
```

`key` deve essere l'indice tipizzato per un dizionario o una tabella hash oppure l'indice Integer di una matrice. Il valore della chiave deve inoltre essere un tipo direttamente associabile alla proprietà a cui è applicato. Ad esempio, una tabella hash che contiene chiavi stringa e valori stringa utilizzabile in questo modo per eseguire l'associazione al testo per un <xref:System.Windows.Controls.TextBox>. In alternativa, se la chiave punta a una raccolta o a un indice secondario, è possibile usare questa sintassi per il binding a una proprietà della raccolta di destinazione. In caso contrario, è necessario fare riferimento a una proprietà specifica, tramite una sintassi come `<Binding Path="[key].propertyName" .../>`.

È possibile specificare il tipo dell'indice, se necessario. Per informazioni dettagliate su questo aspetto del percorso di proprietà indicizzate, vedere <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Più proprietà (impostazione indiretta delle proprietà come destinazioni)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName` deve essere risolto nel nome di una proprietà che è corrente <xref:System.Windows.FrameworkElement.DataContext%2A>. Le proprietà del percorso `propertyName` e `propertyName2` possono essere costituite da qualsiasi proprietà presente in una relazione, dove `propertyName2` è una proprietà presente nel tipo che corrisponde al valore di `propertyName`.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Singola proprietà, associata o qualificata in altro modo dal tipo

```xml
<object property="(ownerType.propertyName)" .../>
```

Le parentesi indicano che questa proprietà in un <xref:System.Windows.PropertyPath> deve essere creata mediante una qualificazione parziale. Può usare uno spazio dei nomi XML per trovare il tipo con un mapping appropriato. Il `ownerType` tipi di ricerche di una [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processore può accedere a, tramite il <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dichiarazioni in ogni assembly. La maggior parte delle applicazioni ha lo spazio dei nomi XML predefinito mappato allo spazio dei nomi [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)], quindi in genere è necessario un prefisso solo per i tipi personalizzati o per i tipi altrimenti esterni allo spazio dei nomi.  `propertyName` deve risolversi nel nome di una proprietà presente in `ownerType`. Questa sintassi viene in genere usata per uno dei casi seguenti:

- Il percorso è specificato in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ovvero in uno stile o modello che non ha un tipo di destinazione specificato. Un utilizzo qualificato non è in genere valido in casi diversi da questo, perché in casi senza uno stile o un modello la proprietà è presente in un'istanza, non in un tipo.

- La proprietà è una proprietà associata.

- Si sta eseguendo il binding a una proprietà statica.

Per l'uso come destinazione dello storyboard, la proprietà specificata come `propertyName` deve essere un <xref:System.Windows.DependencyProperty>.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Attraversamento dell'origine (binding a gerarchie di raccolte)

```xml
<object Path="propertyName/propertyNameX" .../>
```

Il carattere / in questa sintassi viene usato per spostarsi in un oggetto origine dati gerarchico e sono supportati più passaggi nella gerarchia con caratteri / successivi. L'attraversamento dell'origine tiene conto della posizione del puntatore di record corrente, determinata sincronizzando i dati con l'interfaccia utente della relativa visualizzazione. Per informazioni dettagliate sul binding con oggetti origine dati gerarchici e sul concetto di puntatore di record corrente nel data binding, vedere [Usare il modello Master-Details con dati gerarchici](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) o [Panoramica sul data binding](../data/data-binding-overview.md).

> [!NOTE]
> Questa sintassi è apparentemente analoga a [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Un vero e proprio [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] espressione per l'associazione a un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] origine dati non viene usata come una <xref:System.Windows.Data.Binding.Path%2A> valore e deve essere usato invece per si escludono a vicenda <xref:System.Windows.Data.Binding.XPath%2A> proprietà.

### <a name="collection-views"></a>Visualizzazioni di raccolte

Per fare riferimento a una visualizzazione di raccolta denominata, premettere il carattere hash (`#`) al nome della visualizzazione di raccolta.

### <a name="current-record-pointer"></a>Puntatore al record corrente

Per fare riferimento al puntatore al record corrente per una visualizzazione di raccolta o uno scenario di data binding master-dettagli, iniziare la stringa di percorso con una barra (`/`). Qualsiasi percorso dopo la barra viene attraversato a partire dal puntatore al record corrente.

### <a name="multiple-indexers"></a>Indicizzatori multipli

```xaml
<object Path="[index1,index2...]" .../>
```

oppure

```xaml
<object Path="propertyName[index,index2...]" .../>
```

Se un determinato oggetto supporta più indicizzatori, è possibile specificare tali indicizzatori in ordine, analogamente a una sintassi che fa riferimento a una matrice. L'oggetto in questione può essere il contesto corrente o il valore di una proprietà contenente un oggetto a più indici.

Per impostazione predefinita, i valori dell'indicizzatore sono tipizzati usando le caratteristiche dell'oggetto sottostante. È possibile specificare il tipo dell'indice, se necessario. Per informazioni dettagliate sulla tipizzazione degli indicizzatori, vedere <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Sintassi miste

Tutte le sintassi illustrate in precedenza possono essere combinate. Ad esempio, ecco un esempio che crea un percorso di proprietà per il colore in un determinato punto x, y di un `ColorGrid` proprietà che contiene una matrice di griglia di pixel <xref:System.Windows.Media.SolidColorBrush> oggetti:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Caratteri di escape per le stringhe di percorso delle proprietà

Per determinati oggetti business è possibile che la stringa di percorso delle proprietà richieda un carattere di escape per poter essere analizzata correttamente. L'esigenza di usare caratteri di escape deve essere rara, perché molti di questi caratteri hanno problemi di interazione-denominazione simili nei linguaggi che in genere vengono usati per definire l'oggetto business.

- All'interno degli indicizzatori ([ ]), l'accento circonflesso (^) funge da escape per il carattere successivo.

- È necessario usare caratteri di escape (con entità XML) per alcuni caratteri specifici della definizione del linguaggio XML. Usare `&` come carattere di escape per "&". Usare `>` come carattere di escape per il tag di fine ">".

- È necessario usare un carattere di escape (la barra rovesciata `\`) per i caratteri specifici del comportamento del parser XAML di WPF per l'elaborazione di un'estensione di markup.

  - La stessa barra rovesciata (`\`) costituisce il carattere di escape.

  - Il segno di uguale (`=`) separa il nome della proprietà dal valore della proprietà.

  - La virgola (`,`) separa le proprietà.

  - La parentesi graffa chiusa (`}`) rappresenta la fine di un'estensione di markup.

> [!NOTE]
> Tecnicamente, questi caratteri di escape funzionano anche per un percorso di proprietà dello storyboard, ma in genere si attraversano modelli a oggetti per oggetti WPF esistenti e l'uso di caratteri di escape non è necessario.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath per le destinazioni delle animazioni

La proprietà di destinazione di un'animazione deve essere una proprietà di dipendenza che accetta un <xref:System.Windows.Freezable> o un tipo primitivo. La proprietà di destinazione su un tipo e la proprietà animata finale possono tuttavia trovarsi su oggetti diversi. Per le animazioni, un percorso delle proprietà viene usato per definire la connessione tra la proprietà dell'oggetto di destinazione dell'animazione denominata e la proprietà dell'animazione di destinazione prevista, attraversando le relazioni oggetto-proprietà nei valori di proprietà.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Considerazioni generali sulle relazioni oggetto-proprietà per le animazioni

Per altre informazioni sui concetti di animazione in generale, vedere [Cenni preliminari sugli storyboard](../graphics-multimedia/storyboards-overview.md) e [Cenni preliminari sull'animazione](../graphics-multimedia/animation-overview.md).

Il tipo di valore o la proprietà animata deve essere un <xref:System.Windows.Freezable> tipo o primitivo. La proprietà che inizia il percorso deve essere risolto nel nome di una proprietà di dipendenza esistente specificato <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> tipo.

Per supportare la clonazione per l'animazione di un <xref:System.Windows.Freezable> già bloccato, l'oggetto specificato da <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> deve essere un <xref:System.Windows.FrameworkElement> o <xref:System.Windows.FrameworkContentElement> classe derivata.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Singola proprietà nell'oggetto di destinazione

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName` deve essere risolto nel nome di una proprietà di dipendenza esistente specificato <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> tipo.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Impostazione indiretta delle proprietà come destinazioni

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName` deve essere una proprietà che è un <xref:System.Windows.Freezable> valore o un tipo primitivo, presente sull'oggetto specificato <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> tipo.

`propertyName2` deve essere il nome di una proprietà di dipendenza presente nell'oggetto che costituisce il valore di `propertyName`. In altre parole, `propertyName2` deve esistere come una proprietà di dipendenza nel tipo che è il `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.

L'impostazione indiretta delle animazioni come destinazioni è necessaria a causa degli stili e dei modelli applicati. Per impostare come destinazione un'animazione, è necessario un <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> su un oggetto di destinazione e tale nome è stabilito da [X:Name](../../xaml-services/x-name-directive.md) o <xref:System.Windows.FrameworkElement.Name%2A>. Sebbene gli elementi di modelli e stili possano avere nomi, tali nomi sono validi solo all'interno dell'ambito dei nomi dello stile e del modello. Se modelli e stili non condividessero gli ambiti dei nomi con il markup dell'applicazione, i nomi non potrebbero essere univoci. Stili e modelli sono letteralmente condivisi tra le istanze e ciò comporterebbe nomi duplicati. Quindi, se le singole proprietà di un elemento che si vuole animare provengono da uno stile o da un modello, è necessario iniziare con un'istanza di elemento denominato non proveniente da un modello o uno stile e quindi impostare la destinazione nella struttura ad albero visuale dello stile o del modello per arrivare alla proprietà che si vuole animare.

Ad esempio, il <xref:System.Windows.Controls.Panel.Background%2A> proprietà di un <xref:System.Windows.Controls.Panel> un termine <xref:System.Windows.Media.Brush> (effettivamente un <xref:System.Windows.Media.SolidColorBrush>) provenienti da un modello di tema. Per aggiungere un'animazione a un <xref:System.Windows.Media.Brush> completamente, sarebbe necessario essere un BrushAnimation (probabilmente uno per ogni <xref:System.Windows.Media.Brush> tipo) e nessun tipo di questo tipo. Per animare un pennello, è invece necessario animare le proprietà di un determinato <xref:System.Windows.Media.Brush> tipo. È necessario ottenere da <xref:System.Windows.Media.SolidColorBrush> al relativo <xref:System.Windows.Media.SolidColorBrush.Color%2A> per applicare un <xref:System.Windows.Media.Animation.ColorAnimation> non esiste. Il percorso della proprietà per questo esempio sarebbe `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Proprietà associate

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Le parentesi indicano che questa proprietà in un <xref:System.Windows.PropertyPath> deve essere creata mediante una qualificazione parziale. Può usare uno spazio dei nomi XML per trovare il tipo. Il `ownerType` tipi di ricerche di una [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processore può accedere a, tramite il <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dichiarazioni in ogni assembly. La maggior parte delle applicazioni ha lo spazio dei nomi XML predefinito mappato allo spazio dei nomi [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)], quindi in genere è necessario un prefisso solo per i tipi personalizzati o per i tipi altrimenti esterni allo spazio dei nomi. `propertyName` deve risolversi nel nome di una proprietà presente in `ownerType`. La proprietà specificata come `propertyName` deve essere un <xref:System.Windows.DependencyProperty>. Tutte le proprietà associate di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sono implementate come proprietà di dipendenza, quindi questo problema riguarda solo le proprietà associate personalizzate.

<a name="indexanim"></a>

### <a name="indexers"></a>Indicizzatori

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

La maggior parte delle proprietà di dipendenza o <xref:System.Windows.Freezable> tipi non supportano un indicizzatore. L'unico utilizzo di un indicizzatore in un percorso di animazione è quindi in una posizione intermedia tra la proprietà che inizia la catena nella destinazione denominata e la proprietà animata finale. Nella sintassi fornita si tratta di `propertyName2`. Ad esempio, potrebbe essere necessario se la proprietà intermedia è una raccolta, ad esempio utilizzo di un indicizzatore <xref:System.Windows.Media.TransformGroup>, in un percorso di proprietà, ad esempio `RenderTransform.Children[1].Angle`.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath nel codice

Utilizzo del codice per <xref:System.Windows.PropertyPath>, incluse le procedure creare un <xref:System.Windows.PropertyPath>, è documentato nell'argomento di riferimento per <xref:System.Windows.PropertyPath>.

In generale, <xref:System.Windows.PropertyPath> è progettata per usare due costruttori diversi, uno per gli utilizzi di binding e animazione più semplici e uno per gli utilizzi di animazione complessi. Usare il <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> firma per l'associazione utilizzi, in cui l'oggetto è una stringa. Usare la <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> firma per i percorsi di animazione a un solo passaggio, in cui l'oggetto è un <xref:System.Windows.DependencyProperty>. Usare il <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> firma per le animazioni complesse. Quest'ultimo costruttore usa una stringa token per il primo parametro e una matrice di oggetti che riempiono le posizioni nella stringa token per definire una relazione di percorso di proprietà.

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.PropertyPath>
- [Panoramica sul data binding](../data/data-binding-overview.md)
- [Cenni preliminari sugli storyboard](../graphics-multimedia/storyboards-overview.md)
