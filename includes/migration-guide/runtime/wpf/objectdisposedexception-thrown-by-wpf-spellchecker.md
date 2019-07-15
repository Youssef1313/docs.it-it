---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802487"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="6f0c1-101">ObjectDisposedException generata dal controllo ortografico WPF</span><span class="sxs-lookup"><span data-stu-id="6f0c1-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6f0c1-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="6f0c1-102">Details</span></span>|<span data-ttu-id="6f0c1-103">Può verificarsi l'arresto anomalo di applicazioni WPF con un <xref:System.ObjectDisposedException?displayProperty=name> generato dal controllo ortografico.</span><span class="sxs-lookup"><span data-stu-id="6f0c1-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="6f0c1-104">Questo problema è risolto in .NET Framework 4.7 WPF, dove l'eccezione viene gestita in modo normale e pertanto si evitano effetti avversi sulle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="6f0c1-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="6f0c1-105">Si noti che potranno essere rilevate eccezioni first-chance occasionali nelle applicazioni in esecuzione in un debugger.</span><span class="sxs-lookup"><span data-stu-id="6f0c1-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="6f0c1-106">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="6f0c1-106">Suggestion</span></span>|<span data-ttu-id="6f0c1-107">Effettuare l'aggiornamento a .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="6f0c1-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="6f0c1-108">Ambito</span><span class="sxs-lookup"><span data-stu-id="6f0c1-108">Scope</span></span>|<span data-ttu-id="6f0c1-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6f0c1-109">Edge</span></span>|
|<span data-ttu-id="6f0c1-110">Versione</span><span class="sxs-lookup"><span data-stu-id="6f0c1-110">Version</span></span>|<span data-ttu-id="6f0c1-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6f0c1-111">4.6.1</span></span>|
|<span data-ttu-id="6f0c1-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="6f0c1-112">Type</span></span>|<span data-ttu-id="6f0c1-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="6f0c1-113">Runtime</span></span>|

