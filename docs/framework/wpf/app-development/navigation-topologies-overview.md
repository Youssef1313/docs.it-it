---
title: Cenni preliminari sulle topologie di navigazione
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 5d9b09085ed8057f53cae9f9177682b01e698f6d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580714"
---
# <a name="navigation-topologies-overview"></a>Cenni preliminari sulle topologie di navigazione
<a name="introduction"></a>In questa panoramica viene fornita un'introduzione alle topologie di navigazione in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Di seguito vengono analizzate tre topologie di navigazione comuni con i relativi esempi.  
  
> [!NOTE]
> Prima di leggere questo argomento, è necessario avere familiarità con il concetto di navigazione strutturata in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usando le funzioni di pagina. Per altre informazioni su entrambi gli argomenti, vedere [Cenni preliminari sulla navigazione strutturata](structured-navigation-overview.md).  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
- [Topologie di navigazione](#Navigation_Topologies)  
  
- [Topologie di navigazione strutturata](#Structured_Navigation_Topologies)  
  
- [Navigazione in una topologia lineare fissa](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Navigazione dinamica in una topologia gerarchica fissa](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Navigazione in una topologia generata dinamicamente](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie di navigazione  
 In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] la navigazione è in genere costituita da pagine (<xref:System.Windows.Controls.Page>) con collegamenti ipertestuali (<xref:System.Windows.Documents.Hyperlink>) che passano ad altre pagine quando si fa clic su di essa. Le pagine che sono state spostate sono identificate da URI (Uniform Resource Identifier) (vedere [URI di pacchetto in WPF](pack-uris-in-wpf.md)). Si consideri il semplice esempio seguente che mostra le pagine, i collegamenti ipertestuali e gli URI (Uniform Resource Identifier):  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Queste pagine sono disposte in una *topologia di navigazione* la cui struttura è determinata dal modo in cui è possibile spostarsi tra le pagine. Questa particolare topologia di navigazione è adatta in scenari semplici. La navigazione può tuttavia richiedere topologie più complesse, alcune delle quali possono essere definite solo quando un'applicazione è in esecuzione.  
  
 In questo argomento vengono illustrate tre topologie di navigazione comuni: *lineare fissa*, *gerarchica fissa*e *generata dinamicamente*. Ogni topologia di navigazione viene illustrata con un esempio con un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] come quello illustrato nella figura seguente:  
  
 ![Pagine di attività con elementi di dati e pulsanti di spostamento.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologie di navigazione strutturata  
 Vi sono due topologie principali di navigazione:  
  
- **Topologia fissa**: è definita in fase di compilazione e non viene modificata in fase di esecuzione. Le topologie fisse sono utili per la navigazione in una sequenza fissa di pagine in un ordine lineare o gerarchico.  
  
- **Topologia dinamica**: è definita in fase di esecuzione in base agli input raccolti dall'utente, dall'applicazione o dal sistema. Le topologie dinamiche sono utili quando è possibile spostarsi sulle pagine in sequenze diverse.  
  
 Sebbene sia possibile creare topologie di navigazione usando le pagine, gli esempi usano funzioni di pagina poiché questi offrono un supporto aggiuntivo che semplifica il passaggio e la restituzione dei dati tramite le pagine di una topologia.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigazione in una topologia lineare fissa  
 Una topologia lineare fissa è analoga alla struttura di una procedura guidata con una o più pagine in cui ci si sposta in una sequenza fissa. Nella figura seguente viene illustrata la struttura e il flusso di alto livello di una procedura guidata con una topologia lineare fissa:  
  
 ![Diagramma che mostra una topologia lineare fissa.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 I comportamenti tipici per la navigazione in una topologia lineare fissa includono quanto segue:  
  
- Navigazione dalla pagina chiamante a una pagina di avvio che inizializza la procedura guidata e porta alla prima pagina di questa. Non è necessaria una pagina di avvio (<xref:System.Windows.Navigation.PageFunction%601> senza [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) perché una pagina chiamante può chiamare direttamente la prima pagina della procedura guidata. L'uso di una pagina di avvio può tuttavia semplificare l'inizializzazione della procedura guidata, in particolare se questa è complessa.  
  
- Gli utenti possono spostarsi tra le pagine usando i pulsanti Avanti e Indietro (o i collegamenti ipertestuali).  
  
- Gli utenti possono spostarsi tra pagine usando il journal.  
  
- Gli utenti possono annullare la procedura guidata da qualsiasi pagina di questa premendo il pulsante Annulla.  
  
- Gli utenti possono accettare la procedura guidata all'ultima pagina premendo un pulsante Fine.  
  
- Se una procedura guidata viene annullata, questa restituisce un risultato appropriato e non restituisce alcun dato.  
  
- Se un utente accetta una procedura guidata, questa restituisce un risultato appropriato e restituisce i dati raccolti.  
  
- Al completamento della procedura guidata (accettata o annullata), le pagine incluse nella procedura guidata vengono rimosse dal journal. In questo modo ogni istanza della procedura guidata viene mantenuta isolata, per evitare potenziali anomalie di dati o stato.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Navigazione dinamica in una topologia gerarchica fissa  
 In alcune applicazioni, le pagine consentono la navigazione a due o più pagine, come illustrato nella figura seguente: 
  
 ![Diagramma che mostra una pagina in grado di spostarsi su più pagine.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Questa struttura è detta topologia gerarchica fissa e la sequenza in cui viene attraversata è spesso determinata in fase di esecuzione dall'applicazione o dall'utente. In fase di esecuzione, ogni pagina della gerarchia che consente di spostarsi su due o più altre pagine raccoglie i dati richiesti per determinare su quale pagina spostarsi. Nella figura seguente viene illustrata una delle diverse sequenze di navigazione possibili in base alla figura precedente:  
  
 ![Diagramma che mostra una possibile sequenza di navigazione.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Anche se la sequenza di navigazione delle pagine in una struttura gerarchica fissa è determinata in fase di esecuzione, l'esperienza utente è la stessa di una topologia lineare fissa:  
  
- Navigazione dalla pagina chiamante a una pagina di avvio che inizializza la procedura guidata e porta alla prima pagina di questa. Non è necessaria una pagina di avvio (<xref:System.Windows.Navigation.PageFunction%601> senza [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) perché una pagina chiamante può chiamare direttamente la prima pagina della procedura guidata. L'uso di una pagina di avvio può tuttavia semplificare l'inizializzazione della procedura guidata, in particolare se questa è complessa.  
  
- Gli utenti possono spostarsi tra le pagine usando i pulsanti Avanti e Indietro (o i collegamenti ipertestuali).  
  
- Gli utenti possono spostarsi tra pagine usando il journal.  
  
- Gli utenti possono modificare la sequenza di navigazione se tornano indietro tramite il journal.  
  
- Gli utenti possono annullare la procedura guidata da qualsiasi pagina di questa premendo il pulsante Annulla.  
  
- Gli utenti possono accettare la procedura guidata all'ultima pagina premendo un pulsante Fine.  
  
- Se una procedura guidata viene annullata, questa restituisce un risultato appropriato e non restituisce alcun dato.  
  
- Se un utente accetta una procedura guidata, questa restituisce un risultato appropriato e restituisce i dati raccolti.  
  
- Al completamento della procedura guidata (accettata o annullata), le pagine incluse nella procedura guidata vengono rimosse dal journal. In questo modo ogni istanza della procedura guidata viene mantenuta isolata, per evitare potenziali anomalie di dati o stato.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigazione in una topologia generata dinamicamente  
 In alcune applicazioni la sequenza di navigazione di due o più pagine può essere determinata solo in fase di esecuzione dall'utente, dall'applicazione o da dati esterni. Nella figura seguente viene illustrato un set di pagine con una sequenza di navigazione non determinata:  
  
 ![Set di pagine con una sequenza di navigazione non determinata.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Nella figura seguente viene illustrata una sequenza di navigazione scelta dall'utente in fase di esecuzione:  
  
 ![Diagramma che mostra una sequenza di navigazione scelta in fase di esecuzione.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 La sequenza di navigazione è indicata come topologia generata dinamicamente. L'esperienza utente è analoga alle topologie di navigazione precedenti:  
  
- Navigazione dalla pagina chiamante a una pagina di avvio che inizializza la procedura guidata e porta alla prima pagina di questa. Non è necessaria una pagina di avvio (<xref:System.Windows.Navigation.PageFunction%601> senza [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) perché una pagina chiamante può chiamare direttamente la prima pagina della procedura guidata. L'uso di una pagina di avvio può tuttavia semplificare l'inizializzazione della procedura guidata, in particolare se questa è complessa.  
  
- Gli utenti possono spostarsi tra le pagine usando i pulsanti Avanti e Indietro (o i collegamenti ipertestuali).  
  
- Gli utenti possono spostarsi tra pagine usando il journal.  
  
- Gli utenti possono annullare la procedura guidata da qualsiasi pagina di questa premendo il pulsante Annulla.  
  
- Gli utenti possono accettare la procedura guidata all'ultima pagina premendo un pulsante Fine.  
  
- Se una procedura guidata viene annullata, questa restituisce un risultato appropriato e non restituisce alcun dato.  
  
- Se un utente accetta una procedura guidata, questa restituisce un risultato appropriato e restituisce i dati raccolti.  
  
- Al completamento della procedura guidata (accettata o annullata), le pagine incluse nella procedura guidata vengono rimosse dal journal. In questo modo ogni istanza della procedura guidata viene mantenuta isolata, per evitare potenziali anomalie di dati o stato.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Cenni preliminari sulla navigazione strutturata](structured-navigation-overview.md)
