---
ms.openlocfilehash: f007a2b81820a1d25a2d101b35f3a49e7794fec1
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859066"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Checksum del flusso di lavoro modificati da MD5 a SHA1

|   |   |
|---|---|
|Dettagli|Per supportare il debug con Visual Studio, il runtime del flusso di lavoro genera un checksum per un'istanza del flusso di lavoro usando un algoritmo hash. In .NET Framework 4.6.2 e versioni precedenti, l'hash del checksum del flusso di lavoro usava l'algoritmo MD5, che causava problemi nei sistemi abilitati per FIPS. A partire da .NET Framework 4.7 l'algoritmo è SHA1. Se il codice ha mantenuto i checksum, questi non saranno compatibili.|
|Suggerimento|Se il codice non riesce a caricare le istanze del flusso di lavoro a causa di un errore di checksum, provare a impostare lo switch <code>AppContext</code> &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; su true. Nel codice:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>O nella configurazione:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Ambito|Secondario|
|Versione|4.7|
|Tipo|Ridestinazione|

