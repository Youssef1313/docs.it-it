---
title: Strumenti dell'interfaccia della riga di comando aggiuntivi per .NET core
description: Panoramica degli strumenti aggiuntivi che è possibile installare e che supportano ed estendono la funzionalità di .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: c885d6f6b0417a80dd6e26afe9572766738c5b4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771961"
---
# <a name="net-core-additional-tools-overview"></a>Panoramica degli strumenti aggiuntivi per .NET Core

Questa sezione consente di compilare un elenco di strumenti che supportano ed estendono la funzionalità di .NET Core, oltre agli strumenti [di interfaccia della riga di comando di .NET Core (CLI)](../tools/index.md).

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Strumento WCF Web Service Reference](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference è un provider di servizi connessi di Visual Studio disponibile per la prima volta con [Visual Studio 2017 versione 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Questo strumento consente di recuperare metadati da un servizio Web nella soluzione corrente, in un percorso di rete o da un file WSDL, e genera un file di origine compatibile con .NET Core che definisce una classe proxy WCF con metodi utilizzabili per accedere alle operazioni del servizio Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Strumento WCF dotnet-svcutil](dotnet-svcutil-guide.md)

Lo strumento WCF (Windows Communication Foundation) dotnet-svcutil consente di recuperare metadati da un servizio Web, in un percorso di rete o da un file WSDL e genera un file di origine compatibile con .NET Core che definisce una classe proxy WCF con metodi utilizzabili per accedere alle operazioni del servizio Web.
Lo strumento **DotNet-Svcutil** è un'opzione alternativa al [**servizio Web WCF riferimento**](wcf-web-service-reference-guide.md) al provider di servizi connessi di Visual Studio, che è stato prima fornito con visual studio 2017 versione 15,5. Come strumento dell'interfaccia della riga di comando di .NET Core, **dotnet-svcutil** è disponibile come strumento multipiattaforma in Linux, macOS e Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Strumento dotnet-svcutil.xmlserializer WCF](dotnet-svcutil.xmlserializer-guide.md)

In .NET Framework è possibile pregenerare un assembly di serializzazione usando lo strumento svcutil. Il pacchetto NuGet dotnet-svcutil.xmlserializer fornisce funzionalità simili in .NET Core. Pregenera il codice di serializzazione C# per i tipi dell'applicazione client che vengono usati dal contratto di servizio WCF e possono essere serializzati da <xref:System.Xml.Serialization.XmlSerializer>. Ciò migliora le prestazioni di avvio della serializzazione XML durante la serializzazione o la deserializzazione di oggetti di tali tipi.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generazione serializzatore XML](xml-serializer-generator.md)

Come il [Generatore di serializzatori Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) per .NET Framework, il [pacchetto Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) è la soluzione per le librerie .NET Core e .NET Standard. Crea un assembly di serializzazione XML per tipi contenuti in un assembly per migliorare le prestazioni di avvio della serializzazione XML durante la serializzazione o deserializzazione di oggetti di questi tipi usando <xref:System.Xml.Serialization.XmlSerializer>.
