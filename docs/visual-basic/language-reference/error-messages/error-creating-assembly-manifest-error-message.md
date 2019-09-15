---
title: "Errore durante la creazione del manifesto dell'assembly: <error message>"
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972283"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="9bab7-102">Errore durante la creazione del \<manifesto dell'assembly: messaggio di errore ></span><span class="sxs-lookup"><span data-stu-id="9bab7-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="9bab7-103">Il compilatore Visual Basic chiama assembly linker (al. exe, noto anche come ALink) per generare un assembly con un manifesto.</span><span class="sxs-lookup"><span data-stu-id="9bab7-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="9bab7-104">Il linker ha segnalato un errore nella fase di pre-emissione della creazione dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="9bab7-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="9bab7-105">Questo può accadere se si verificano errori con il file di chiave o il contenitore di chiavi specificato.</span><span class="sxs-lookup"><span data-stu-id="9bab7-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="9bab7-106">Per la firma completa di un assembly, è necessario fornire un file di chiave valido contenente informazioni sulle chiavi pubblica e privata.</span><span class="sxs-lookup"><span data-stu-id="9bab7-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="9bab7-107">Per ritardare la firma di un assembly, è necessario selezionare la casella di controllo **Solo firma ritardata** e fornire un file di chiave valido contenente informazioni sulla chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="9bab7-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="9bab7-108">Quando la firma di un assembly viene ritardata, la chiave privata non è necessaria.</span><span class="sxs-lookup"><span data-stu-id="9bab7-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="9bab7-109">Per altre informazioni, vedere [Procedura: Firmare un assembly con un nome sicuro](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9bab7-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="9bab7-110">**ID errore:** BC30140</span><span class="sxs-lookup"><span data-stu-id="9bab7-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bab7-111">Per correggere l'errore</span><span class="sxs-lookup"><span data-stu-id="9bab7-111">To correct this error</span></span>  
  
1. <span data-ttu-id="9bab7-112">Esaminare il messaggio di errore tra virgolette e consultare l'argomento [al. exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="9bab7-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="9bab7-113">per l'errore AL1019 ulteriori spiegazioni e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="9bab7-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="9bab7-114">Se l'errore persiste, raccogliere informazioni sulla situazione contingente e informare il Servizio Supporto Tecnico Clienti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9bab7-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bab7-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9bab7-115">See also</span></span>

- [<span data-ttu-id="9bab7-116">Procedura: Firmare un assembly con un nome sicuro</span><span class="sxs-lookup"><span data-stu-id="9bab7-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="9bab7-117">Pagina Firma, Creazione progetti</span><span class="sxs-lookup"><span data-stu-id="9bab7-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="9bab7-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="9bab7-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- <span data-ttu-id="9bab7-119">[Talk to Us](/visualstudio/ide/talk-to-us) (Comunicazioni con Microsoft)</span><span class="sxs-lookup"><span data-stu-id="9bab7-119">[Talk to Us](/visualstudio/ide/talk-to-us)</span></span>
