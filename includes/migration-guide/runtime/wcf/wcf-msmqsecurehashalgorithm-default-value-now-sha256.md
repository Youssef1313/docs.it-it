---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857224"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="ca19e-101">Il valore predefinito MsmqSecureHashAlgorithm di WCF è ora SHA256</span><span class="sxs-lookup"><span data-stu-id="ca19e-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ca19e-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="ca19e-102">Details</span></span>|<span data-ttu-id="ca19e-103">A partire da .NET Framework 4.7.1 l'algoritmo di firma del messaggio predefinito in WCF per i messaggi Msmq è SHA256.</span><span class="sxs-lookup"><span data-stu-id="ca19e-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="ca19e-104">In .NET Framework 4.7 e versioni precedenti l'algoritmo di firma del messaggio predefinito è SHA1.</span><span class="sxs-lookup"><span data-stu-id="ca19e-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="ca19e-105">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="ca19e-105">Suggestion</span></span>|<span data-ttu-id="ca19e-106">Se si riscontrano problemi di compatibilità con questa modifica in .NET Framework 4.7.1 o versione successiva, è possibile rifiutarla esplicitamente aggiungendo la riga seguente alla sezione <code>&lt;runtime&gt;</code> del file app.config:</span><span class="sxs-lookup"><span data-stu-id="ca19e-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="ca19e-107">Ambito</span><span class="sxs-lookup"><span data-stu-id="ca19e-107">Scope</span></span>|<span data-ttu-id="ca19e-108">Secondario</span><span class="sxs-lookup"><span data-stu-id="ca19e-108">Minor</span></span>|
|<span data-ttu-id="ca19e-109">Versione</span><span class="sxs-lookup"><span data-stu-id="ca19e-109">Version</span></span>|<span data-ttu-id="ca19e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ca19e-110">4.7.1</span></span>|
|<span data-ttu-id="ca19e-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="ca19e-111">Type</span></span>|<span data-ttu-id="ca19e-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="ca19e-112">Runtime</span></span>|

