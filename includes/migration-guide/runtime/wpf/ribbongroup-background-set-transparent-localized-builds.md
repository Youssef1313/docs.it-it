---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802553"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="aced7-101">Viene impostato lo sfondo trasparente per RibbonGroup nelle build localizzate</span><span class="sxs-lookup"><span data-stu-id="aced7-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="aced7-102">Dettagli</span><span class="sxs-lookup"><span data-stu-id="aced7-102">Details</span></span>|<span data-ttu-id="aced7-103">Lo sfondo di <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> nelle build localizzate viene sempre disegnato con il pennello trasparente, causando un'esperienza insoddisfacente per l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="aced7-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="aced7-104">Questo problema è stato risolto nella correzione di WPF per .NET Framework 4.7 con l'aggiornamento delle risorse localizzate per <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, che a sua volta garantisce che sia selezionato il pennello corretto.</span><span class="sxs-lookup"><span data-stu-id="aced7-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="aced7-105">Suggerimento</span><span class="sxs-lookup"><span data-stu-id="aced7-105">Suggestion</span></span>|<span data-ttu-id="aced7-106">Effettuare l'aggiornamento a .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="aced7-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="aced7-107">Ambito</span><span class="sxs-lookup"><span data-stu-id="aced7-107">Scope</span></span>|<span data-ttu-id="aced7-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="aced7-108">Edge</span></span>|
|<span data-ttu-id="aced7-109">Versione</span><span class="sxs-lookup"><span data-stu-id="aced7-109">Version</span></span>|<span data-ttu-id="aced7-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="aced7-110">4.6.2</span></span>|
|<span data-ttu-id="aced7-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="aced7-111">Type</span></span>|<span data-ttu-id="aced7-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="aced7-112">Runtime</span></span>|

