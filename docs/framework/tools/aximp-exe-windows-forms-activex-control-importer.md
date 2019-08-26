---
title: Aximp.exe (utilità di importazione di controlli ActiveX di Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd3d7ea4d9639c5c68ecf977b4e95e816d99a4f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915430"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (utilità di importazione di controlli ActiveX di Windows Form)
L'utilità di importazione di controlli ActiveX converte in un controllo Windows Form le definizioni dei tipi in una libreria di tipi COM per un controllo ActiveX.  
  
 In Windows Form possono essere contenuti solo controlli Windows Form, ovvero classi derivate da <xref:System.Windows.Forms.Control>. Aximp.exe genera una classe wrapper per un controllo ActiveX che può essere ospitato in Windows Form. Questo consente di utilizzare lo stesso supporto per la fase di progettazione e la stessa metodologia di programmazione applicabili ad altri controlli Windows Form.  
  
 Per ospitare il controllo ActiveX, è necessario generare un controllo wrapper che derivi da <xref:System.Windows.Forms.AxHost>. Tale controllo contiene un'istanza del controllo ActiveX sottostante ed è in grado di comunicare con il controllo ActiveX pur avendo l'aspetto di un controllo Windows Form. Il controllo così generato ospita il controllo ActiveX e ne espone proprietà, metodi ed eventi come se fossero del controllo generato.  
  
 Viene installato automaticamente con Visual Studio. Per eseguire lo strumento, usare il Prompt dei comandi per gli sviluppatori per Visual Studio (o il prompt dei comandi di Visual Studio in Windows 7). Per altre informazioni, vedere [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Al prompt dei comandi digitare quanto segue:  
  
## <a name="syntax"></a>Sintassi  
  
```  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Osservazioni  
  
|Argomento|DESCRIZIONE|  
|--------------|-----------------|  
|*file*|Nome del file di origine contenente il controllo ActiveX da convertire. L'argomento del file deve avere l'estensione .dll oppure .ocx.|  
  
|Opzione|DESCRIZIONE|  
|------------|-----------------|  
|`/delaysign`|Specifica ad Aximp.exe di firmare il controllo risultante utilizzando la firma ritardata. È necessario specificare questa opzione con l'opzione `/keycontainer:`, `/keyfile:` o `/publickey:`. Per altre informazioni sulla firma ritardata, vedere [Ritardo della firma di un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).|  
|`/help`|Visualizza la sintassi e le opzioni di comando dello strumento.|  
|`/keycontainer:` *containerName*|Firma il controllo risultante con un nome sicuro usando la coppia di chiavi pubblica/privata presente nel contenitore di chiavi specificato da *containerName*.|  
|`/keyfile:` *filename*|Firma il controllo risultante con un nome sicuro usando la coppia di chiavi pubblica/privata ufficiale del server di pubblicazione trovata in *filename*.|  
|`/nologo`|Evita la visualizzazione del messaggio di avvio Microsoft.|  
|`/out:` *filename*|Specifica il nome dell'assembly da creare.|  
|`/publickey:` *filename*|Firma il controllo risultante con un nome sicuro usando la chiave pubblica presente nel file specificato da *filename*.|  
|`/rcw:` *filename*|Utilizza il Runtime Callable Wrapper specificato invece di generarne uno nuovo. È possibile specificare più istanze. La directory corrente viene usata per i percorsi relativi. Per altre informazioni, vedere la sezione [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) .|  
|`/silent`|Evita la visualizzazione dei messaggi di operazione riuscita.|  
|`/source`|Genera codice sorgente C# per il wrapper di Windows Form.|  
|`/verbose`|Specifica la modalità dettagliata. Visualizza ulteriori informazioni sullo stato.|  
|`/?`|Visualizza la sintassi e le opzioni di comando dello strumento.|  
  
 Aximp.exe converte un'intera libreria dei tipi di controlli ActiveX alla volta e produce un set di assembly contenenti i metadati di Common Language Runtime e l'implementazione dei controlli per i tipi definiti nella libreria dei tipi originale. I file generati vengono denominati in base ai criteri seguenti:  
  
 Proxy di Common Language Runtime per i tipi COM: *progid*.dll  
  
 Proxy di Windows Form per i controlli ActiveX (dove Ax significa ActiveX): Ax*progid*.dll  
  
> [!NOTE]
> Se il nome di un membro del controllo ActiveX corrisponde a un nome definito in .NET Framework, il nome del membro verrà fatto precedere dal prefisso "Ctl" durante la creazione della classe derivata da AxHost. Se, ad esempio, il controllo ActiveX contiene un membro denominato "Layout", questo verrà rinominato "CtlLayout" nella classe derivata da AxHost in quanto l'evento Layout è definito all'interno di .NET Framework.  
  
 È possibile esaminare i file generati con strumenti quali [Ildasm.exe (Disassembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
 L'utilizzo di Aximp.exe per generare un assembly .NET per il controllo ActiveX WebBrowser (shdocvw.dll) non è supportato.  
  
 L'esecuzione di Aximp.exe sul file shdocvw.dll comporterà sempre la creazione di un altro file denominato shdocvw.dll nella directory da cui viene eseguito lo strumento. L'inserimento nella directory Documents and Settings del file generato causerà problemi per Microsoft Internet Explorer ed Esplora risorse. Al riavvio del computer, viene eseguita una ricerca nella directory Documents and Settings prima che nella directory system32 per trovare una copia di shdocvw.dll. Verrà utilizzata la copia trovata in Documents and Settings e verrà effettuato un tentativo di caricamento dei wrapper gestiti. Internet Explorer ed Esplora risorse non funzioneranno correttamente in quanto dipendono dal motore di rendering della versione di shdocvw.dll presente nella directory system32. Se si verifica tale problema, eliminare la copia di shdocvw.dll nella directory Documents and Settings e riavviare il computer.  
  
 Anche l'utilizzo di Aximp.exe con shdocvw.dll per creare un assembly .NET da utilizzare nello sviluppo di un'applicazione può causare problemi. In questo caso, l'applicazione caricherà sia la versione del sistema di shdocvw.dll sia la versione generata ed è possibile che venga data priorità alla versione del sistema. In questa situazione, quando si tenta di caricare una pagina Web all'interno del controllo ActiveX WebBrowser è possibile che per l'utente venga visualizzata una finestra di dialogo Apri/Salva. Quando l'utente fa clic su **Apri** la pagina Web viene aperta in Internet Explorer. Ciò si verifica solo su computer in cui viene eseguito Internet Explorer versione 6 o precedenti. Per evitare questo problema, usare il controllo <xref:System.Windows.Forms.WebBrowser> gestito o usare Visual Studio per generare il file shdocvw.dll gestito come descritto in [ Procedura: Aggiungere riferimenti alle librerie dei tipi](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Esempio  
 Il comando che segue genera MediaPlayer.dll e AxMediaPlayer.dll per il controllo `msdxm.ocx` di Media Player.  
  
```  
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Vedere anche

- [Strumenti](../../../docs/framework/tools/index.md)
- [Ildasm.exe (Disassembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
