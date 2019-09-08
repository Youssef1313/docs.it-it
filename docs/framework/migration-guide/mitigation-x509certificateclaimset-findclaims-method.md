---
title: 'Mitigazione: metodo X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc03e6c88a2aabb967587d8b1ee7d0b784b4e7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778944"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="59310-102">Mitigazione: metodo X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="59310-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="59310-103">A partire dalle app destinate a .NET Framework 4.6.1, il metodo <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tenterà di far corrispondere l'argomento `claimType` con tutte le voci DNS nel relativo campo SAN.</span><span class="sxs-lookup"><span data-stu-id="59310-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="59310-104">Impatto</span><span class="sxs-lookup"><span data-stu-id="59310-104">Impact</span></span>  
 <span data-ttu-id="59310-105">Questa modifica interessa solo le app destinate a versioni di .NET Framework a partire da .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="59310-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="59310-106">Per le app destinate a versioni precedenti di .NET Framework, il metodo <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> cerca di far corrispondere l'argomento `claimType` solo con l'ultima voce DNS.</span><span class="sxs-lookup"><span data-stu-id="59310-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="59310-107">Mitigazione</span><span class="sxs-lookup"><span data-stu-id="59310-107">Mitigation</span></span>  
 <span data-ttu-id="59310-108">Se la modifica è indesiderata, le app destinate a versioni di .NET Framework a partire da .NET Framework 4.6.1 possono rifiutarla esplicitamente aggiungendo l'impostazione di configurazione seguente alla sezione [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) del file di configurazione dell'app:</span><span class="sxs-lookup"><span data-stu-id="59310-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="59310-109">Le app destinate a versioni precedenti di .NET Framework ma in esecuzione su .NET Framework 4.6.1 o versione successiva possono optare per questo comportamento aggiungendo l'impostazione di configurazione seguente alla sezione [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) del file di configurazione dell'app:</span><span class="sxs-lookup"><span data-stu-id="59310-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59310-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="59310-110">See also</span></span>

- [<span data-ttu-id="59310-111">Modifiche di reindirizzamento</span><span class="sxs-lookup"><span data-stu-id="59310-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
