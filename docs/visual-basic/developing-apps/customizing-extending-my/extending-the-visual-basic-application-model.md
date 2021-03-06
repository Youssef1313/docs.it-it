---
title: Estensione del modello di applicazione Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 46c18ab540c90c4147514685c2acc824755b435f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976855"
---
# <a name="extending-the-visual-basic-application-model"></a>Estensione del modello di applicazione Visual Basic

È possibile aggiungere funzionalità al modello di applicazione eseguendo l'override dei membri `Overridable` della classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Questa tecnica consente di personalizzare il comportamento del modello applicativo e di aggiungere chiamate a metodi personalizzati quando l'applicazione viene avviata e arrestata.

## <a name="visual-overview-of-the-application-model"></a>Panoramica visiva del modello applicativo

In questa sezione viene illustrata visivamente la sequenza di chiamate di funzione nel modello di applicazione Visual Basic. Nella sezione successiva viene descritto in dettaglio lo scopo di ogni funzione.

Il grafico seguente mostra la sequenza di chiamate del modello applicativo in una normale Visual Basic Windows Forms Application. La sequenza viene avviata quando la procedura `Sub Main` chiama il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

![Diagramma che mostra la sequenza di chiamate del modello di applicazione.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Il modello di applicazione Visual Basic fornisce anche gli eventi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Nella grafica seguente viene illustrato il meccanismo per la generazione di questi eventi.

![Diagramma che mostra il metodo OnStartupNextInstance che genera l'evento StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagramma che mostra il metodo OnUnhandledException che genera l'evento UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Override dei metodi di base

Il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> definisce l'ordine in cui vengono eseguiti i metodi di `Application`. Per impostazione predefinita, la procedura `Sub Main` per un Windows Forms Application chiama il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

Se l'applicazione è un'applicazione normale (applicazione a più istanze) o la prima istanza di un'applicazione a istanza singola, il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> esegue i `Overridable` metodi nell'ordine seguente:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Per impostazione predefinita, questo metodo imposta gli stili visivi, gli stili di visualizzazione del testo e l'entità corrente per il thread principale dell'applicazione (se l'applicazione usa l'autenticazione di Windows) e chiama `ShowSplashScreen` se non viene usata né `/nosplash` né `-nosplash` come argomento della riga di comando.

     La sequenza di avvio dell'applicazione viene annullata se questa funzione restituisce `False`. Questa operazione può essere utile se si verificano circostanze in cui l'applicazione non deve essere eseguita.

     Il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> chiama i metodi seguenti:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Determina se l'applicazione dispone di una schermata iniziale definita e, in tal caso, Visualizza la schermata iniziale in un thread separato.

         Il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> contiene il codice che visualizza la schermata iniziale per almeno il numero di millisecondi specificato dalla proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>. Per usare questa funzionalità, è necessario aggiungere la schermata iniziale all'applicazione usando **Progettazione progetti** (che imposta la proprietà `My.Application.MinimumSplashScreenDisplayTime` su due secondi) oppure impostare la proprietà `My.Application.MinimumSplashScreenDisplayTime` in un metodo che esegue l'override del metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Per ulteriori informazioni, vedere <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> Consente a una finestra di progettazione di creare codice che inizializza la schermata iniziale.

         Per impostazione predefinita, questo metodo non effettua alcuna operazione. Se si seleziona una schermata iniziale per l'applicazione in **Progettazione progetti**Visual Basic, la finestra di progettazione esegue l'override del metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> con un metodo che imposta la proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> su una nuova istanza del form della schermata iniziale.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A> Fornisce un punto di estendibilità per la generazione dell'evento `Startup`. La sequenza di avvio dell'applicazione si interrompe se questa funzione restituisce `False`.

     Per impostazione predefinita, questo metodo genera l'evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>. Se il gestore dell'evento imposta la proprietà <xref:System.ComponentModel.CancelEventArgs.Cancel> dell'argomento dell'evento su `True`, il metodo restituisce `False` per annullare l'avvio dell'applicazione.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A> Fornisce il punto di partenza per il momento in cui l'applicazione principale è pronta per l'avvio, al termine dell'inizializzazione.

     Per impostazione predefinita, prima di immettere il Windows Forms ciclo di messaggi, questo metodo chiama il `OnCreateMainForm` (per creare il form principale dell'applicazione) e `HideSplashScreen` (per chiudere la schermata iniziale):

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> Consente a una finestra di progettazione di creare codice che inizializza il form principale.

         Per impostazione predefinita, questo metodo non effettua alcuna operazione. Tuttavia, quando si seleziona un form principale per l'applicazione in **Progettazione progetti**Visual Basic, la finestra di progettazione esegue l'override del metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> con un metodo che imposta la proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> su una nuova istanza del form principale.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A> Se l'applicazione ha una schermata iniziale definita ed è aperta, questo metodo chiude la schermata iniziale.

         Per impostazione predefinita, questo metodo chiude la schermata iniziale.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> Consente di personalizzare il comportamento di un'applicazione a istanza singola quando viene avviata un'altra istanza dell'applicazione.

     Per impostazione predefinita, questo metodo genera l'evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A> Fornisce un punto di estendibilità per la generazione dell'evento `Shutdown`. Questo metodo non viene eseguito se si verifica un'eccezione non gestita nell'applicazione principale.

     Per impostazione predefinita, questo metodo genera l'evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A> Eseguito se si verifica un'eccezione non gestita in uno dei metodi elencati in precedenza.

     Per impostazione predefinita, questo metodo genera l'evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> finché un debugger non è collegato e l'applicazione gestisce l'evento di `UnhandledException`.

 Se l'applicazione è un'applicazione a istanza singola e l'applicazione è già in esecuzione, l'istanza successiva dell'applicazione chiama il metodo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> sull'istanza originale dell'applicazione e quindi viene chiusa.

 Il costruttore <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> chiama la proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> per determinare quale motore di rendering del testo utilizzare per i moduli dell'applicazione. Per impostazione predefinita, la proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> restituisce `False`, che indica che viene utilizzato il motore di rendering del testo GDI, che è l'impostazione predefinita in Visual Basic 2005 e versioni successive. È possibile eseguire l'override della proprietà <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> per restituire `True`, che indica che viene utilizzato il motore di rendering del testo GDI+, che è l'impostazione predefinita in Visual Basic .NET 2002 e Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Configurazione dell'applicazione

 Come parte del modello di applicazione Visual Basic, la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fornisce proprietà protette per la configurazione dell'applicazione. Queste proprietà devono essere impostate nel costruttore della classe di implementazione.

 In un progetto Windows Forms predefinito, **Progettazione progetti** crea codice per impostare le proprietà con le impostazioni della finestra di progettazione. Le proprietà vengono usate solo quando l'applicazione viene avviata; l'impostazione dopo l'avvio dell'applicazione non ha alcun effetto.

|proprietà|Determina|Impostazione nel riquadro applicazione di progettazione progetti|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Indica se l'applicazione viene eseguita come applicazione a istanza singola o a più istanze.|Casella di controllo **Crea applicazione a istanza singola**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Se l'applicazione utilizzerà gli stili visivi che corrispondono a Windows XP.|Casella di controllo **Abilita stili di visualizzazione XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Se l'applicazione salva automaticamente le impostazioni utente dell'applicazione quando l'applicazione viene chiusa.|Casella **di controllo Salva My. Settings on Shutdown**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Cosa comporta l'interruzione dell'applicazione, ad esempio quando il modulo di avvio si chiude o quando l'ultimo form viene chiuso.|Elenco **modalità di arresto**|

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Cenni preliminari sul modello di applicazione Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Pagina Applicazione, Creazione progetti (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
