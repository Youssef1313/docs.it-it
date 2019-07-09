---
title: Strategia di sicurezza di WPF - Sicurezza della piattaforma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: f99a9f38d5fbb62732f157720ee544042e346469
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663569"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia di sicurezza di WPF - Sicurezza della piattaforma
Anche se Windows Presentation Foundation (WPF) offre un'ampia gamma di servizi di sicurezza, sfrutta le funzionalità di sicurezza della piattaforma sottostante, che include il sistema operativo, il [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], e [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Questi livelli forniscono a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] un modello di sicurezza in profondità solido e dettagliato per evitare ogni singola vulnerabilità, come illustrato nella figura seguente:  
  
 ![Diagramma che mostra il modello di sicurezza WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Nella parte rimanente di questo argomento verranno illustrate le funzionalità specifiche di questi livelli che riguardano in modo specifico [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)].  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Sicurezza del sistema operativo  
 Il livello minimo di sistema operativo richiesto da [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] è [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Il nucleo della [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] fornisce numerose funzionalità di sicurezza che costituiscono la base di sicurezza per tutte le applicazioni di Windows, incluse quelle compilate con [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] incorpora, ed estende, le funzionalità di sicurezza di [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Questo argomento mostra quali di queste funzionalità di sicurezza sono importanti per [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] e descrive come si integrano in [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] per formare un solido sistema di difesa in profondità.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oltre a una revisione generale e un approfondimento su Windows, esistono tre funzionalità chiave disponibili in [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] verranno illustrate in questo argomento:  
  
- Compilazione /GS  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>Compilazione /GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] offre protezione ricompilando molte librerie di sistema principali, incluse tutte le dipendenze [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] quali [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], per limitare i sovraccarichi del buffer. A tale scopo, è necessario usare il parametro /GS con il compilatore da riga di comando di C/C++. Anche se i sovraccarichi del buffer dovrebbero essere evitati in modo esplicito, la compilazione /GS rappresenta un esempio di difesa da potenziali vulnerabilità create accidentalmente o intenzionalmente.  
  
 In passato i sovraccarichi del buffer sono stati causa di molte violazioni della sicurezza a impatto elevato. Si verifica un sovraccarico del buffer quando un utente malintenzionato sfrutta una vulnerabilità del codice per introdurre codice dannoso che viene scritto oltre i limiti di un buffer. Il malintenzionato sarà così in grado di assumere il controllo del processo in cui il codice è in esecuzione, sovrascrivendo l'indirizzo di ritorno di una funzione per indurre l'esecuzione del proprio codice dannoso. Il risultato sarà l'esecuzione di codice arbitrario attraverso codice dannoso con gli stessi privilegi del processo di cui è stato assunto il controllo.  
  
 In generale, il flag del compilatore /GS protegge da alcuni potenziali sovraccarichi del buffer introducendo uno speciale cookie di sicurezza per proteggere l'indirizzo di ritorno di una funzione dotata di buffer di stringhe locali. Dopo la restituzione di un risultato da parte di una funzione, il cookie di sicurezza viene confrontato con il suo valore precedente. Se il valore è cambiato, è possibile che si sia verificato un sovraccarico del buffer e che il processo venga interrotto con una condizione di errore. L'interruzione del processo impedisce l'esecuzione di codice potenzialmente dannoso. Visualizzare [/GS (controllo sicurezza Buffer)](/cpp/build/reference/gs-buffer-security-check) per altri dettagli.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] è compilato con il flag /GS per aggiungere un ulteriore livello di difesa alle applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)].  
  
#### <a name="microsoft-windows-update-enhancements"></a>Miglioramenti a Microsoft Windows Update  
 Anche [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] è stato migliorato in [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] per semplificare il processo di download e installazione degli aggiornamenti. Queste modifiche migliorano in modo sostanziale la sicurezza per i clienti [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] in quanto contribuiscono a garantire che i sistemi siano sempre aggiornati, in modo specifico per quanto riguarda la sicurezza.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 Gli utenti [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] in [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] trarranno numerosi vantaggi dai miglioramenti apportati alla sicurezza del sistema operativo, inclusi l'accesso utente con privilegi minimi, i controlli di integrità del codice e l'isolamento dei privilegi.  
  
#### <a name="user-account-control-uac"></a>Controllo dell'account utente  
 Oggi, gli utenti Windows tendono a eseguire con privilegi di amministratore perché molte applicazioni richiedono li per installazione o l'esecuzione o entrambi. La scrittura delle impostazioni predefinite di un'applicazione nel Registro di sistema ne è un esempio.  
  
 Usare i privilegi di amministratore per eseguire un'applicazione significa che l'applicazione viene eseguita da processi a cui sono stati concessi i privilegi di amministratore. In termini di sicurezza, ciò significa che eventuale codice dannoso che assume il controllo di un processo eseguito con privilegi di amministratore erediterà automaticamente quei privilegi, incluso l'accesso a risorse di sistema critiche.  
  
 Un modo per proteggersi da una tale minaccia per la sicurezza consiste nell'eseguire le applicazioni con la quantità minima necessaria di privilegi. Questo concetto è noto come il principio dei privilegi minimi ed è una funzionalità principale del sistema operativo [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]. Tale funzionalità è nota come Controllo dell'account utente (UAC, User Account Control) e viene usata da [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] in due modi principali:  
  
- Per eseguire la maggior parte delle applicazioni con privilegi UAC per impostazione predefinita, anche se l'utente è un amministratore. Solo le applicazioni che richiedono i privilegi di amministratore verranno eseguite con i privilegi di amministratore. Per essere eseguite con i privilegi di amministratore, le applicazioni devono essere contrassegnate in modo esplicito nel manifesto dell'applicazione o come voce nei criteri di sicurezza.  
  
- Per fornire soluzioni di compatibilità come la virtualizzazione. Molte applicazioni, ad esempio, provano a scrivere in percorsi limitati, come C:\Programmi. Per le applicazioni eseguite in ambito UAC, esiste un percorso alternativo specifico di ogni utente in cui è possibile scrivere senza disporre dei privilegi di amministratore. Per le applicazioni eseguite in ambito UAC, il percorso C:\Programmi viene virtualizzato affinché le applicazioni scrivano direttamente nel percorso alternativo specifico di ogni utente. Questa soluzione di compatibilità consente di eseguire molte applicazioni che in passato non sarebbe stato possibile eseguire in base al principio UAC.  
  
#### <a name="code-integrity-checks"></a>Controlli di integrità del codice  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] incorpora controlli di integrità del codice più accurati per impedire che venga introdotto codice dannoso nei file di sistema o nel kernel in fase di esecuzione/caricamento. Questo va oltre la protezione dei file di sistema.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processo con diritti limitati per le applicazioni ospitate nei browser  
 Le applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ospitate nei browser vengono eseguite nella sandbox dell'area Internet. L'integrazione di [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] con [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] migliora ulteriormente questa protezione con supporto aggiuntivo.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 e Internet Explorer 7 per XP  
 Per fornire funzionalità di sicurezza ancora più avanzate, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sfrutta il modello di sicurezza del sistema operativo limitando i privilegi del processo per le [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Prima che venga avviata un'applicazione [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ospitata da un browser, il sistema operativo crea un processo host che rimuove i privilegi non necessari dal token del processo. Alcuni esempi di privilegi rimossi includono le autorizzazioni ad arrestare il computer dell'utente, a caricare i driver e ad accedere in lettura a tutti i file nel computer.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7 per Vista  
 In [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], le applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] vengono eseguite in modalità protetta. In modo specifico, le [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] vengono eseguite con integrità di livello medio.  
  
#### <a name="defense-in-depth-layer"></a>Livello di difesa in profondità  
 Poiché le [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] vengono in genere eseguite in una sandbox in base al set di autorizzazioni dell'area Internet, la rimozione di questi privilegi non danneggia, da un punto di vista della compatibilità, tali [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Viene invece creato un livello di difesa aggiuntivo; se un'applicazione eseguita in una sandbox è in grado di sfruttare altri livelli e di assumere il controllo del processo, il processo disporrà comunque unicamente di privilegi limitati.  
  
 Visualizzare [utilizzando un Account utente con privilegi minimi](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Sicurezza di Common Language Runtime (CLR)  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] offre numerose funzionalità di sicurezza tra cui convalida e verifica, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] e metodologia critica per la sicurezza.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Convalida e verifica  
 Per garantire l'integrità e l'isolamento degli assembly, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] si basa su un processo di convalida. La convalida di [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] garantisce che gli assembly vengano isolati convalidando il loro formato di file eseguibile di tipo PE (Portable Executable) per indirizzi che puntano all'esterno dell'assembly. La convalida di [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] esegue inoltre la convalida dell'integrità dei metadati incorporati in un assembly.  
  
 Per assicurare l'indipendenza, aiutare a evitare problemi di sicurezza comuni (ad esempio i sovraccarichi del buffer) e abilitare l'uso delle sandbox tramite l'isolamento dei processi secondari, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] sicurezza si basa sul concetto di verifica.  
  
 Le applicazioni gestite vengono compilate in Microsoft Intermediate Language (MSIL). Quando vengono eseguiti metodi in un'applicazione gestita, il relativo MSIL viene compilato in codice nativo tramite la compilazione JIT. La compilazione JIT include un processo di verifica riguardante molte regole di sicurezza e affidabilità per garantire che il codice:  
  
