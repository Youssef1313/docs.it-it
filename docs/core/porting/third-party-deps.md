---
title: Analizzare le dipendenze per convertire il codice per .NET Core
description: Informazioni su come analizzare le dipendenze esterne per convertire il progetto da .NET Framework a .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 5fa5a20e9a2b5427401835a0c1c6e1845d86c3ef
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798788"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analizzare le dipendenze per convertire il codice per .NET Core

Per convertire il codice a .NET Core o .NET Standard, è necessario conoscere le dipendenze. Le dipendenze esterne sono i pacchetti NuGet o `.dll`a cui si fa riferimento nel progetto, ma non vengono compilati personalmente.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Eseguire la migrazione dei pacchetti NuGet a `PackageReference`

.NET Core usa [PackageReference](/nuget/consume-packages/package-references-in-project-files) per specificare le dipendenze dei pacchetti. Se si usa [packages. config](/nuget/reference/packages-config) per specificare i pacchetti nel progetto, è necessario convertirli nel formato `PackageReference` perché `packages.config` non è supportato in .NET Core.

Per informazioni su come eseguire la migrazione, vedere l'articolo [eseguire la migrazione da Packages. config a PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) .

## <a name="upgrade-your-nuget-packages"></a>Aggiornare i pacchetti NuGet

Dopo la migrazione del progetto al formato `PackageReference`, è necessario verificare se i pacchetti sono compatibili con .NET Core.

Per prima cosa, aggiornare i pacchetti alla versione più recente. Questa operazione può essere eseguita con l'interfaccia utente di gestione pacchetti NuGet in Visual Studio. È probabile che le versioni più recenti delle dipendenze del pacchetto siano già compatibili con .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analizzare le dipendenze del pacchetto

Se non si è ancora verificato che le dipendenze dei pacchetti convertite e aggiornate funzionano in .NET Core, è possibile ottenere questo risultato in diversi modi:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizzare i pacchetti NuGet usando nuget.org

