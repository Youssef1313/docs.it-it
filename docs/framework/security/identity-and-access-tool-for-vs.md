---
title: Identity and Access Tool per Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: d58cca13dc3ac67742e5371aed628a6a680e61e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045420"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="5b2c1-102">Identity and Access Tool per Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="5b2c1-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="5b2c1-103">In questo argomento viene descritto il nuovo strumento Identity and Access Tool for Visual Studio 11</span><span class="sxs-lookup"><span data-stu-id="5b2c1-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="5b2c1-104">È possibile scaricare questo strumento dall'URL seguente: <https://go.microsoft.com/fwlink/?LinkID=245849> o direttamente da Visual Studio 11 cercando "Identity" direttamente in Gestione estensioni.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-104">You can download this tool from the following URL: <https://go.microsoft.com/fwlink/?LinkID=245849> or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="5b2c1-105">Identity and Access Tool for Visual Studio 11 offre un'esperienza notevolmente semplificata in fase di sviluppo con le caratteristiche principali seguenti:</span><span class="sxs-lookup"><span data-stu-id="5b2c1-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
- <span data-ttu-id="5b2c1-106">Con il nuovo strumento è possibile eseguire lo sviluppo utilizzando tipi di progetto di applicazioni Web e IIS Express di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
- <span data-ttu-id="5b2c1-107">A differenza dell'autenticazione di sola protezione generale, con il nuovo strumento è possibile specificare la pagina o il controller di individuazione dell'area di autenticazione principale locale (o qualsiasi altro endpoint tramite cui viene gestita l'esperienza di autenticazione nell'applicazione) e tramite WIF tutte le richieste non autenticate verranno indirizzate a questo controller o pagina, anziché al servizio token di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
- <span data-ttu-id="5b2c1-108">Nello strumento è incluso un servizio token di sicurezza del test che viene eseguito nel computer locale quando si avvia una sessione di debug.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="5b2c1-109">Pertanto, non sarà più necessario creare progetti STS personalizzati, né modificarli per ottenere le attestazioni necessarie per eseguire il test delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="5b2c1-110">I tipi e i valori delle attestazioni sono completamente personalizzabili.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-110">The claim types and values are fully customizable.</span></span>  
  
- <span data-ttu-id="5b2c1-111">È possibile modificare le impostazioni comuni direttamente mediante l'interfaccia utente dello strumento, senza dover modificare il file web.config.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
- <span data-ttu-id="5b2c1-112">È possibile stabilire la federazione con Active Directory Federation Services (AD FS) 2.0, o altri provider di WS-Federation, in una singola schermata.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
- <span data-ttu-id="5b2c1-113">Lo strumento sfrutta le funzionalità del servizio di controllo di accesso (ACS) di Windows Azure con un semplice elenco di caselle di controllo per tutti i provider di identità che si desidera utilizzare: Facebook, Google, Live ID, Yahoo!, qualsiasi provider OpenID e qualsiasi provider WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="5b2c1-114">Selezionare i provider di identità, scegliere OK, quindi F5. In questo modo sia l'applicazione sia ACS verranno configurati automaticamente e l'applicazione di test sarà in grado di riconoscere ACS.</span><span class="sxs-lookup"><span data-stu-id="5b2c1-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2c1-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5b2c1-115">See also</span></span>

- [<span data-ttu-id="5b2c1-116">Funzionalità di WIF</span><span class="sxs-lookup"><span data-stu-id="5b2c1-116">WIF Features</span></span>](wif-features.md)