- non violi contratti di tipo  
  
- non causi sovraccarichi del buffer  
  
- non acceda alla memoria in modo irregolare o eccessivo.  
  
 Il codice gestito che non rispetta le regole di verifica non verrà eseguito, a meno che non venga considerato codice attendibile.  
  
 Il vantaggio di codice verificabile è i motivi principali per cui [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] si basa su .NET Framework. Pertanto, più esteso sarà l'uso di codice verificabile, minori saranno le possibilità di sfruttare le vulnerabilità del sistema.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Sicurezza per l'accesso al codice  
 Un computer client espone un'ampia varietà di risorse a cui un'applicazione gestita ha accesso, ad esempio il file system, il Registro di sistema, i servizi di stampa, l'interfaccia utente, la reflection e le variabili di ambiente. Prima di un'applicazione gestita può accedere a tutte le risorse in un computer client, è necessario disporre dell'autorizzazione di .NET Framework per eseguire questa operazione. Un'autorizzazione in [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] è una sottoclasse di <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementa una sottoclasse per ogni risorsa a cui possono accedere le applicazioni gestite.  
  
 Le autorizzazioni concesse a un'applicazione gestita da [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] all'avvio vengono collettivamente definite set di autorizzazioni e tale set è determinato dalle evidenze fornite dall'applicazione. Per le applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], le evidenze fornite sono il percorso, o area, da cui vengono avviate. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identifica le aree seguenti:  
  
