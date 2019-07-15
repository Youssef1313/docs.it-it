---
ms.openlocfilehash: 7b86365e841defb78558b10fa171a88031b4820e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859120"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Il valore predefinito di ServicePointManager.SecurityProtocol è SecurityProtocolType.System.Default

|   |   |
|---|---|
|Dettagli|A partire dalle app destinate a .NET Framework 4.7, il valore predefinito della proprietà <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> è <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Questa modifica consente alle API di rete di .NET Framework basate su SslStream (ad esempio FTP, HTTPS e SMTP) di ereditare i protocolli di sicurezza predefiniti dal sistema operativo anziché usare i valori hardcoded definiti da .NET Framework. Il valore predefinito varia a seconda del sistema operativo e di eventuali configurazioni personalizzate eseguite dall'amministratore di sistema. Per informazioni sul protocollo SChannel predefinito in ogni versione del sistema operativo Windows, vedere [Protocolli in TLS/SSL (SSP Schannel)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Per le applicazioni destinate a una versione precedente di .NET Framework, il valore predefinito della proprietà <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> dipende dalla versione di .NET Framework di destinazione. Per altre informazioni, vedere la [sezione Servizi di rete in Modifiche di reindirizzamento per la migrazione da .NET Framework 4.5.2 a 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking).|
|Suggerimento|Questa modifica influisce sulle app destinate a .NET Framework 4.7 o versioni successive. </br>Se si preferisce usare un protocollo definito anziché affidarsi a un'impostazione predefinita del sistema, è possibile impostare in modo esplicito il valore della proprietà <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>.</br>Se questa modifica non è accettabile, è possibile rifiutarla esplicitamente aggiungendo un'impostazione di configurazione alla sezione [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) del file di configurazione dell'applicazione. L'esempio seguente mostra sia la sezione <code>&lt;runtime&gt;</code> che l'opzione per il rifiuto esplicito <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Ambito|Secondario|
|Versione|4.7|
|Tipo|Ridestinazione|
|API interessate|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

