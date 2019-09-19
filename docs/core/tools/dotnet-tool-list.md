---
title: Comando dotnet tool list
description: Il comando dotnet tool list visualizza lo strumento globale .NET Core specificato del computer.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117560"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>nome

`dotnet tool list` - Elenca tutti gli [strumenti globali .NET Core](global-tools.md) attualmente installati nella directory predefinita nel computer o nel percorso specificato.

## <a name="synopsis"></a>Riepilogo

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Descrizione

Il comando `dotnet tool list` consente di visualizzare tutti gli strumenti globali .NET Core installati a livello utente nel computer (profilo utente corrente) o nel percorso specificato. Il comando visualizza il nome del pacchetto, la versione installata e il comando dello strumento globale. Per usare il comando, è necessario specificare che si vuole visualizzare tutti gli strumenti a livello utente con l'opzione `--global` oppure specificare un percorso personalizzato con l'opzione `--tool-path`.

## <a name="options"></a>Opzioni

`-g|--global`

Visualizza gli strumenti globali a livello utente. Non può essere usata con l'opzione `--tool-path`. Se non si specifica questa opzione, è necessario specificare l'opzione `--tool-path`.

`-h|--help`

Stampa una breve guida per il comando.

`--tool-path <PATH>`

Specifica un percorso personalizzato in cui trovare gli strumenti globali. Il valore di PATH può essere assoluto o relativo. Non può essere usata con l'opzione `--global`. Se non si specifica questa opzione, è necessario specificare l'opzione `--global`.

## <a name="examples"></a>Esempi

Elenca tutti gli strumenti globali installati a livello utente nel computer (profilo utente corrente):

`dotnet tool list -g`

Elenca gli strumenti globali di una cartella di Windows specifica:

`dotnet tool list --tool-path c:\global-tools`

Elenca gli strumenti globali di una cartella di Linux/macOS specifica:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Vedere anche

- [Strumenti globali .NET Core](global-tools.md)
