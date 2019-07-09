---
title: Strumento Visualizzatore di tracce dei servizi (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 02d2dd74031f280808027df1c0b7b78a90e6cd52
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664108"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Strumento Visualizzatore di tracce dei servizi (SvcTraceViewer.exe)

Strumento Visualizzatore di tracce dei servizi Windows Communication Foundation (WCF) consente di analizzare le tracce di diagnostica vengono generate da WCF. Service Trace Viewer offre un modo per unire, visualizzare e filtrare i messaggi di traccia nel log in modo che è possibile diagnosticare, riparare e verificare i problemi del servizio WCF.

## <a name="configuring-tracing"></a>Configurazione delle funzionalità di traccia

Le tracce di diagnostica forniscono informazioni che mostrano quello si sta verificando in tutta l'operazione dell'applicazione. Come si intuisce dal nome, è possibile seguire le operazioni dall'origine alla destinazione e tramite punti intermedi.

È possibile configurare la traccia utilizzando il file di configurazione dell'applicazione, ovvero Web. config per le applicazioni ospitate sul Web, oppure *NomeApp*. config per applicazioni self-hosted. Di seguito è riportato un esempio:

```xml
<system.diagnostics>
    <trace autoflush="true" />
    <sources>
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"
                    propagateActivity="true">
            <listeners>
               <add name="sdt"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "SdrConfigExample.e2e" />
            </listeners>
         </source>
    </sources>
</system.diagnostics>
```

In questo esempio vengono specificati il nome e il tipo del listener di traccia. Il listener viene denominato `sdt` e come tipo viene aggiunto il listener di traccia standard di .NET Framework, ovvero System.Diagnostics.XmlWriterTraceListener. Il `initializeData` attributo è utilizzato per impostare il nome del file di log per il Listener sia `SdrConfigExample.e2e`. Per il file di log è possibile sostituire un percorso completo con un semplice nome file.

In questo esempio viene creato un file nella directory radice denominato SdrConfigExample.e2e. Quando si usa il Visualizzatore di tracce per aprire il file come descritto nella sezione "Apertura e visualizzazione di file di traccia WCF", è possibile visualizzare tutti i messaggi che sono stati inviati.

Il livello di traccia viene controllato in base all'impostazione `switchValue`. Nella tabella seguente viene fornita una descrizione dei livelli di traccia disponibili.

|Livello di traccia|Descrizione|
|-----------------|-----------------|
|Critico|-Registra le voci del registro eventi e Fail-Fast e informazioni di correlazione di traccia. Di seguito sono indicati alcuni esempi di quando è possibile utilizzare il livello Critico:<br />-AppDomain non disponibile a causa di un'eccezione non gestita.<br />-L'applicazione non viene avviato.<br />-Il messaggio che ha causato l'errore ha originata nel processo MyApp.exe.|
|Error|-Registra tutte le eccezioni. È possibile utilizzare il Livello di errore nei casi seguenti:<br />-Il codice è arrestato in modo anomalo a causa di un'eccezione di Cast non valido.<br />-Un'eccezione "non è stato possibile creare endpoint" è causato da errore all'avvio dell'applicazione.|
|Avviso|-Una condizione esistente che può dare luogo a un errore o critico. È possibile utilizzare questo livello nei casi seguenti:<br />-L'applicazione riceve più richieste di maggiore di quello consentito dalle impostazioni di limitazione.<br />-La coda di ricezione ha raggiunto il 98 percento della capacità massima configurata.|
|Informazioni|-Generazione di messaggi utili per il monitoraggio e la diagnosi dello stato di sistema, la misurazione delle prestazioni, o la profilatura. È possibile utilizzare queste informazioni durante la pianificazione delle capacità e la gestione delle prestazioni. È possibile utilizzare questo livello nei casi seguenti:<br />-Errore dopo che il messaggio ha raggiunto l'AppDomain ed è stato deserializzato.<br />-Errore durante la creazione di associazione HTTP.|
|Dettagliato|Di debug a livello traccia per codice utente e di manutenzione. Impostare questo livello quando:<br />-Non si conosce quale metodo nel codice è stato chiamato quando si è verificato l'errore.<br />-È stato configurato un endpoint errato ed il servizio non è stato possibile avviare perché la voce nell'archivio prenotazioni è bloccata.|
|ActivityTracing|Eventi di flusso tra attività di elaborazione e componenti.<br /><br /> Questo livello consente ad amministratori e sviluppatori di mettere in correlazione applicazioni nello stesso dominio applicazione.<br /><br /> -Le tracce per limiti di attività: avvio/arresto.<br />-Le tracce per trasferimenti.|

 È possibile utilizzare l'istruzione `add` per specificare il nome e il tipo del listener di traccia che si desidera utilizzare. Nella configurazione dell'esempio il listener viene denominato `sdt` e come tipo viene aggiunto il listener di traccia standard di .NET Framework, ovvero `System.Diagnostics.XmlWriterTraceListener`. Utilizzare l'istruzione `initializeData` per impostare il nome del file di log del Listener. È inoltre possibile sostituire un percorso completo con un semplice nome file.

A partire da .NET Framework 4.8, i controlli casella combinata in alcuni temi a contrasto elevato vengono visualizzati nel colore corretto. È possibile disabilitare questa modifica rimuovendo l'impostazione seguente dal *svcTraceViewer.exe.config* file:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Uso dello strumento Visualizzatore di tracce dei servizi

### <a name="opening-and-viewing-wcf-trace-files"></a>Apertura e visualizzazione di file di traccia WCF

Il Visualizzatore traccia servizio supporta tre tipi di file:

- Analisi di File (svclog) di WCF

- File di traccia eventi, con estensione etl

- File di traccia Crimson

 Mediante lo strumento Visualizzatore di tracce dei servizi è possibile aprire i file di traccia supportati, aggiungere e integrare file aggiuntivi e aprire e unire simultaneamente un gruppo di file di traccia.

##### <a name="to-open-a-trace-file"></a>Per aprire un file di traccia

1. Avviare Service Trace Viewer, utilizzare una finestra di comando per passare al percorso di installazione di WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) e quindi digitare `SvcTraceViewer.exe`.

