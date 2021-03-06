---
title: Panoramica degli strumenti di diagnostica -.NET Core
description: Panoramica degli strumenti e delle tecniche disponibili per la diagnosi delle applicazioni .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.topic: overview
ms.openlocfilehash: c0a45a1bfe866ad42890db576b5dd5098b1dbc3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318341"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quali strumenti di diagnostica sono disponibili in .NET Core?

Il software non sempre si comporta come previsto, ma .NET Core offre strumenti e API utili per diagnosticare questi problemi in modo rapido ed efficace.

Questo articolo consente di trovare i vari strumenti necessari.

## <a name="managed-debuggers"></a>Debugger gestiti

I [debugger gestiti](managed-debuggers.md) consentono di interagire con il programma. La sospensione, l'esecuzione incrementale, l'analisi e la ripresa forniscono informazioni approfondite sul comportamento del codice. Un debugger è la prima scelta per la diagnosi dei problemi funzionali che possono essere facilmente riprodotti.

## <a name="logging-and-tracing"></a>Registrazione e traccia

La [registrazione e la traccia](logging-tracing.md) sono tecniche correlate. Si riferiscono all'instrumentazione del codice per creare file di log. I file registrano i dettagli delle operazioni eseguite da un programma. Questi dettagli possono essere usati per diagnosticare i problemi più complessi. In combinazione con i timestamp, queste tecniche sono utili anche per le analisi delle prestazioni.

## <a name="unit-testing"></a>Unit test

[Unit test](../testing/index.md) è un componente chiave dell'integrazione continua e della distribuzione di software di alta qualità. Gli unit test sono progettati per offrire avvisi in anticipo in caso di problemi funzionali.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Strumenti globali di diagnostica DotNet di .NET Core

### <a name="dotnet-counters"></a>contatori DotNet

[DotNet-Counters](dotnet-counters.md) è uno strumento di monitoraggio delle prestazioni per il monitoraggio dell'integrità di primo livello e l'analisi delle prestazioni. Osserva i valori dei contatori delle prestazioni pubblicati tramite l'API <xref:System.Diagnostics.Tracing.EventCounter>. Ad esempio, è possibile monitorare rapidamente elementi come l'utilizzo della CPU o la frequenza delle eccezioni generate nell'applicazione .NET Core.

### <a name="dotnet-dump"></a>DotNet-dump

Lo strumento [DotNet-dump](dotnet-dump.md) consente di raccogliere e analizzare i dump di base di Windows e Linux senza un debugger nativo.

### <a name="dotnet-trace"></a>traccia DotNet

.NET Core include il cosiddetto `EventPipe` tramite cui vengono esposti i dati di diagnostica. Lo strumento [DotNet-Trace](dotnet-trace.md) consente di usare i dati di profilatura interessanti dall'app che possono risultare utili negli scenari in cui è necessario causare la lentezza delle app.
