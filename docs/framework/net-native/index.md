---
title: Compilazione di app con .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660900"
---
# <a name="compiling-apps-with-net-native"></a>Compilazione di app con .NET Native

.NET native è una tecnologia di precompilazione per la compilazione e distribuzione di App di Windows che è inclusa in Visual Studio 2015 e versioni successive. che compila automaticamente la versione finale delle app scritte in codice gestito (C# o Visual Basic) e destina .NET Framework e Windows 10 al codice nativo.

In genere, le applicazioni che usano .NET Framework vengono compilate in Microsoft Intermediate Language (IL). In fase di esecuzione, il compilatore just-in-time (JIT) traduce IL in codice nativo. Al contrario, .NET Native compila le app Windows direttamente in codice nativo. Per gli sviluppatori, questo significa che:

- Le app offrono le prestazioni del codice nativo. In genere, le prestazioni risulteranno superiori al codice che viene innanzitutto compilato a livello di integrità e quindi compilato in codice nativo tramite il compilatore JIT.

- È possibile continuare a programmare in c# o Visual Basic.

- È possibile continuare a sfruttare le risorse fornite da .NET Framework, tra cui la libreria di classi, gestione della memoria e Garbage Collection automatiche e la gestione delle eccezioni.

Per gli utenti delle app .NET nativa offre i seguenti vantaggi:

- Tempi di esecuzione per la maggior parte delle App e gli scenari.

- Tempi di avvio più rapidi per la maggior parte delle App e gli scenari.

- Basso costo di distribuzione e l'aggiornamento.

- Utilizzo memoria applicazione ottimizzata.

> [!IMPORTANT]
> Per la maggior parte delle App e gli scenari, .NET Native offre tempi di avvio significativamente più veloce e prestazioni superiori rispetto a un'app compilata in linguaggio intermedio o di un'immagine NGEN. Tuttavia, i risultati possono variare. Per assicurarsi che l'app ha tratto vantaggio dai miglioramenti delle prestazioni di .NET Native, è necessario confrontare le prestazioni con quello della versione non - .NET Native dell'app. Per altre informazioni, vedere [panoramica delle sessioni di prestazioni](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Ma prevede più di una compilazione in codice nativo .NET Native. trasforma il modo in cui le applicazioni di .NET Framework vengono compilate ed eseguite. In particolare:

- Durante la precompilazione, le parti necessarie di .NET Framework vengono collegate staticamente nell'applicazione. Ciò consente di eseguire l'applicazione con le librerie app-local di .NET Framework e di effettuare l'analisi globale per offrire prestazioni ottimali del compilatore. Di conseguenza, l'avvio delle applicazioni sarà più rapido e coerente dopo l'aggiornamento di .NET Framework.

- Il runtime di .NET Native è ottimizzato per la precompilazione statica e nella maggior parte dei casi offre prestazioni superiori. Allo stesso tempo, mantiene le funzionalità di reflection di base che gli sviluppatori troveranno estremamente produttive.

- .NET native Usa il back-end stesso come il C++ compilatore, che è ottimizzato per scenari di precompilazione statici.

.NET native è in grado di offrire i vantaggi delle prestazioni di C++ gestire gli sviluppatori di codice perché Usa gli strumenti identici o simili come C++ dietro le quinte, come illustrato in questa tabella.

||.NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|Librerie|.NET Framework + Windows Runtime|Win32 + Windows Runtime|
|Compilatore|Compilatore di ottimizzazione UTC|Compilatore di ottimizzazione UTC|
|Distribuito|File binari Ready to run|File binari Ready to run (ASM)|
|Runtime|MRT.dll (Runtime CLR minimo)|CRT.dll (C Runtime)|

Per le app Windows per Windows 10, caricare i file binari per la compilazione con .NET Native in pacchetti di applicazioni (file APPX) in Windows Store.

## <a name="in-this-section"></a>In questa sezione

Per altre informazioni sullo sviluppo di applicazioni con la compilazione con .NET Native, vedere i seguenti argomenti:

- [Introduzione a compilazione codice .NET Native: La procedura dettagliata dell'esperienza per sviluppatori](../../../docs/framework/net-native/getting-started-with-net-native.md)

- [Compilazione e .NET native:](../../../docs/framework/net-native/net-native-and-compilation.md) Modo in cui .NET Native compila il progetto in codice nativo.

- [Reflection e .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [API basate sulla reflection](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [Riferimento all'API Reflection](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [Informazioni di riferimento sul file di configurazione delle direttive di runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [Serialization and Metadata](../../../docs/framework/net-native/serialization-and-metadata.md) (Serializzazione e metadati)

- [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) (Migrazione dell'app di Windows Store a .NET Native)

- [Risoluzione dei problemi generale per .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
