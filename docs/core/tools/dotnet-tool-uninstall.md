---
title: Comando dotnet tool uninstall
description: Il comando dotnet tool uninstall disinstalla lo strumento globale .NET Core specificato nel computer.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117550"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>nome

`dotnet tool uninstall` - Disinstalla lo [strumento globale .NET Core](global-tools.md) specificato dal computer.

## <a name="synopsis"></a>Riepilogo

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Descrizione

Il comando `dotnet tool uninstall` consente di disinstallare gli strumenti globali .NET Core dal computer. Per usare il comando, è necessario specificare che si vuole rimuovere uno strumento a livello utente con l'opzione `--global` oppure specificare un percorso in cui è installato lo strumento con l'opzione `--tool-path`.

## <a name="arguments"></a>Argomenti

`PACKAGE_NAME`

Nome/ID del pacchetto NuGet che contiene lo strumento globale .NET Core da disinstallare. È possibile trovare il nome del pacchetto usando il comando [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Opzioni

`-g|--global`

Specifica che lo strumento da rimuovere appartiene a un'installazione a livello utente. Non può essere usata con l'opzione `--tool-path`. Se non si specifica questa opzione, è necessario specificare l'opzione `--tool-path`.

`-h|--help`

Stampa una breve guida per il comando.

`--tool-path <PATH>`

Specifica il percorso da cui disinstallare lo strumento globale. Il valore di PATH può essere assoluto o relativo. Non può essere usata con l'opzione `--global`. Se non si specifica questa opzione, è necessario specificare l'opzione `--global`.

## <a name="examples"></a>Esempi

Disinstalla lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/):

`dotnet tool uninstall -g dotnetsay`

Disinstalla lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/) da una cartella di Windows specifica:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Disinstalla lo strumento globale [dotnetsay](https://www.nuget.org/packages/dotnetsay/) da una cartella di Linux/macOS specifica:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Vedere anche

- [Strumenti globali .NET Core](global-tools.md)
