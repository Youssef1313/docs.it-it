---
ms.openlocfilehash: ae3766e2045b5834fbf6ea20415942413b1590c0
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858628"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Servizi WCF che usano NETTCP con sicurezza SSL e autenticazione dei certificati MD5

|   |   |
|---|---|
|Dettagli|.NET Framework 4.6 aggiunge TLS 1.1 e TLS 1.2 all'elenco dei protocolli predefiniti SSL WCF. Quando .NET Framework 4.6 o versione successiva è installato sia nei computer client che nei server, per la negoziazione viene usato TLS 1.2, che non supporta l'autenticazione dei certificati MD5. Di conseguenza, se un cliente usa un certificato MD5, il client WCF non riuscirà a connettersi al servizio WCF.|
|Suggerimento|È possibile risolvere questo problema in modo che un client WCF possa connettersi a un server WCF effettuando una delle operazioni seguenti:<ul><li>Aggiornare il certificato in modo che non usi l'algoritmo MD5. Si tratta della soluzione consigliata.</li><li>Se l'associazione non è configurata in modo dinamico nel codice sorgente, aggiornare il file di configurazione dell'applicazione in modo che usi TLS 1.1 o una versione precedente del protocollo. In questo modo è possibile continuare a usare un certificato con l'algoritmo hash MD5.</li></ul> <blockquote> [!WARNING] Questa soluzione non è consigliata, poiché un certificato con l'algoritmo hash MD5 viene considerato non protetto.</blockquote> Il file di configurazione seguente permette di effettuare queste operazioni:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Se l'associazione è configurata in modo dinamico nel codice sorgente, aggiornare la proprietà <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> in modo che usi TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> o una versione precedente del protocollo nel codice sorgente.</li></ul> <blockquote> [!WARNING] Questa soluzione non è consigliata, poiché un certificato con l'algoritmo hash MD5 viene considerato non protetto.</blockquote> |
|Ambito|Secondario|
|Versione|4.6|
|Tipo|Runtime|

