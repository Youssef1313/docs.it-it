---
title: Sviluppo per piattaforme multiple con .NET Framework
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2167f74c5d1dd9f49995b6407e65feb474084dc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641432"
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>Sviluppo per piattaforme multiple con .NET Framework

Con .NET Framework e Visual Studio è possibile sviluppare app per piattaforme Microsoft e non Microsoft.
  
## <a name="options-for-cross-platform-development"></a>Opzioni per lo sviluppo multipiattaforma

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 Per sviluppare applicazioni per più piattaforme è possibile condividere il codice sorgente ed effettuare chiamate tra il codice .NET Framework e le API di Windows Runtime.  
  
|Per...|Usare...|  
|-----------------------|------------|  
|Condividere codice sorgente tra app Windows Phone 8.1 e app Windows 8.1|**Progetti condivisi** (modello di App universali in Visual Studio 2013 Update 2).<br /><br /> -Attualmente alcun supporto per Visual Basic.<br />-È possibile separare il codice specifico della piattaforma usando &`if` istruzioni.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Iniziare a scrivere codice](/windows/uwp/get-started/create-uwp-apps)<br />-   [Usa Visual Studio per creare App XAML universali](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (post di blog)<br />-   [Con Visual Studio per compilare le app con convergenza di XAML](https://channel9.msdn.com/Events/Build/2014/3-591) (video)|  
|Condividere i binari tra app destinate a piattaforme diverse|**Progetti libreria di classi portabile** per il codice che è indipendente dalla piattaforma.<br /><br /> -Questo approccio viene in genere usato per il codice che implementa la logica di business.<br />-È possibile usare Visual Basic o c#.<br />-Supporto per API varia a seconda della piattaforma.<br />-Progetti libreria di classi portabili destinate a Windows 8.1 e Windows Phone 8.1 supportano APIs di Windows Runtime e XAML. Queste funzionalità non sono disponibili nelle versioni precedenti di Libreria di classi portabile.<br />-Se necessario, è possibile astrarre il codice specifico della piattaforma usando interfacce o classi astratte.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Libreria di classi portabile](cross-platform-development-with-the-portable-class-library.md)<br />-   [Come rendere usare le librerie di classi portabile per l'utente](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/) (post di blog)<br />-   [Uso di libreria di classi portabile con MVVM](using-portable-class-library-with-model-view-view-model.md) <br />-   [Risorse dell'App per librerie destinate a piattaforme Multiple](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (estensione di Visual Studio)|  
|Condividere codice sorgente tra app per piattaforme diverse da Windows 8.1 e Windows Phone 8.1|**Aggiungi come collegamento** funzionalità.<br /><br /> -Questo approccio è adatto per la logica che è comune a entrambe le app, ma non è portabile per qualche motivo. È possibile usare questa funzionalità per il codice C# o Visual Basic.<br />     Ad esempio, Windows Phone 8 e Windows 8 condividono le API di Windows Runtime, ma le librerie di classi portabili non supportano Windows Runtime per queste piattaforme. È possibile usare `Add as link` per condividere il codice Windows Runtime tra un'app Windows Phone 8 e un'app di Windows Store destinata a Windows 8.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Condividere codice con Aggiungi come collegamento](https://docs.microsoft.com/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [Procedura: Aggiungere elementi esistenti a un progetto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|Scrivere app di Windows Store usando .NET Framework o chiamare API di Windows Runtime API dal codice .NET Framework|**Windows Runtime APIs** dal codice .NET Framework c# o Visual Basic e usare .NET Framework per creare App Windows Store. È opportuno tenere presenti le differenze relative alle API tra le due piattaforme, tuttavia sono disponibili classi che agevolano la gestione di queste differenze.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Supporto di .NET framework per le app di Windows Store e Windows Runtime](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Passaggio di un URI per il Runtime di Windows](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|Sviluppare app .NET Framework per piattaforme non Microsoft|**Gli assembly di riferimento di libreria di classi portabili** in .NET Framework e uno strumento di terze parti o estensione di Visual Studio, ad esempio Xamarin.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Libreria di classi portabile ora disponibile in tutte le piattaforme.](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (post di blog)<br />-   [Documentazione di Xamarin](/xamarin)|  
|Usare JavaScript e HTML per lo sviluppo multipiattaforma|**Modelli di App universali** in Visual Studio 2013 Update 2 per lo sviluppo utilizzando Windows Runtime APIs per Windows 8.1 e Windows Phone 8.1. Attualmente non è possibile usare JavaScript e HTML con le API .NET Framework per sviluppare app multipiattaforma.<br /><br /> Per informazioni dettagliate, vedere:<br /><br /> -   [Modelli di progetto JavaScript](https://docs.microsoft.com/previous-versions/windows/apps/hh758331%28v=win.10%29)<br />-   [Porting di un'app di Windows Runtime scritte in JavaScript per Windows Phone](https://docs.microsoft.com/previous-versions/windows/apps/dn636144%28v=win.10%29)|