> [!NOTE]
> Lo strumento Visualizzatore di tracce dei servizi può essere associato a due tipi di file: svclog e stvproj. Per eseguire e annullare la registrazione delle estensioni di file è possibile utilizzare due parametri nella riga di comando.
>
> /register: consente di registrare l'associazione delle estensioni di file "svclog" e "stvproj" a SvcTraceViewer.exe
>
> /unregister: consente di annullare la registrazione dell'associazione delle estensioni di file "svclog" e "stvproj" a SvcTraceViewer.exe

1. All'avvio di Service Trace Viewer, fare clic su **File** e quindi scegliere **Open**. Passare al percorso in cui sono archiviati i file di traccia.

2. Fare doppio clic sul file di traccia che si desidera aprire.

    > [!NOTE]
    > Premere MAIUSC mentre si fa clic su più file di traccia per selezionarli e aprirli simultaneamente. Lo strumento Visualizzatore di tracce dei servizi consente di unire e visualizzare il contenuto di tutti i file in una visualizzazione unificata. È ad esempio possibile aprire i file di traccia sia del client sia del servizio. Ciò è utile quando nella configurazione sono state attivate le funzionalità di registrazione dei messaggi e di propagazione delle attività. In questo caso la visualizzazione unificata dei contenuti dei file consente infatti di analizzare lo scambio dei messaggi fra client e servizio. È anche possibile trascinare più file nel visualizzatore o usare il **progetto** scheda. Per ulteriori dettagli, vedere la sezione relativa alla gestione dei progetti.

3. Per aggiungere file aggiuntivi nella raccolta che è aperta, fare clic su **File** e quindi scegliere **Add**. Nella finestra visualizzata, spostarsi al percorso dei file di traccia e fare doppio clic sul file che si desidera aggiungere.

> [!CAUTION]
> Non è consigliabile caricare un file di log di traccia di dimensioni superiori a 200 MB. Se si tenta di caricare un file di dimensioni superiori, il processo di caricamento può richiedere molto tempo, a seconda delle risorse del computer. Lo strumento Visualizzatore di tracce dei servizi può non rispondere per molto tempo o può esaurire la memoria del computer. Per evitare che ciò avvenga, è consigliabile configurare la funzionalità di caricamento parziale. Per ulteriori informazioni su questa procedura, vedere la sezione "Caricamento di file di traccia di grandi dimensioni”.

#### <a name="event-tracing-and-crimson-tracing"></a>Formati di traccia eventi e di traccia Crimson

Il formato nativo del visualizzatore è il formato di traccia di attività generato da WCF. Le tracce generate in un altro formato devono essere convertite affinché il visualizzatore sia in grado di leggerle. Attualmente, oltre al formato di traccia delle attività, il visualizzatore supporta i formati di traccia eventi e di traccia Crimson.

Quando si apre un file che non contiene tracce di attività, il visualizzatore prova a convertirlo. Occorre quindi specificare il nome e il percorso del file in cui salvare i dati di traccia convertiti. Dopo aver eseguito la conversione dei dati, il visualizzatore mostra il contenuto del nuovo file.

> [!NOTE]
> Al termine della conversione, i dati di traccia convertiti vengono salvati nel disco rigido. Prima di avviare la conversione è pertanto necessario verificare che lo spazio disponibile sul disco sia sufficiente a contenere tali dati. In caso contrario, la conversione avrà esito negativo.

### <a name="managing-projects"></a>Gestione di progetti

Per visualizzare simultaneamente più file di traccia è possibile utilizzare la funzionalità di gestione di progetti del visualizzatore. Se ad esempio si dispone del file di traccia di un client e del file di traccia di un servizio, è possibile aggiungerli a un progetto. Ogni volta che si apre il progetto, tutti i relativi file di traccia verranno quindi caricati simultaneamente.

Esistono due modalità per gestire i progetti:

- Nel **File** menu, è possibile aprire, salvare e chiudere progetti.

- Nel **progetto** scheda, è possibile aggiungere file a un progetto.

### <a name="viewing-wcf-traces"></a>Visualizzazione di tracce WCF

