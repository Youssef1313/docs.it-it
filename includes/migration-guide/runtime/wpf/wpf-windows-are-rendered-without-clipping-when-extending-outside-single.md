---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858424"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="9cbb0-101">Il rendering delle finestre WPF viene eseguito senza ritaglio quando le finestre si estendono oltre un singolo monitor</span><span class="sxs-lookup"><span data-stu-id="9cbb0-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9cbb0-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="9cbb0-102">Details</span></span>|<span data-ttu-id="9cbb0-103">In .NET Framework 4.6 in esecuzione su Windows 8 e versioni successive viene eseguito il rendering dell'intera finestra senza ritaglio quando la finestra si estende al di fuori di un singolo schermo in uno scenario d'uso di più monitor.</span><span class="sxs-lookup"><span data-stu-id="9cbb0-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="9cbb0-104">Questo comportamento è diverso rispetto a quello delle versioni precedenti di .NET Framework in cui le finestre WPF che si estendevano oltre un singolo schermo venivano ritagliate.</span><span class="sxs-lookup"><span data-stu-id="9cbb0-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="9cbb0-105">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="9cbb0-105">Suggestion</span></span>|<span data-ttu-id="9cbb0-106">Questo funzionamento (applicazione o non applicazione del ritaglio) può essere impostato esplicitamente tramite l'elemento <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> in <code>&lt;appSettings&gt;</code> nel file di configurazione di un'applicazione oppure impostando la proprietà <code>EnableMultiMonitorDisplayClipping</code> all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="9cbb0-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="9cbb0-107">Ambito</span><span class="sxs-lookup"><span data-stu-id="9cbb0-107">Scope</span></span>|<span data-ttu-id="9cbb0-108">Secondario</span><span class="sxs-lookup"><span data-stu-id="9cbb0-108">Minor</span></span>|
|<span data-ttu-id="9cbb0-109">Versione</span><span class="sxs-lookup"><span data-stu-id="9cbb0-109">Version</span></span>|<span data-ttu-id="9cbb0-110">4.6</span><span class="sxs-lookup"><span data-stu-id="9cbb0-110">4.6</span></span>|
|<span data-ttu-id="9cbb0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cbb0-111">Type</span></span>|<span data-ttu-id="9cbb0-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="9cbb0-112">Runtime</span></span>|

