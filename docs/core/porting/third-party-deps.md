---
title: Analizzare le dipendenze per convertire il codice per .NET Core
description: Informazioni su come analizzare le dipendenze esterne per convertire il progetto da .NET Framework a .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521481"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analizzare le dipendenze per convertire il codice per .NET Core

Per convertire il codice a .NET Core o .NET Standard, è necessario conoscere le dipendenze. Le dipendenze esterne sono i [pacchetti NuGet](#analyze-referenced-nuget-packages-in-your-projects) o le [DLL](#analyze-dependencies-that-arent-nuget-packages) a cui si fa riferimento nel progetto, ma che non si compilano. È necessario valutare le singole dipendenze e definire un piano di emergenza per quelle non compatibili con .NET Core. Ecco come determinare se una dipendenza è compatibile con .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a>Analizzare i pacchetti NuGet cui si fa riferimento nei progetti

Se il progetto contiene riferimenti a pacchetti NuGet, è necessario verificare se i pacchetti sono compatibili con .NET Core.
È possibile ottenere questo risultato in due modi:

- [Tramite l'app NuGet Package Explorer](#analyze-nuget-packages-using-nuget-package-explorer)
- [Tramite il sito nuget.org](#analyze-nuget-packages-using-nugetorg)

Dopo l'analisi dei pacchetti, se questi non sono compatibili con .NET Core e supportano solo .NET Framework, sarà possibile verificare se la [modalità di compatibilità .NET Framework](#net-framework-compatibility-mode) risulta utile per il trasferimento.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analizzare i pacchetti NuGet usando NuGet Package Explorer

Un pacchetto NuGet è un set di cartelle contenenti assembly specifici per la piattaforma. Pertanto è necessario verificare se nel pacchetto è presente una cartella che contiene un assembly compatibile.

Il metodo più semplice per esaminare le cartelle del pacchetto NuGet è lo strumento [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Dopo aver installato lo strumento seguire questa procedura per visualizzare i nomi delle cartelle:

1. Aprire NuGet Package Explorer.
2. Fare clic su **Open package from online feed** (Apri il pacchetto dal feed online).
3. Cercare il nome del pacchetto.
4. Selezionare il nome del pacchetto nei risultati della ricerca e fare clic su **open** (Apri).
5. Espandere la cartella *lib* sul lato destro per visualizzare i nomi delle cartelle.

Cercare una cartella con uno dei nomi seguenti:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Questi valori sono i [Target Framework Moniker (TFM)](../../standard/frameworks.md) che corrispondono a versioni dei profili [.NET Standard](../../standard/net-standard.md), .NET Core e dei tradizionali profili della libreria di classi portabile (PCL) compatibili con .NET Core.

> [!IMPORTANT]
> Quando si esaminano i TFM supportati da un pacchetto, si noti che `netcoreapp*` è compatibile, ma è destinato solo ai progetti .NET Core e non ai progetti .NET Standard.
> Una libreria che supporta solo `netcoreapp*` ma non `netstandard*` può essere usata solo da altre applicazioni .NET Core.

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizzare i pacchetti NuGet usando nuget.org

In alternativa è possibile visualizzare i TFM supportati da ogni pacchetto in [nuget.org](https://www.nuget.org/) nella sezione **Dependencies** (Dipendenze) della pagina del pacchetto.

La verifica della compatibilità risulta più semplice nel sito, ma le informazioni presenti in **Dependencies** (Dipendenze) non sono disponibili per tutti i pacchetti nel sito.

### <a name="net-framework-compatibility-mode"></a>Modalità di compatibilità di .NET Framework

Il risultato dell'analisi dei pacchetti NuGet può essere che i pacchetti supportano solo .NET Framework, come la maggior parte dei pacchetti NuGet.

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

## <a name="port-your-packages-to-packagereference"></a>Convertire i pacchetti a `PackageReference`

.NET Core usa [PackageReference](/nuget/consume-packages/package-references-in-project-files) per specificare le dipendenze dei pacchetti. Se si usa [packages.config](/nuget/reference/packages-config) per specificare i pacchetti, sarà necessario eseguire la conversione a `PackageReference`.

Per altre informazioni, vedere [Eseguire la migrazione da packages.config a PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).

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
