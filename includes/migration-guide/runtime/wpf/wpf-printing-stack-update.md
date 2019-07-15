---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802505"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="f42c6-101">Aggiornamento dello stack di stampa WPF</span><span class="sxs-lookup"><span data-stu-id="f42c6-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f42c6-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="f42c6-102">Details</span></span>|<span data-ttu-id="f42c6-103">Le API di stampa di WPF che usano <xref:System.Printing.PrintQueue?displayProperty=name> ora chiamano l'API di gestione del pacchetto dei documenti di stampa di Windows invece dell'API di stampa XPS, ora deprecata.</span><span class="sxs-lookup"><span data-stu-id="f42c6-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="f42c6-104">La modifica è stata apportata per ottimizzare la funzionalità. Né gli utenti né gli sviluppatori dovrebbero riscontrare modifiche nel comportamento o nell'uso dell'API.</span><span class="sxs-lookup"><span data-stu-id="f42c6-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="f42c6-105">Il nuovo stack di stampa viene abilitato per impostazione predefinita durante l'esecuzione in Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="f42c6-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="f42c6-106">Il vecchio stack di stampa continua a funzionare come in precedenza nelle versioni precedenti di Windows.</span><span class="sxs-lookup"><span data-stu-id="f42c6-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="f42c6-107">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="f42c6-107">Suggestion</span></span>|<span data-ttu-id="f42c6-108">Per usare lo stack precedente in Windows 10 Creators Update, impostare il valore <code>UseXpsOMPrinting</code> REG_DWORD della chiave del Registro di sistema <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> su <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="f42c6-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="f42c6-109">Ambito</span><span class="sxs-lookup"><span data-stu-id="f42c6-109">Scope</span></span>|<span data-ttu-id="f42c6-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f42c6-110">Edge</span></span>|
|<span data-ttu-id="f42c6-111">Versione</span><span class="sxs-lookup"><span data-stu-id="f42c6-111">Version</span></span>|<span data-ttu-id="f42c6-112">4.7</span><span class="sxs-lookup"><span data-stu-id="f42c6-112">4.7</span></span>|
|<span data-ttu-id="f42c6-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="f42c6-113">Type</span></span>|<span data-ttu-id="f42c6-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="f42c6-114">Runtime</span></span>|