È possibile visualizzare i moniker del Framework di destinazione (TFM) supportati da ogni pacchetto in [NuGet.org](https://www.nuget.org/) nella sezione **dipendenze** della pagina del pacchetto.

Sebbene l'utilizzo del sito sia un metodo più semplice per verificare la compatibilità, le informazioni sulle **dipendenze** non sono disponibili nel sito per tutti i pacchetti.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analizzare i pacchetti NuGet usando NuGet Package Explorer

Un pacchetto NuGet è un set di cartelle contenenti assembly specifici per la piattaforma. Pertanto è necessario verificare se nel pacchetto è presente una cartella che contiene un assembly compatibile.

Il metodo più semplice per esaminare le cartelle del pacchetto NuGet è lo strumento [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Dopo aver installato lo strumento seguire questa procedura per visualizzare i nomi delle cartelle:

1. Aprire NuGet Package Explorer.
2. Fare clic su **Open package from online feed** (Apri il pacchetto dal feed online).
3. Cercare il nome del pacchetto.
4. Selezionare il nome del pacchetto nei risultati della ricerca e fare clic su **open** (Apri).
5. Espandere la cartella *lib* sul lato destro per visualizzare i nomi delle cartelle.

Cercare una cartella con i nomi usando uno dei modelli seguenti: `netstandardX.Y` o `netcoreappX.Y`.

Questi valori sono i [Target Framework Moniker (TFM)](../../standard/frameworks.md) che corrispondono a versioni dei profili [.NET Standard](../../standard/net-standard.md), .NET Core e dei tradizionali profili della libreria di classi portabile (PCL) compatibili con .NET Core.

> [!IMPORTANT]
> Quando si esaminano i TFM supportati da un pacchetto, si noti che `netcoreapp*` è compatibile, ma è destinato solo ai progetti .NET Core e non ai progetti .NET Standard.
> Una libreria che supporta solo `netcoreapp*` ma non `netstandard*` può essere usata solo da altre applicazioni .NET Core.

## <a name="net-framework-compatibility-mode"></a>Modalità di compatibilità di .NET Framework

Dopo aver analizzato i pacchetti NuGet, è possibile che siano destinati solo ai .NET Framework.

A partire da .NET Standard 2.0 è stata introdotta la modalità di compatibilità di .NET Framework. Questa modalità consente a progetti .NET Standard e .NET Core di gestire riferimenti a librerie .NET Framework. I riferimenti alle librerie .NET Framework non funzionano per tutti i progetti, ad esempio se la libreria usa API Windows Presentation Foundation (WPF), ma sono in grado di risolvere molti scenari di portabilità.

Quando nel progetto si fa riferimento a pacchetti NuGet che supportano .NET Framework, ad esempio [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), viene visualizzato un avviso di fallback del pacchetto ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) simile all'esempio seguente:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Questo avviso viene visualizzato quando si aggiunge il pacchetto e ogni volta che si esegue la compilazione, per garantire che il pacchetto venga testato con il progetto. Se il progetto funziona come previsto, è possibile eliminare l'avviso modificando le proprietà del pacchetto in Visual Studio o modificando manualmente il file di progetto nell'editor di codice preferito.

Per eliminare l'avviso modificando il file di progetto, trovare la voce `PackageReference` del pacchetto per il quale si vuole eliminare l'avviso e aggiungere l'attributo `NoWarn`. L'attributo `NoWarn` accetta un elenco delimitato da virgole di tutti gli ID avviso. L'esempio seguente illustra come eliminare l'avviso `NU1701` per il pacchetto `Huitian.PowerCollections` modificando manualmente il file di progetto:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Per altre informazioni sull'eliminazione degli avvisi del compilatore in Visual Studio, vedere [Non visualizzare avvisi per i pacchetti NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Operazioni da eseguire quando una dipendenza del pacchetto NuGet non viene eseguita in .NET Core

Se un pacchetto NuGet importante non può essere eseguito in .NET Core, è possibile provare varie soluzioni:

1. Se il progetto è open source e ospitato in una posizione come GitHub, è possibile coinvolgere direttamente gli sviluppatori.
2. È possibile contattare l'autore direttamente su [NuGet.org](https://www.nuget.org/). Cercare il pacchetto e fare clic su **Contact owners (Contatta i proprietari** ) sul lato sinistro della pagina del pacchetto.
3. È possibile cercare un altro pacchetto che supporta .NET Core ed esegue la stessa attività del pacchetto in uso.
4. È possibile tentare di scrivere autonomamente il codice eseguito dal pacchetto.
5. È inoltre possibile eliminare la dipendenza del pacchetto modificando la funzionalità dell'app, almeno fino a quando una versione compatibile del pacchetto non diventa disponibile.

Tenere presente che spesso i gestori di progetti open source e gli autori di pacchetti NuGet sono volontari. Questi utenti offrono il loro contributo a titolo gratuito perché sono interessati a un determinato argomento e in molti casi svolgono un'altra attività. Tenere presente questo aspetto quando si richiede loro supporto per .NET Core.

Se non si riesce a risolvere il problema con nessuna delle indicazioni precedenti, potrebbe essere necessario rimandare il trasferimento a .NET Core a una data successiva.

Il team .NET è interessato a sapere quali sono le librerie più importanti da supportare in .NET Core. È possibile inviare un messaggio di posta elettronica indicando le librerie preferite all'indirizzo dotnet@microsoft.com.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizzare le dipendenze che non sono pacchetti NuGet

Nel file system può essere presente una dipendenza diversa da un pacchetto NuGet, ad esempio una DLL. L'unico metodo per determinare la portabilità di tale dipendenza è l'esecuzione dello strumento [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). Lo strumento può analizzare gli assembly che supportano .NET Framework e identificare le API non trasferibili ad altre piattaforme .NET come .NET Core. È possibile eseguire lo strumento come applicazione console o come [estensione di Visual Studio](../../standard/analyzers/portability-analyzer.md).

>[!div class="step-by-step"]
>[avanti](libraries.md)
