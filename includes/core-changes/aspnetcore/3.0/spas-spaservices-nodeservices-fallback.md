---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522689"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Spa: SpaServices e NodeServices non eseguono più il fallback al logger della console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> e <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> non visualizzeranno i log della console a meno che non sia stata configurata la registrazione.

#### <a name="version-introduced"></a>Versione introdotta

3.0

#### <a name="old-behavior"></a>Comportamento precedente

`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` usati per creare automaticamente un logger della console quando la registrazione non è configurata.

#### <a name="new-behavior"></a>Nuovo comportamento

`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` non visualizzeranno i log della console a meno che non sia stata configurata la registrazione.

#### <a name="reason-for-change"></a>Motivo della modifica

È necessario allineare al modo in cui gli altri pacchetti ASP.NET Core implementano la registrazione.

#### <a name="recommended-action"></a>Azione consigliata

Se è necessario il comportamento precedente, per configurare la registrazione della console, aggiungere `services.AddLogging(builder => builder.AddConsole())` al metodo `Setup.ConfigureServices`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API interessate

Nessuno

<!--

#### Affected APIs

Not detectable via API analysis

-->
