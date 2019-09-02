---
title: Come installare lo strumento dell'interfaccia della riga di comando (CLI) di ML.NET
description: Panoramica e installazione dello strumento dell'interfaccia della riga di comando (CLI) di ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8b6de466a6cf72b44a16c80fc024671bc4e975e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106904"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Come installare lo strumento dell'interfaccia della riga di comando (CLI) di ML.NET

L'interfaccia della riga di comando di ML.NET è uno strumento che può essere eseguito in qualsiasi prompt dei comandi (Windows, Mac o Linux) per generare modelli ML.NET e codice sorgente di buona qualità in base ai training set specificati.

> [!NOTE]
> Questo argomento fa riferimento all'interfaccia della riga di comando di ML.NET e al Machine Learning automatico, attualmente in anteprima, e il materiale può essere soggetto a modifiche.

## <a name="pre-requisites"></a>Prerequisiti

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Facoltativo) [Visual Studio 2017 o 2019](https://visualstudio.microsoft.com/vs/)

È possibile eseguire i progetti in codice C# generati con F5 in Visual Studio o con `dotnet run` (interfaccia della riga di comando di .NET Core).

Nota: Se dopo l'installazione di [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) il comando `dotnet tool` non funziona, disconnettersi da Windows ed eseguire di nuovo l'accesso.

## <a name="install"></a>Installazione di

L'interfaccia della riga di comando di ML.NET viene installata come gli altri strumenti globali dotnet. Usare il comando dell'interfaccia della riga di comando di .NET Core `dotnet tool install`. 

L'esempio seguente illustra come installare l'interfaccia della riga di comando di ML.NET nel percorso del feed NuGet predefinito:

```console
dotnet tool install -g mlnet
```

Se lo strumento non può essere installato (ovvero, se non è disponibile nel feed NuGet predefinito), vengono visualizzati i messaggi di errore. Verificare che i feed previsti vengano controllati.

Se l'installazione ha esito positivo, viene visualizzato un messaggio che mostra il comando usato per chiamare lo strumento e la versione installata, simile all'esempio seguente:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

È possibile verificare che l'installazione sia avvenuta correttamente digitando il comando seguente:

```console
mlnet
```

Verranno visualizzate le informazioni della Guida per i comandi disponibili per lo strumento mlnet, ad esempio per il comando 'auto-train'.

## <a name="install-a-specific-release-version"></a>Installare una versione specifica

Se si sta tentando di installare una versione non definitiva o una versione specifica dello strumento, è possibile specificare il [framework](../../standard/frameworks.md) usando il formato seguente:

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

È anche possibile verificare se il pacchetto è installato correttamente digitando il comando seguente:

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Disinstallare il pacchetto dell'interfaccia della riga di comando

Digitare il comando seguente per disinstallare il pacchetto dal computer locale:

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aggiornare il pacchetto dell'interfaccia della riga di comando

Digitare il comando seguente per aggiornare il pacchetto del computer locale:

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Configurare i suggerimenti dell'interfaccia della riga di comando (completamento automatico con il tasto TAB)

Poiché è basata su `System.CommandLine`, l'interfaccia della riga di comando di ML.NET include un supporto predefinito per il completamento con il tasto TAB.

L'animazione seguente mostra un esempio del funzionamento del completamento automatico con il tasto TAB:

![immagine](./media/cli-tab-completion.gif)

Il completamento automatico con il tasto TAB (suggerimenti di parametri) può essere usato in *Windows PowerShell* e *bash macOS/Linux* ma non in *Windows CMD*.

Per abilitarlo nella versione di anteprima corrente è necessario che l'utente finale esegua le operazioni descritte di seguito per ogni shell. Al termine, il completamento potrà essere usato per tutte le app scritte con `System.CommandLine`, ad esempio l'interfaccia della riga di comando di ML.NET.

Nel computer in cui si vuole abilitare il completamento, è necessario eseguire due operazioni.

1. Installare lo strumento globale `dotnet-suggest` eseguendo il comando seguente:

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. Aggiungere lo script shim appropriato al profilo della shell. Potrebbe essere necessario creare un file del profilo della shell. Lo script shim inoltra le richieste di completamento della shell allo strumento `dotnet-suggest` che delega all'app basata su `System.CommandLine` appropriata.

    - Per bash, aggiungere il contenuto di [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) a `~/.bash_profile`.

    - Per PowerShell, aggiungere il contenuto di [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) al profilo PowerShell. È possibile individuare il percorso previsto per il profilo PowerShell eseguendo il comando seguente nella console:

    ```console
    echo $profile
    ``` 

(Per le altre shell, [ricercare](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) o aprire un [problema](https://github.com/dotnet/System.CommandLine/issues)).

## <a name="installation-directory"></a>Directory di installazione

L'interfaccia della riga di comando di ML.NET può essere installata nella directory predefinita o in un percorso specifico. Le directory predefinite sono:

| Sistema operativo          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| WINDOWS     | `%USERPROFILE%\.dotnet\tools` |

Questi percorsi vengono aggiunti al percorso dell'utente alla prima esecuzione dell'SDK in modo che gli strumenti globali installati possano essere chiamati direttamente.

Nota: gli strumenti globali sono specifici dell'utente e non globali del computer. Per questa ragione non è possibile installare uno strumento globale disponibile per tutti gli utenti del computer. Lo strumento è disponibile solo per i singoli profili utente in cui è stato installato.

Gli strumenti globali possono anche essere installati in una directory specifica. Quando vengono installati in una directory specifica, l'utente deve verificare che il comando sia disponibile includendo la directory nel percorso, chiamando il comando con la directory specificata chiamando lo strumento dall'interno della directory specificata.
In questo caso l'interfaccia della riga di comando di .NET Core non aggiunge automaticamente il percorso alla variabile di ambiente PATH.

## <a name="see-also"></a>Vedere anche

- [Esercitazione dell'introduzione allo strumento dell'interfaccia della riga di comando di ML.NET CLI](../tutorials/mlnet-cli.md)
- [Come eseguire automaticamente il training dei modelli con lo strumento dell'interfaccia della riga di comando di ML.NET](../automate-training-with-cli.md)
- [Guida di riferimento per i comandi di training automatico dell'interfaccia della riga di comando di ML.NET](../reference/ml-net-cli-reference.md) 
- [Telemetria nell'interfaccia della riga di comando di ML.NET](../resources/ml-net-cli-telemetry.md)