- **Risorse del computer**. Applicazioni avviate dal computer client (completamente attendibili).  
  
- **Intranet locale**. Applicazioni avviate da Intranet (parzialmente attendibili).  
  
- **Internet**. Applicazioni avviate da Internet (meno attendibili).  
  
- **Siti attendibili**. Applicazioni identificate da un utente come attendibili (meno attendibili).  
  
- **Siti non attendibili**. Applicazioni identificate da un utente come non attendibili (non attendibili).  
  
 Per ognuna di queste zone, [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] fornisce un set di autorizzazioni predefinito che include le autorizzazioni corrispondenti al livello di attendibilità associato a ognuna, Sono inclusi:  
  
- **FullTrust**. Per le applicazioni avviate dal **My Computer** zona. Sono concesse tutte le autorizzazioni possibili.  
  
- **LocalIntranet**. Per le applicazioni avviate dal **Intranet locale** zona. Viene concesso un sottoinsieme di autorizzazioni per fornire un accesso moderato alle risorse di un computer client, tra cui spazio di memorizzazione isolato, accesso dell'interfaccia utente senza restrizioni, finestre di dialogo di file senza restrizioni, reflection limitata, accesso limitato alle variabili di ambiente. Le autorizzazioni per risorse critiche come il Registro di sistema non vengono concesse.  
  
