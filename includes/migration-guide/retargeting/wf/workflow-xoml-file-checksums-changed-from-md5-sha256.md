---
ms.openlocfilehash: c44971dfd65ee31657279daec2d34b8cfa8d4860
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410382"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="70cb8-101">Checksum del file XOML del flusso di lavoro modificati da MD5 a SHA256</span><span class="sxs-lookup"><span data-stu-id="70cb8-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="70cb8-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="70cb8-102">Details</span></span>|<span data-ttu-id="70cb8-103">Per supportare il debug dei flussi di lavoro basati su XOML con Visual Studio, quando vengono compilati progetti di flusso di lavoro contenenti file XOML, viene inserito nel codice generato un checksum del contenuto del file XOML come valore <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70cb8-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="70cb8-104">In .NET Framework 4.7.2 e versioni precedenti l'hash del checksum usava l'algoritmo MD5 che causava problemi nei sistemi abilitati per FIPS.</span><span class="sxs-lookup"><span data-stu-id="70cb8-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="70cb8-105">A partire da .NET Framework 4.8, viene usato l'algoritmo SHA256.</span><span class="sxs-lookup"><span data-stu-id="70cb8-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="70cb8-106">Per ragioni di compatibilità con WorkflowMarkupSourceAttribute.MD5Digest, vengono usati solo i primi 16 byte del checksum generato. Ciò potrebbe causare problemi durante il debug.</span><span class="sxs-lookup"><span data-stu-id="70cb8-106">To be compatible with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="70cb8-107">Potrebbe essere necessario ricompilare il progetto.</span><span class="sxs-lookup"><span data-stu-id="70cb8-107">You may need to re-build your project.</span></span>|
|<span data-ttu-id="70cb8-108">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="70cb8-108">Suggestion</span></span>|<span data-ttu-id="70cb8-109">Se la ricompilazione del progetto non risolve il problema, provare a impostare l'opzione <code>AppContext</code> &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; su true. Nel codice:</span><span class="sxs-lookup"><span data-stu-id="70cb8-109">If re-building your project does not solve the problem, try setting the <code>AppContext</code> switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span><pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre><span data-ttu-id="70cb8-110">Oppure in un file di configurazione (che deve trovarsi in MSBuild.exe.config per il file MSBuild.exe in uso):</span><span class="sxs-lookup"><span data-stu-id="70cb8-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="70cb8-111">Ambito</span><span class="sxs-lookup"><span data-stu-id="70cb8-111">Scope</span></span>|<span data-ttu-id="70cb8-112">Secondario</span><span class="sxs-lookup"><span data-stu-id="70cb8-112">Minor</span></span>|
|<span data-ttu-id="70cb8-113">Versione</span><span class="sxs-lookup"><span data-stu-id="70cb8-113">Version</span></span>|<span data-ttu-id="70cb8-114">4.8</span><span class="sxs-lookup"><span data-stu-id="70cb8-114">4.8</span></span>|
|<span data-ttu-id="70cb8-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="70cb8-115">Type</span></span>|<span data-ttu-id="70cb8-116">Ridestinazione</span><span class="sxs-lookup"><span data-stu-id="70cb8-116">Retargeting</span></span>|