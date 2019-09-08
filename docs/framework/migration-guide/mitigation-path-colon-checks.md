---
title: 'Mitigazione: Verifica della presenza dei due punti nel percorso'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789986"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="f7ab9-102">Mitigazione: Verifica della presenza dei due punti nel percorso</span><span class="sxs-lookup"><span data-stu-id="f7ab9-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="f7ab9-103">A partire dalle applicazioni destinate a .NET Framework 4.6.2, sono state apportate alcune modifiche per supportare i percorsi in precedenza non supportati, sia in termini di lunghezza che di formato.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="f7ab9-104">In particolare, i controlli per la sintassi del separatore dell'unità appropriata (due punti) sono stati resi più corretti.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f7ab9-105">Impatto</span><span class="sxs-lookup"><span data-stu-id="f7ab9-105">Impact</span></span>  
 <span data-ttu-id="f7ab9-106">Queste modifiche bloccano alcuni percorsi URI supportati in precedenza dai metodi <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f7ab9-107">Mitigazione</span><span class="sxs-lookup"><span data-stu-id="f7ab9-107">Mitigation</span></span>  
 <span data-ttu-id="f7ab9-108">Per risolvere il problema di un percorso in precedenza accettabile che non è più supportato dai metodi <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, è possibile eseguire queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="f7ab9-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="f7ab9-109">Rimuovere manualmente lo schema da un URL.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="f7ab9-110">Ad esempio, rimuovere `file://` da un URL.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="f7ab9-111">Passare l'URI a un costruttore <xref:System.Uri> e recuperare il valore della proprietà <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="f7ab9-112">Rifiutare esplicitamente la normalizzazione del nuovo percorso impostando il commutatore `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> su `true`.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f7ab9-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f7ab9-113">See also</span></span>

- [<span data-ttu-id="f7ab9-114">Modifiche di reindirizzamento</span><span class="sxs-lookup"><span data-stu-id="f7ab9-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