- **Internet**. Per le applicazioni avviate dal **Internet** oppure **siti attendibili** zona. Viene concesso un sottoinsieme di autorizzazioni per fornire accesso limitato alle risorse di un computer client, tra cui spazio di memorizzazione isolato, solo apertura di file e interfaccia utente limitata. In pratica, questa autorizzazione impostata isola le applicazioni dal computer client.  
  
 Applicazioni identificate come provenienti dal **siti non attendibili** zona non concede alcuna autorizzazione dal [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] affatto. Di conseguenza, queste non dispongono di alcun set di autorizzazioni predefinito.  
  
 Nella figura seguente illustra la relazione tra le zone, set di autorizzazioni, autorizzazioni e le risorse:  
  
 ![Diagramma che mostra i set di autorizzazioni CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Le restrizioni della sandbox di sicurezza dell'area Internet sono ugualmente applicabili a qualsiasi codice che un'applicazione [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] importa da una libreria di sistema, compreso [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. In questo modo, ogni frammento di codice viene bloccato, anche [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Purtroppo, per poter essere eseguita, un'applicazione [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] deve eseguire funzionalità che richiedono molte più autorizzazioni rispetto a quelle abilitate dalla sandbox di sicurezza dell'area Internet.  
  
 Si consideri un'applicazione [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] contenente la seguente pagina:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Per eseguire questa applicazione [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], il codice [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sottostante deve eseguire molte più funzionalità di quelle disponibili all'applicazione [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] chiamante, tra cui:  
  
- Creazione di un handle di finestra (HWND) per il rendering  
  
- Invio di messaggi  
  
- Caricamento del tipo di carattere Tahoma  
  
 Da un punto di vista della sicurezza, consentire l'accesso diretto a queste operazioni dall'applicazione eseguita in una sandbox avrebbe conseguenze devastanti.  
  
 Fortunatamente, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] affronta questa situazione consentendo di eseguire le operazioni con privilegi elevati per conto dell'applicazione eseguita in una sandbox. Mentre tutte le [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operazioni vengono confrontate con autorizzazioni di sicurezza limitate dell'area Internet del dominio dell'applicazione il [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (come con altre librerie di sistema) viene concesso un set di autorizzazioni che include tutte le possibili autorizzazioni.
  
 È quindi necessario che [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] riceva privilegi elevati, ma è altresì fondamentale impedire che tali privilegi vengano determinati dal set di autorizzazioni dell'area Internet del dominio dell'applicazione host.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] viene eseguita usando il **Assert** metodo di un'autorizzazione. Nel codice riportato di seguito viene illustrata questa operazione.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Il **Assert** impedisce che le autorizzazioni illimitate richieste da [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] vengano limitate dalle Internet autorizzazioni dell'area di [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)].  
  
 Da una prospettiva, piattaforma [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] è responsabile dell'uso **Assert** correttamente; un utilizzo non corretto del **Assert** potrebbe consentire a codice dannoso di elevare i privilegi. Di conseguenza, è importante quindi a chiamare solo **Assert** quando necessario, e per assicurarsi che sandbox rimangano inalterate le restrizioni. Ad esempio, al codice sandbox non è consentita l'apertura di file casuali, ma è consentito l'uso dei tipi di carattere. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] consente alle applicazioni sandbox di usare funzionalità del tipo di carattere chiamando **Assert**e per [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] per leggere i file che contengono tali caratteri per conto dell'applicazione sandbox.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Distribuzione ClickOnce  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] è una tecnologia di distribuzione completa inclusa in .NET Framework e si integra con [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (vedere [ClickOnce sicurezza e distribuzione](/visualstudio/deployment/clickonce-security-and-deployment) per informazioni dettagliate). Le applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] autonome possono essere distribuite tramite [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], mentre le applicazioni ospitate da un browser devono essere distribuite con [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Alle applicazioni distribuite tramite [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] viene fornito un ulteriore livello di sicurezza su[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; sostanzialmente, le applicazioni distribuite tramite [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] richiedono le autorizzazioni di cui hanno bisogno. A tali applicazioni vengono concesse solo quelle autorizzazioni se non superano l'insieme di autorizzazioni dell'area da cui vengono distribuite. Per ridurre il set di autorizzazioni solo a quelli necessari, anche se sono inferiori a quelle fornite da autorizzazioni dell'area di avvio impostato, il numero di risorse che l'applicazione abbia accesso a viene ridotto al minimo. Di conseguenza, se si perde il controllo dell'applicazione, le vulnerabilità del computer client saranno ridotte.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia critica per la sicurezza  
 Il codice [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] che usa autorizzazioni per abilitare la sandbox dell'area Internet per le applicazioni [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] deve essere mantenuto al livello più elevato possibile di controllo della sicurezza. Per facilitare questo requisito, .NET Framework fornisce un nuovo supporto per la gestione del codice che eleva i privilegi. In particolare, il [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] consente di identificare il codice che eleva i privilegi e contrassegnarla con il <xref:System.Security.SecurityCriticalAttribute>; qualsiasi codice non contrassegnato con <xref:System.Security.SecurityCriticalAttribute> diventa *trasparente* usando questa metodologia. Viceversa, il codice gestito non contrassegnato con <xref:System.Security.SecurityCriticalAttribute> non può elevare i privilegi.  
  
 La metodologia critico per la sicurezza consente di organizzare [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] codice che eleva i privilegi nel *kernel critico per la sicurezza*, mentre il resto diventa trasparente. Isolando il codice critico per la sicurezza consente la [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] team di progettazione concentrare l'attenzione di un controllo di origine e all'analisi aggiuntiva di sicurezza nel kernel critico per la sicurezza oltre alle procedure di sicurezza standard (vedere [strategia di sicurezza di WPF -Progettazione della sicurezza](wpf-security-strategy-security-engineering.md)).  
  
 Si noti che .NET Framework consente al codice attendibile di estendere il [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] sandbox dell'area Internet, consentendo agli sviluppatori di scrivere assembly gestiti contrassegnati con <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) e distribuiti alla Global Assembly Cache (GAC) dell'utente. Contrassegnare un assembly con APTCA è un'operazione estremamente delicata dal punto di vista della sicurezza in quanto consente a qualsiasi codice di chiamare quell'assembly, incluso eventuale codice dannoso proveniente da Internet. È necessario esercitare massima cautela, seguire le procedure consigliate e gli utenti devono scegliere di considerare attendibile un programma software per poterlo installare.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Sicurezza di Microsoft Internet Explorer  
 Oltre a ridurre i problemi di sicurezza e a semplificare la configurazione della sicurezza, [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] contiene molte funzionalità che migliorano la sicurezza degli utenti di [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Tramite queste funzionalità si tenta di fornire agli utenti un maggiore controllo sulla loro esperienza di esplorazione.  
  
 Prima di [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], gli utenti potevano riscontrare le situazioni elencate di seguito:  
  
- Finestre popup casuali.  
  
- Reindirizzamento di script non chiaro.  
  
- Numerose finestre di dialogo di sicurezza in alcuni siti Web.  
  
 In alcuni casi, i siti Web non attendibili provano a ingannare gli utenti effettuando lo spoofing della [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] di installazione o visualizzando ripetutamente una finestra di dialogo di installazione di [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)], anche se l'utente la ha annullata. Tramite queste tecniche, è possibile che un numero significativo di utenti sia stato indotto a prendere decisioni che hanno causato l'installazione di applicazioni spyware.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] include molte funzionalità per contenere questi tipi di problemi, che vertono sul concetto di inizializzazione da parte dell'utente. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] rileva quando un utente ha fatto clic su un elemento di collegamento o di pagina prima un'azione che è noto come *inizializzazione parte dell'utente*ed espone un comportamento diverso rispetto a quando un'azione simile viene attivata tramite script in una pagina. Ad esempio, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] incorpora un **popup** che rileva quando un utente fa clic su un pulsante prima che la pagina Creazione di una finestra popup. In questo modo, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] consente i popup più innocui, mentre blocca quelli non richiesti né desiderati dagli utenti. I popup bloccati vengono intercettati sotto la nuova **sulla barra informazioni**, che consente all'utente di manualmente l'override del blocco e di visualizzare la finestra popup.  
  
 La stessa logica di inizializzazione da parte dell'utente viene applicata anche a **aperto**/**salvare** richieste di sicurezza. Le finestre di dialogo di installazione di [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] vengono sempre intercettate sotto la barra informazioni, a meno che non rappresentino un aggiornamento da un controllo installato in precedenza. Queste misure consentono agli utenti un'esperienza più controllata e sicura, perché sono protetti da quei siti che con l'inganno inducono a installare software indesiderato o dannoso.  
  
 Queste funzionalità proteggono inoltre i clienti che usano [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] per esplorare siti Web che consentono loro di scaricare e installare applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. In particolare, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] consente una migliore esperienza che riduce le possibilità di installare applicazioni dannose indipendentemente dalla tecnologia usata per compilarle, incluso [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] migliora ulteriormente la sicurezza poiché si basa sull'uso di [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] per facilitare il download di applicazioni da Internet. Poiché le [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] vengono eseguite all'interno di una sandbox di sicurezza dell'area Internet, possono essere avviate senza problemi. Al contrario, l'esecuzione delle applicazioni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] autonome richiede attendibilità completa. Per queste applicazioni, [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] visualizza una finestra di dialogo di sicurezza durante il processo di avvio, per notificare l'uso dei requisiti di sicurezza aggiuntivi dell'applicazione. Questa operazione, che deve essere avviata dall'utente, verrà determinata dalla logica avviata dall'utente e potrà essere annullata.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] incorpora ed estende le funzionalità di sicurezza di [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] in un impegno costante rivolto alla sicurezza.  
  
## <a name="see-also"></a>Vedere anche

- [Sicurezza dall'accesso di codice](../misc/code-access-security.md)
- [Sicurezza](security-wpf.md)
- [Sicurezza con attendibilità parziale in WPF](wpf-partial-trust-security.md)
- [Strategia di sicurezza WPF - Progettazione della sicurezza](wpf-security-strategy-security-engineering.md)
