---
title: Schema dei file di configurazione per .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921036"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schema dei file di configurazione per .NET Framework

I file di configurazione sono file XML standard che è possibile usare per modificare le impostazioni e impostare criteri per le app. Lo schema di configurazione di .NET Framework è costituito da elementi che è possibile usare nei file di configurazione per controllare il comportamento delle app. Il sommario di questa sezione rispecchia la gerarchia dello schema per l'avvio, il runtime, la rete e altri tipi di impostazioni di configurazione.

Per informazioni sui tipi, il formato e il percorso dei file di configurazione, vedere l'articolo [Configurazione di app](../index.md). Per modificare direttamente i file di configurazione, acquisire familiarità con XML.

> [!IMPORTANT]
> Gli attributi e i tag XML nei file di configurazione fanno distinzione tra maiuscole e minuscole.

## <a name="in-this-section"></a>Contenuto della sezione

[**Elemento \<configuration>** ](configuration-element.md) Viene descritto l'elemento `<configuration>`, ossia l'elemento di primo livello di tutti i file di configurazione.

[**Elemento \<assemblyBinding>** ](assemblybinding-element-for-configuration.md) Specifica i criteri di associazione degli assembly al livello di configurazione.

[**Elemento \<linkedConfiguration>** ](linkedconfiguration-element.md) Specifica un file di configurazione da includere.

[Schema delle impostazioni di avvio](./startup/index.md) Vengono descritti gli elementi che specificano la versione di Common Language Runtime da usare.

[Schema delle impostazioni di runtime](./runtime/index.md) Vengono descritti gli elementi che configurano l'associazione degli assembly e il comportamento dell'ambiente di esecuzione.

[Schema delle impostazioni di rete](./network/index.md) Vengono descritti gli elementi che specificano la modalità di connessione di .NET Framework a Internet.

[Schema delle impostazioni di crittografia](./cryptography/index.md) Vengono descritti gli elementi che eseguono il mapping dei nomi descrittivi degli algoritmi alle classi che implementano gli algoritmi di crittografia.

[Schema delle sezioni di configurazione](configuration-sections-schema.md) Vengono descritti gli elementi che consentono di creare e usare le sezioni di configurazione per le impostazioni personalizzate.

[Schema delle impostazioni di traccia e debug](./trace-debug/index.md) Vengono descritti gli elementi che specificano i listener e le opzioni di traccia.

[Schema di impostazioni del compilatore e del provider di linguaggi](./compiler/index.md) Vengono descritti gli elementi che specificano la configurazione del compilatore per i provider di linguaggi disponibili.

[Schema Application Settings](application-settings-schema.md) Vengono descritti gli elementi che consentono a un'applicazione Windows Form o ASP.NET di archiviare e recuperare le impostazioni con ambito applicazione o utente.

[Schema impostazioni applicazione](./appsettings/index.md) Contiene le impostazioni dell'applicazione personalizzate, ad esempio i percorsi di file, gli URL del servizio Web XML o qualsiasi altra informazione di configurazione personalizzata per un'applicazione.

[Schema delle impostazioni Web](./web/index.md) Tutti gli elementi nello schema delle impostazioni Web, che include gli elementi per la configurazione del funzionamento di ASP.NET con un'applicazione host, come IIS. Usato nei file *Aspnet.config*.

[Schema di configurazione di Windows Form](winforms/index.md) Tutti gli elementi nella sezione di configurazione dell'applicazione Windows Form, che include le personalizzazioni, ad esempio il supporto di valori DPI alti e di più monitor.

[Schema di configurazione di WCF](./wcf/index.md) Tutti gli elementi che consentono di configurare il servizio e le applicazioni client WCF.

[Sintassi delle direttive WCF](./wcf-directive/index.md) Viene descritta la direttiva `@ServiceHost` che definisce gli attributi specifici della pagina usati dal compilatore con estensione svc.

[Schema di configurazione di WIF](windows-identity-foundation/index.md) Tutti gli elementi dello schema di configurazione WIF (Windows Identity Foundation).

## <a name="related-sections"></a>Sezioni correlate

[Schema delle impostazioni remote](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Vengono descritti gli elementi che configurano le applicazioni client e server che implementano i servizi remoti.

[Schema delle impostazioni ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Vengono descritti gli elementi che controllano il comportamento delle applicazioni Web ASP.NET.

[Schema delle impostazioni dei servizi Web ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Vengono descritti gli elementi che controllano il comportamento dei servizi Web ASP.NET e dei relativi client.

[Configurazione di app .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Viene descritto come configurare la sicurezza, l'associazione degli assembly e i servizi remoti in .NET Framework.
