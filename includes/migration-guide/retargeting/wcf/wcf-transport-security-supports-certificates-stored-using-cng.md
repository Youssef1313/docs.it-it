---
ms.openlocfilehash: 8c1ca89af289dbcc6c68d5ace3e8a9f32672ec0d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859345"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>La sicurezza del trasporto WCF supporta i certificati archiviati usando CNG

|   |   |
|---|---|
|Dettagli|A partire dalle applicazioni che hanno come destinazione .NET Framework 4.6.2, la sicurezza del trasporto WCF supporta i certificati archiviati usando la libreria di crittografia di Windows (CNG). Questo supporto è limitato ai certificati con una chiave pubblica che ha un esponente di lunghezza non superiore a 32 bit. Quando un'applicazione è destinata a .NET Framework 4.6.2, questa funzionalità è attivata per impostazione predefinita. Nelle versioni precedenti di .NET Framework il tentativo di usare i certificati X509 con un provider di archiviazione chiavi CSG genera un'eccezione.|
|Suggerimento|Le applicazioni destinate a .NET Framework 4.6.1 e versioni precedenti ma eseguite in .NET Framework 4.6.2 abilitano il supporto per i certificati CNG aggiungendo la riga seguente alla sezione <code>&lt;runtime&gt;</code> del file app.config o web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>L'operazione può essere eseguita anche con il codice seguente:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Si noti che, grazie a questa modifica, i codici di gestione delle eccezioni che dipendono dal tentativo di avviare una comunicazione protetta con un certificato CNG di esito negativo non verranno più eseguiti.|
|Ambito|Secondario|
|Versione|4.6.2|
|Tipo|Ridestinazione|