WCF genera tracce utilizzando il formato di traccia di attività. Nel modello delle tracce delle attività, le singole tracce vengono raggruppate in attività in base al loro scopo. Il flusso di controllo logico viene trasferito tra le attività. Durante il periodo di attività di un'applicazione, ad esempio, iniziano e terminano molte attività di trasmissione di messaggi. Per altre informazioni sulla visualizzazione troppo le tracce e le attività e dell'interfaccia utente di Service Trace Viewer, vedere [utilizzando Service Trace Viewer per la visualizzazione di tracce correlate e risoluzione dei problemi](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Passaggio a una visualizzazione specifica

Nel Visualizzatore di tracce dei servizi sono disponibili le visualizzazioni distinte seguenti, Essi vengono visualizzati come schede nel riquadro a sinistra del visualizzatore e sono accessibili anche dal **vista** menu.

- Visualizzazione Attività

- Visualizzazione Progetto

- Visualizzazione Messaggio

- Visualizzazione grafico

##### <a name="activity-view"></a>Visualizzazione Attività

Una volta vengono aperti i file di traccia, è possibile visualizzare le tracce raggruppate per attività e visualizzato nei **attività** vista nel riquadro a sinistra.

Il **attività** nomi delle attività di visualizzazione consente di visualizzare, numero di tracce contenute nell'attività, durata massima, ora di inizio e ora di fine.

Se si fa clic su una delle attività elencate, nel riquadro delle tracce a destra vengono visualizzate le tracce contenute in tale attività. È quindi possibile selezionare una traccia per visualizzarne i dettagli.

È possibile selezionare più attività premendo la **Ctrl** oppure **MAIUSC** chiave e scegliendo attività desiderate. Nel riquadro delle tracce vengono visualizzate tutte le tracce contenute nelle attività selezionate.

È possibile fare doppio clic per visualizzarla in un'attività **Graph** visualizzazione. L'alternativa consiste nel selezionare un'attività e passare a **Graph** visualizzazione.

> [!NOTE]
> L'attività "000000000000" è un'attività speciale che non può essere visualizzata nella visualizzazione grafico. Poiché a tale attività sono collegate tutte le altre attività, la visualizzazione di questa attività comporta una notevole riduzione delle prestazioni.

Per ordinare l'elenco delle attività è possibile fare clic sul titolo della colonna. Le attività che contengono tracce di avviso presentano uno sfondo giallo, mentre quelle che contengono tracce di errore presentano uno sfondo rosso.

Esistono tre tipi distinti di attività, ognuno di essi caratterizzato da un'icona visualizzata a sinistra di ogni attività. Per conoscere il significato delle icone, consultare la sezione relativa alla descrizione delle icone di traccia.

##### <a name="project-view"></a>Visualizzazione Progetto

Questa visualizzazione consente di gestire i file di traccia del progetto corrente. Per ulteriori dettagli, vedere la sezione relativa alla gestione dei progetti.

##### <a name="message-view"></a>Visualizzazione Messaggio

Questa vista consente visualizzare tutti i log dei messaggi tiene traccia, tra cui azione, data/ora, processo, attività e da/verso e passare ai dettagli di traccia del log dei messaggi associati. È possibile raggruppare le tracce di log messaggio dal limite di attività, processi e Thread, o trasmissione e ricezione per semplificare l'esplorazione del flusso del messaggio.

##### <a name="graph-view"></a>Visualizzazione grafico

Questa vista sono riportati i dati di traccia per una determinata attività in formato grafico. Questo tipo di visualizzazione consente di esaminare l'esecuzione sequenziale dei passaggi degli eventi e le interrelazioni tra più attività dovute allo spostamento di dati fra tali file.

Per passare alla **Graph** visualizzazione, selezionare un'attività nel **attività** consente di visualizzare e fare clic sul **attività** tab oppure una traccia log dei messaggi nel **messaggio**Vista. Se sono stati caricati più file di traccia e l'attività contiene tracce ricavate da più di un file, tutte le tracce attinenti sono visualizzate nella visualizzazione Grafico. Facendo doppio clic sulle attività e le tracce del log dei messaggi comporta anche per il **Graph** visualizzazione.

Nelle **Graph** visualizzazione, ogni colonna verticale rappresenta un'attività e ogni blocco nella colonna rappresenta una traccia. Le attività sono raggruppate per processo (o thread). Le frecce piccole tra le attività rappresentano i trasferimenti. Le frecce grandi tra i processi rappresentano lo scambio di messaggi. L'attività attualmente selezionata è sempre visualizzata in giallo.

###### <a name="selecting-traces-in-the-graph"></a>Selezione di Tracce nel Grafico

1. Fare clic su un blocco del grafico.

2. Utilizzare i tasti SU e GIÙ per selezionare le tracce adiacenti.

3. Osservare le informazioni di traccia riportate nel riquadro delle tracce e nel Riquadro dettagli.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Espansione o compressione dei trasferimenti delle attività

Quando l'attività attualmente selezionata trasferisce l'esecuzione a un'altra attività è possibile espandere i trasferimenti delle attività. Ciò consente di seguire i trasferimenti.

Per espandere o comprimere i trasferimenti delle attività,

1. Individuare la traccia di trasferimento con un segno "+" a sinistra dell'icona di trasferimento.

2. Fare clic su "+" oppure premere **Ctrl** e "+" utilizzando la tastiera.

3. Nel grafico verrà visualizzata l'attività successiva.

4. Un "-" viene visualizzato a sinistra dell'icona di trasferimento. Fare clic su di "-" accedere o premere Ctrl e "-", consente di comprimere il trasferimento dell'attività.

> [!NOTE]
> Quando esistono più trasferimenti verso una determinata attività e si espande uno di essi, il sistema visualizza le attività che portano alla nuova attività a partire dall'attività radice. Queste nuove attività sono visualizzate in forma compressa. Per esaminare i dettagli di queste attività è possibile espanderle verticalmente facendo clic sull'icona di espansione posta nell'intestazione del grafico.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Espansione o compressione verticale delle attività

Al fine di nascondere i dettagli superflui, il visualizzatore consente di comprimere le attività riportate nel grafico delle attività. Quando un'attività è compressa, le tracce specifiche in essa contenute non vengono visualizzate. Vengono riportati soltanto i trasferimenti di traccia. Per visualizzare tutte le tracce di un'attività è possibile espandere verticalmente l'attività. A tale scopo, fare clic sul simbolo di espansione dell'attività posto nell'intestazione del grafico.

Per espandere o comprimere verticalmente le attività

1. Fare clic sull'icona "+" nell'intestazione di attività per espandere verticalmente l'attività.

2. Si noti che nel grafico vengono visualizzate tutte le tracce.

3. Scegliere il "-" sull'icona nell'intestazione di attività per comprimere verticalmente le attività.

4. Si noti che nell'attività sono riportati solo i trasferimenti, i log dei messaggi, le tracce di avviso e di eccezione di maggiore importanza.

###### <a name="options"></a>Opzioni

È possibile selezionare due opzioni di **opzione** menu nella parte visibile del grafico.

- Mostra tracce del limite delle attività. Tale opzione, se deselezionata, consente di escludere dal grafico le tracce di limite attività.

- Mostra tracce dettagliate che non appartengono a messaggi. Tale opzione, se deselezionata, consente di escludere dal grafico le tracce di livello dettagliato, tranne nel caso di tracce di messaggio. Nella maggior parte dei casi le tracce di livello dettagliato sono meno importanti ai fini dell'analisi. Questa opzione è utile quando non si desidera analizzare le tracce di livello dettagliato al fine di concentrarsi esclusivamente sulle tracce più importanti.

###### <a name="layout-mode"></a>Modalità di layout

Il visualizzatore presenta due modalità di Layout: **Processo** e **Thread**. Questa impostazione definisce l'unità massima di organizzazione. La modalità di Layout predefinita è **processo**, il che significa che le attività vengono raggruppate da parte dei processi nel grafico.

###### <a name="execution-list"></a>Elenco di esecuzione

In questo elenco a discesa è possibile selezionare quale processo o thread visualizzare nel grafico. Se ad esempio sono stati aperti i file di traccia di un servizio e di due client (A e B), per visualizzare nel grafico solo il servizio e il client A è possibile deselezionare nell'elenco il client B.

#### <a name="viewing-trace-details"></a>Visualizzazione dei dettagli di una traccia

Per visualizzare i dettagli di una traccia, selezionarla nel riquadro delle tracce. I dettagli vengono riportati nel Riquadro dettagli.

##### <a name="trace-pane"></a>Riquadro delle tracce

Il riquadro nell'angolo superiore destro del Visualizzatore di tracce dei servici è il riquadro delle tracce. In questo riquadro sono elencate tutte le tracce contenute nell'attività selezionata, insieme alle relative informazioni aggiuntive, ad esempio livello di traccia, ID del thread e nome del processo.

È possibile copiare il codice XML non elaborato della traccia negli Appunti facendo clic su una traccia e selezionando **traccia copia negli Appunti**.

##### <a name="detail-pane"></a>Riquadro dettagli

Il riquadro nell'angolo inferiore sinistro del Visualizzatore di tracce dei servizi è il Riquadro dettagli. Questo riquadro presenta tre schede che consentono di visualizzare i dettagli di una traccia.

Il **formattato** vista vengono visualizzate le informazioni in modo più organizzato. Tutti gli elementi XML noti vengono elencati in tabelle e alberi, semplificando la lettura e la comprensione delle informazioni.

Il **XML** visualizzazione codice XML corrispondente alla traccia selezionata. Tale visualizzazione supporta l'evidenziazione e l'utilizzo dei colori per la sintassi. Quando si usa **trovare** per cercare le stringhe, vengono evidenziati i risultati della ricerca.

Il **messaggio** Vista sono riportati la parte del messaggio del codice XML nelle tracce del log dei messaggi. Tale visualizzazione è visibile solo quando si seleziona una traccia di messaggio.

### <a name="filtering-wcf-traces"></a>Filtro delle tracce WCF

Per semplificare l'analisi dei file di traccia è possibile filtrarli nei modi seguenti:

- la barra degli strumenti di filtro consente di accedere ai filtri predefiniti e personalizzati. Può essere abilitata tramite il **vista** menu.

- Il filtro predefinito del visualizzatore è utilizzabile per filtrare in modo selettivo parti delle tracce WCF. Per impostazione predefinita, tale filtro è impostato in modo da consentire il passaggio di tutte le tracce dell'infrastruttura. Le impostazioni di questo filtro vengono definite nel **opzioni di filtro** sottomenu **visualizzazione** menu.

- I filtri XPath personalizzati consentono agli utenti di avere il controllo completo sull'applicazione dei filtri. Possono essere definiti nel **filtro personalizzato** sotto **visualizzazione** menu.

Vengono visualizzate solo le tracce che passano attraverso tutti i filtri attivi.

#### <a name="using-the-filter-toolbar"></a>Utilizzo della barra degli strumenti di filtro

La barra degli strumenti di filtro si trova nella parte superiore dello strumento. Se non è presente, è possibile attivarla nella **vista** menu. La barra è costituita da tre componenti:

- Cercare: **Cercare** definisce l'oggetto da ricercare nell'operazione di filtro. Ad esempio, se si desidera trovare tutte le tracce generate nel contesto del processo X, impostare questo campo su X e il **Cerca In** campo "Nome processo". Quando si sceglie un filtro basato su tempo, questo campo diventa un controllo di selezione Datetime.

- Cerca: Questo campo definisce il tipo di filtro da applicare.

- Livello: Questa impostazione definisce il livello di traccia minimo consentito dal filtro. Ad esempio, se il livello è impostato su Errore e successivi, consente di visualizzare soltanto le tracce di livello Errore e Critico. I criteri di questo filtro vengono applicati insieme ai criteri specificati in Cerca e Cerca in.

Il **Filtra ora** pulsante Avvia l'operazione di filtro. L'applicazione di alcuni filtri, specialmente quando riguarda set di dati di grandi dimensioni, richiede molto tempo. È possibile annullare l'operazione di filtro, premere il **arrestare** pulsante visualizzato nella barra di stato sotto il **operazioni** menu.

Il **chiaro** pulsante Reimposta filtri predefiniti e personalizzati per consentire tutte le tracce per pass-through.

#### <a name="filter-options"></a>Opzioni di filtro

Il visualizzatore è in grado di rimuovere automaticamente dalla visualizzazione determinate tracce di WCF. La rimozione può riguardare in modo selettivo le tracce generate da aree specifiche di WCF, ad esempio le tracce relative alle transazioni.

Le impostazioni di questo filtro vengono definite nel **opzioni di filtro** sottomenu **visualizzazione** menu.

#### <a name="custom-filters"></a>Filtri personalizzati

Se si ha familiarità con il linguaggio Xpath (XML Path) è possibile utilizzarlo per creare filtri personalizzati finalizzati alla ricerca di dati di traccia correlati a qualsiasi elemento XML di interesse. I filtri sono accessibili tramite la barra degli strumenti di filtro.

I filtri personalizzati possono includere parametri. È inoltre possibile importare filtri personalizzati già esistenti.

##### <a name="creating-a-custom-filter"></a>Creazione di un filtro personalizzato

I filtri possono essere creati in due modi:

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Creazione di un filtro personalizzato tramite la Creazione guidata modelli

È possibile fare clic su una traccia esistente e creare un filtro basato sulla struttura della traccia. Questo esempio illustra la creazione di un filtro personalizzato basato sull'ID del thread.

1. Nel riquadro di traccia che si trova nella parte superiore destra del visualizzatore, selezionare la traccia contenente l'elemento su cui si desidera basare il filtro.

2. Scegliere il **Crea filtro personalizzato** pulsante nella parte superiore del riquadro delle tracce.

3. Nella finestra di dialogo visualizzata, immettere il nome del filtro. In questo esempio, immettere `Thread ID`. È inoltre possibile fornire una descrizione del filtro.

4. Nella visualizzazione albero a sinistra viene visualizzata la struttura del record di traccia selezionato nel passaggio 1. Passare all'elemento per il quale si desidera creare una condizione. In questo esempio, passare all'elemento ThreadID da individuare nella query XPath: /E2ETraceEvent/System/Execution/@ThreadID nodo. Fare doppio clic sull'attributo ThreadID contenuto nella visualizzazione albero. Nella parte destra della finestra di dialogo viene creata un'espressione per l'attributo.

5. Impostare il parametro per la condizione di ThreadID di tipo None in '{0}'. Questo passaggio fa in modo che il valore ThreadID venga configurato quando il filtro viene applicato. Per ulteriori informazioni, consultare la sezione relativa all'applicazione dei filtri. È possibile definire fino a quattro parametri. Le condizioni vengono combinate mediante l'operatore OR.

6. Fare clic su **accettabile** per creare il filtro.

> [!NOTE]
> I filtri creati tramite la Creazione guidata modelli possono essere modificati solo manualmente. Questa procedura guidata non può essere utilizzata su un filtro già esistente. Inoltre, se si utilizza la Creazione guidata modelli per creare un filtro Xpath, le condizioni di tale filtro vengono combinate tramite l'operatore OR. Di conseguenza, se si desidera impostare un operatore AND, l'espressione del filtro deve essere modificata manualmente.

###### <a name="creating-a-custom-filter-manually"></a>Creazione manuale di un filtro personalizzato

Il menu Filtri Personalizzati consente di immettere filtri XPath manualmente.

1. Nel menu Visualizza, fare clic sui **filtri personalizzati** voce di menu.

2. Nella finestra di dialogo visualizzata, fare clic su **New.**

3. Specificare almeno il nome e un'espressione Xpath del filtro.

4. Fare clic su **OK**.

###### <a name="applying-a-custom-filter"></a>Applicazione di un filtro personalizzato

Una volta creato un filtro personalizzato, tale filtro è accessibile tramite la barra degli strumenti di filtro. Selezionare il filtro da applicare nel **Cerca In** campo della barra degli strumenti di filtro. Per utilizzare l'esempio precedente, selezionare "ID thread".

1. Specificare il valore desiderato nel **Find What** campo. In questo esempio, immettere l'ID del thread da individuare.

2. Fare clic su **Filtra ora**e osservare il risultato dell'operazione.

Se il filtro utilizza più parametri, immetterli usando ';' come separatore nel **Find What** campo. Ad esempio, la stringa seguente definisce 3 parametri: ‘1;findValue;text’. Il Visualizzatore applica "1" per il {0} parametro del filtro. 'findValue' e 'text' vengono applicate a {1} e {2} rispettivamente.

###### <a name="sharing-custom-filters"></a>Condivisione di filtri personalizzati

I filtri personalizzati possono essere condivisi tra sessioni diverse e utenti diversi. È possibile esportare i filtri in un file di definizione e quindi importare questo file in un altro percorso.

 Per importare un filtro personalizzato:

1. Nel **View** menu, fare clic su **filtri personalizzati**.

2. Nella finestra di dialogo visualizzata, scegliere il **importazione** pulsante.

3. Passare al file del filtro personalizzato (con estensione stvcf), fare clic sul file e scegliere il **Open** pulsante.

Per esportare un filtro personalizzato:

1. Nel menu Visualizza, fare clic su **filtri personalizzati**.

2. Nella finestra di dialogo visualizzata, selezionare il filtro che si desidera esportare.

3. Scegliere il **esportare** pulsante.

4. Specificare il nome e percorso del file di definizione del filtro personalizzato (con estensione stvcf), quindi scegliere il **salvare** pulsante.

> [!NOTE]
> Questi filtri personalizzati possono essere importati ed esportati solo tramite lo strumento Visualizzatore di tracce dei servizi e non possono essere letti con altri strumenti.

### <a name="finding-data"></a>Ricerca dei dati

Il visualizzatore offre le modalità seguenti per la ricerca dei dati:

- La barra degli strumenti Trova consente di accedere rapidamente alle opzioni di ricerca più comuni.

- La finestra di dialogo Trova offre ulteriori opzioni di ricerca. È accessibile tramite il **modifica** dal menu o tramite i tasti Ctrl + F.

La barra degli strumenti Trova si trova nella parte superiore del visualizzatore. Se non è presente, è possibile attivarla nella **vista** menu. La barra è costituita da due componenti:

- Trova: Consente di immettere una parola chiave di ricerca.

- Cerca In: Consente di immettere l'ambito di ricerca. È possibile scegliere se eseguire la ricerca in tutte le attività o soltanto nell'attività corrente.

Nella finestra di dialogo Trova sono disponibili altre due opzioni:

- Trova destinazione:

  - L'opzione "dati di log non elaborati" Cerca la parola chiave in tutti i dati non elaborati.

  - Le opzioni "Testo XML" e "Nell'attributo XML" solo la ricerca negli elementi XML.

  - L'opzione "Messaggio registrato" Cerca la parola chiave solo nei messaggi.

- Ignora attività radice: La ricerca ignora le tracce di attività "000000000000". Ciò consente di migliorare le prestazioni nei file di traccia di grandi dimensioni quando l'attività radice presenta migliaia di tracce, per lo più relative a trasferimenti.

### <a name="navigating-traces"></a>Esplorazione delle tracce

Poiché le tracce vengono registrate in sequenza durante la fase di esecuzione dell'applicazione, l'esplorazione delle tracce può agevolarne il debug. Il Visualizzatore di tracce dei servizi offre varie opzioni di esplorazione delle tracce.

#### <a name="step-forward-or-backward"></a>Passo avanti o Passo indietro

Se si considera ogni traccia come una riga di codice nel programma, l'esecuzione di istruzioni in avanti è molto simile a "Esegui istruzione/routine" nell'ambiente di sviluppo integrato (IDE) di Visual Studio. A differenza di tale funzione, tuttavia, è inoltre possibile passare alla traccia precedente. Queste opzioni consentono di passare alla traccia successiva o precedente dell'attività.

- Passo avanti: Usare la **attività** menu o premere "F10". È inoltre possibile utilizzare tasto di direzione "giù" nel riquadro delle tracce.

- Passaggio con le versioni precedenti: Usare la **attività** menu o premere "F9". È inoltre possibile utilizzare tasto di direzione "up" nel riquadro delle tracce.

> [!NOTE]
> Questo è possibile accedere a un'attività che si verificano in un processo diverso o anche in un computer diverso, poiché messaggi WCF possono contenere ID che si estendono su macchine attività.

#### <a name="follow-transfer"></a>Trasferimento successivo

Le tracce di trasferimento sono tracce speciali del file di traccia che descrivono il trasferimento dell'esecuzione da un'attività a un'altra. Ad esempio, potrà trasferire "Attività A" in "Attività B". In tal caso, viene creata una traccia transfer nel "Attività di un" con il nome "a: Attività"e l'icona di trasferimento. Questa traccia di trasferimento è un collegamento tra le due tracce. In "Attività B", potrebbe anche esserci una traccia di trasferimento alla fine dell'attività da ritrasferire al "Attività A". Ciò è simile alle chiamate di funzione nei programmi: Un a chiama B, B restituisce quindi.

"Trasferimento successivo" è simile a "Esegui istruzione" in un debugger. consente di seguire il trasferimento dell'esecuzione da A a B, senza influire sulle altre tracce.

Esistono due modalità per eseguire questo tipo di esplorazione: tramite mouse o mediante tastiera.

- Tramite Mouse: Fare doppio clic sulla traccia di trasferimento nel riquadro delle tracce.

- Mediante tastiera: Selezionare una traccia di trasferimento e utilizzare "Trasferimento successivo" nel **attività** menu o premere "F11"

> [!NOTE]
> In molti casi, quando l'attività A trasferisce l'esecuzione all'attività B, l'attività A attende che l'attività B restituisca l'esecuzione. Di conseguenza, durante la registrazione di traccia dell'attività B, per l'attività A non viene eseguita alcuna registrazione di traccia. Tuttavia, è anche possibile che l'attività A non attenda l'attività B. In questo caso la registrazione di traccia dell'attività A continua normalmente. Un'altra possibilità è che l'attività B non restituisca l'esecuzione all'attività A. Ciò rappresenta una differenza rispetto alle chiamate di funzione. I trasferimenti fra le attività risultano più comprensibili se esaminati nella visualizzazione Grafico.

#### <a name="jump-to-next-or-previous-transfer"></a>Vai al trasferimento successivo o Vai al trasferimento precedente

Durante l'analisi dell'attività corrente o delle attività selezionate, quando vengono selezionate più attività, può essere utile individuare rapidamente le attività a cui viene trasferita l'esecuzione. "Vai al trasferimento successivo" consente di individuare la traccia di trasferimento successiva dell'attività. Dopo aver trovato la traccia di trasferimento, è possibile utilizzare "Trasferimento successivo" per passare all'attività successiva.

- Passare al trasferimento successivo: Usare la **attività** menu o premere "CTRL+F10".

- Vai al trasferimento precedente: Usare la **attività** menu o premere "CTRL+F9".

#### <a name="navigate-in-graph-view"></a>Esplorazione tramite la visualizzazione Grafico

Anche se lo spostamento nel riquadro attività e riquadro delle tracce è simile all'esecuzione del debug, usando **Graph** Vista fornisce una migliore esperienza di navigazione. Per altre informazioni vedere la sezione "Visualizzazione grafico".

### <a name="loading-large-trace-files"></a>Caricamento dei file di traccia di grandi dimensioni

I file di traccia possono essere di dimensioni notevoli. Ad esempio, se si abilita la traccia a livello "Dettagliato", il file di traccia risultante di esecuzione di pochi minuti può facilmente essere centinaia di MB o più, a seconda sul modello di velocità e la comunicazione di rete.

L'apertura di un file di traccia di grandi dimensioni nello strumento Visualizzatore di tracce dei servizi può comportare una riduzione delle prestazioni. È possibile che il caricamento risulti lento e che il tempo di risposta dopo il caricamento sia elevato. La velocità effettiva varia da caso a caso e dipende della configurazione hardware del sistema in uso. Nella maggior parte dei PC, il caricamento di un file di traccia più grande di 200 MB comporta una notevole riduzione delle prestazioni. Se il file di traccia presenta dimensioni superiori a 1 GB, è possibile che lo strumento utilizzi tutta la memoria disponibile o che risulti bloccato per un periodo di tempo molto lungo.

Per evitare il caricamento lento e il tempo di risposta per analizzare il file di traccia di grandi dimensioni, Service Trace Viewer è disponibile una funzionalità di caricamento "parziale", che carica solo una piccola parte della traccia in un momento. Si supponga ad esempio di disporre di un file di oltre 1 GB relativo a una traccia in esecuzione sul server da diversi giorni. In questo caso, qualora si verifichino errori, non è necessario aprire l'intero file di traccia. È invece possibile caricare soltanto le tracce relative all'intervallo di tempo in cui si ritiene che si siano verificati gli errori. Poiché l'ambito è ridotto, lo strumento Visualizzatore di tracce dei servizi può caricare il file più velocemente. L'identificazione degli errori può quindi essere svolta a partire da un set minore di dati.

#### <a name="enabling-partial-loading"></a>Abilitazione della funzionalità di caricamento parziale

La funzionalità di caricamento parziale non richiede l'abilitazione manuale. Se si tenta di caricare un set di file di traccia le cui dimensioni complessive sono maggiori di 40 MB, nello strumento Visualizzatore di tracce dei servizi viene aperta automaticamente una finestra di dialogo in cui è possibile selezionare la parte che si desidera caricare.

> [!NOTE]
> Poiché è possibile che le tracce non siano distribuite uniformemente nell'intervallo di tempo, l'ampiezza del periodo di tempo che si specifica nella barra degli strumenti della funzionalità di caricamento parziale potrebbe non essere proporzionale alle dimensioni di caricamento visualizzate. Le dimensioni di caricamento effettive possono essere minori rispetto alla stima visualizzata nella finestra di dialogo della funzionalità di caricamento parziale.

#### <a name="adjusting-partial-loading"></a>Impostazione dell'intervallo di tempo per il caricamento parziale

Dopo aver caricato parte del file di traccia, per modificare l'intervallo di tempo relativo al set di dati caricato è possibile regolare la barra degli strumenti della funzionalità di caricamento parziale che si trova nella parte superiore del visualizzatore.

1. Utilizzare il mouse per spostare la barra degli strumenti oppure immettere l'ora di inizio e di fine.

2. Scegliere il **Adjust** pulsante.

## <a name="understanding-trace-icons"></a>Descrizione delle icone di traccia

Di seguito è riportato un elenco di icone che utilizza lo strumento Service Trace Viewer il **attività** visualizzazione **Graph** visualizzazione e **traccia** riquadro per rappresentare elementi diversi.

> [!NOTE]
> Alcune tracce non suddivise per categoria (ad esempio, "un messaggio è stato chiuso") non hanno icona.

### <a name="activity-tracing-traces"></a>Tracce di attività

|Icona|Descrizione|
|----------|-----------------|
|![Traccia di avviso](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Traccia di avviso: Una traccia generata al livello di avviso|
|![Traccia di errore](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Traccia dell'errore: Una traccia generata al livello di errore.|
|![Traccia di inizio dell'attività:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Traccia di inizio dell'attività Una traccia che contrassegna l'inizio di un'attività. contenente il nome dell’attività. I progettisti dell’applicazione e gli sviluppatori devono definire una traccia d’inizio dell’attività per ogni ID attività per processo o thread.<br /><br /> Se l'ID attività viene propagato attraverso origini di traccia per la correlazione tra tracce, è possibile vedere più inizi per lo stesso ID attività (uno per ogni origine di traccia). La traccia di inizio viene emessa se è abilitata la funzione ActivityTracing per l'origine di traccia.|
|![Traccia di arresto dell'attività](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Traccia di arresto dell'attività: Una traccia che contrassegna la fine di un'attività. . contenente il nome dell’attività. I progettisti dell’applicazione e gli sviluppatori devono definire una traccia d’interruzione dell’attività per ogni ID attività per origine di traccia. Nessuna traccia derivante da una determinata origine di traccia viene visualizzata dopo che venga generata un’interruzione dell’attività da parte dell’origine di traccia, a meno che la granularità del tempo di traccia non sia sufficientemente piccola. In questo caso, durante la visualizzazione, può verificarsi un’esecuzione interleave di due tracce della stessa durata, comprendenti un’interruzione. Se l'ID attività viene propagato attraverso origini di traccia per la correlazione tra tracce, è possibile vedere più Interruzioni per lo stesso ID attività (una per ogni origine di traccia). La traccia di interruzione viene emessa se è abilitata la funzione ActivityTracing per l'origine di traccia.|
|![Traccia di sospensione dell'attività](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Traccia di sospensione dell'attività: È in pausa una traccia che contrassegna l'avvio di un'attività. Nessuna traccia è generata in un'attività sospesa finché l'attività non riprende. Un'attività sospesa indica che non si sta verificando nessuna elaborazione in quell'attività nell'ambito dell'origine della traccia. Le tracce di Sospensione/Ripresa sono utili per il profiling. La traccia di sospensione viene emessa se è abilitata la funzione ActivityTracing per l'origine di traccia.|
|![Attività di traccia di ripresa](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Traccia di ripresa dell'attività: Una traccia che indica il momento di che ripresa di un'attività dopo che era stato sospeso. Le tracce possono essere generate nuovamente in quell'attività. Le tracce di Sospensione/Ripresa sono utili per il profiling. La traccia di ripresa viene emessa se è abilitata la funzione ActivityTracing per l'origine di traccia.|
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Trasferimento: Una traccia generata quando il flusso di controllo logico viene trasferito da un'attività a un altro. L'attività originaria del trasferimento può continuare ad eseguire le operazioni in parallelo con l'attività che riceve il trasferimento. La traccia di trasferimento viene emessa se è abilitata la funzione ActivityTracing per l'origine di traccia.|
|![Da trasferire](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Trasferimento da: Una traccia che definisce il trasferimento da un'altra attività all'attività corrente.|
|![Trasferire](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Trasferimento a: Una traccia che definisce il trasferimento del flusso di controllo logico dall'attività corrente a un'altra attività.|

### <a name="wcf-traces"></a>Tracce WCF

|Icona|Descrizione|
|----------|-----------------|
|![Traccia Log dei messaggi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Traccia Log dei messaggi: Una traccia generata quando viene registrato un messaggio WCF tramite la funzionalità di registrazione dei messaggi, quando il `System.ServiceModel.MessageLogging` origine di traccia è abilitata. Facendo clic su questa traccia verrà visualizzato il messaggio. Esistono quattro punti di registrazione configurabili per un messaggio: ServiceLevelSendRequest, TransportSend, TransportReceive e ServiceLevelReceiveRequest che possono essere specificati anche dalla `messageSource` attributo nella traccia del log dei messaggi.|
|![Traccia messaggio ricevuto](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Traccia messaggio ricevuto: Una traccia generata quando viene ricevuto un messaggio WCF, se il `System.ServiceModel` origine di traccia è abilitata a livello di informazioni o dettagliato. Questa traccia è essenziale per visualizzare la freccia di correlazione di messaggi nell'attività **Graph** visualizzazione.|
|![Traccia messaggio inviato](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Traccia messaggio ricevuto: Una traccia generata quando viene inviato un messaggio WCF se il `System.ServiceModel` origine di traccia è abilitata a livello di informazioni o dettagliato. Questa traccia è essenziale per visualizzare la freccia di correlazione di messaggi nell'attività **Graph** visualizzazione.|

### <a name="activities"></a>Attività

|Icona|Descrizione|
|----------|-----------------|
|![Activity](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Attività: Indica che l'attività corrente è un'attività generica.|
|![Attività radice](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Attività radice: Indica l'attività radice di un processo.|

### <a name="wcf-activities"></a>Attività WCF

|Icona|Descrizione|
|----------|-----------------|
|![Attività dell'ambiente](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Attività dell'ambiente: Un'attività che crea, apre o chiude un host WCF o un client. Gli errori che si sono verificati durante queste fasi verranno visualizzati in questa attività.|
|![Attività Listen](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Attività Listen: Un'attività che si registra tracce riferite a un listener. In questa attività, si possono visualizzare informazioni e richieste di connessione del listener.|
|![Attività ricezione byte](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Attività ricezione byte: Attività che raduna tutte le tracce correlate alla ricezione di byte in ingresso su una connessione tra due endpoint. Questa attività è essenziale nelle correlazioni con le attività del trasporto che propagano l'ID attività, ad esempio http.sys. Errori di connessione, quali interruzioni, verranno visualizzati in questa attività.|
|![Attività elaborazione messaggio](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Attività elaborazione messaggio: Attività che raduna tracce riferite alla creazione di un messaggio WCF. Gli errori causati da envelope errata o da messaggi in formato non valido verranno visualizzati nell'attività. In questa attività, è possibile controllare le intestazioni del messaggio per vedere se un ID attività è stato propagato dal chiamante. In questo caso, quando si passa all’attività di tipo ProcessAction (icona successiva), si può inoltre assegnare a tale attività l'ID attività propagato per la correlazione tra tracce di chiamante e chiamato.|
|![Traccia Log dei messaggi](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Attività elaborazione azione: Attività che raduna tutte le tracce relative a una richiesta WCF tra due endpoint. Se `propagateActivity` è impostato su `true` su entrambi gli endpoint della configurazione, tutte le tracce da entrambi gli endpoint vengono incorporate in un'unica attività per correlazione diretta. Tale attività conterrà errori a causa dell’elaborazione nel trasporto o della sicurezza, che si estendono al limite del codice utente e viceversa (se esiste una risposta).|
|![Attività elaborazione messaggio](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Eseguire l'attività di codice utente: Attività che raduna tracce di codice utente per l'elaborazione di una richiesta.|

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se non si dispone delle autorizzazioni di scrittura nel Registro di sistema, viene visualizzato il messaggio di errore seguente "Microsoft Service Trace Viewer non è stato registrato nel sistema" quando si usa il "`svctraceviewer /register`" comando per registrare lo strumento. In questo caso è necessario accedere utilizzando un account che abbia accesso in scrittura al Registro di sistema.

Lo strumento Visualizzatore di tracce dei servizi scrive inoltre alcune impostazioni (ad esempio, filtri personalizzati e opzioni di filtro) nel file SvcTraceViewer.exe.settings nella cartella dell'assembly. Se non si dispone dell’autorizzazione in lettura per il file, è comunque possibile avviare lo strumento, ma non è possibile caricare le impostazioni.

Se, aprendo il file con estensione etl, viene visualizzato il messaggio di errore "Si è verificato un errore sconosciuto durante l'elaborazione di una o più tracce" vuole dire che il formato del file con estensione etl non è valido.

Se si apre un registro di traccia creato utilizzando un sistema operativo attivato per la lingua araba, è possibile che il filtro dell'ora non funzioni. Ad esempio, l'anno 2005 corrisponde all’anno 1427 del calendario arabo. L'intervallo di tempo supportato dal filtro dello strumento Visualizzatore di tracce dei servizi, tuttavia, non supporta una data antecedente al 1752. Questo può determinare l'impossibilità di selezionare una data corretta nel filtro. Per risolvere questo problema, è possibile creare un filtro personalizzato (**Visualizza/filtri personalizzati**) utilizzando un'espressione XPath per includere un intervallo di tempo specifico.

## <a name="see-also"></a>Vedere anche

- [Uso del visualizzatore di tracce dei servizi per la visualizzazione di tracce correlate e la risoluzione dei problemi](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Configurazione delle funzionalità di traccia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Traccia end-to-end](./diagnostics/tracing/end-to-end-tracing.md)
