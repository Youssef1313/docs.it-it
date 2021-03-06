---
title: Eseguire la migrazione a scenari di cloud ibrido
description: Modernizzare le applicazioni .NET esistenti con il cloud di Azure e i contenitori di Windows | Eseguire la migrazione a scenari basati su cloud ibrido
ms.date: 04/30/2018
ms.openlocfilehash: 4348a9b538042fee7ebd9c08f480491f17425937
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2019
ms.locfileid: "72394537"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Eseguire la migrazione a scenari di cloud ibrido

Alcune organizzazioni e aziende non possono eseguire la migrazione di alcune applicazioni ai cloud pubblici, ad esempio Microsoft Azure o qualsiasi altro cloud pubblico a causa delle normative o dei propri criteri. Tuttavia, è probabile che qualsiasi organizzazione possa trarre vantaggio dalla presenza di alcune delle proprie applicazioni nel cloud pubblico e in altre applicazioni locali. Tuttavia, un ambiente misto può causare una complessità eccessiva negli ambienti grazie a piattaforme e tecnologie diverse usate in cloud pubblici e ambienti locali.

Microsoft offre la migliore soluzione cloud ibrida, una in cui è possibile ottimizzare le risorse esistenti in locale e nel cloud pubblico, garantendo la coerenza in un cloud ibrido di Azure. Puoi ottimizzare le competenze esistenti e ottenere un approccio flessibile e unificato per la creazione di app che possono essere eseguite nel cloud o in locale, grazie alla Azure Stack (locale) e ad Azure (cloud pubblico).

Per quanto riguarda la sicurezza, è possibile centralizzare la gestione e la sicurezza nel cloud ibrido. Puoi ottenere il controllo su tutti gli asset, dal tuo Data Center al cloud, fornendo Single Sign-On alle app locali e cloud. A tale scopo, estendere Active Directory a un cloud ibrido e usare la gestione delle identità.

Infine, è possibile distribuire e analizzare facilmente i dati, usare gli stessi linguaggi di query per le risorse cloud e locali e applicare analisi e apprendimento avanzato in Azure per arricchire i dati, indipendentemente dalla relativa origine.

## <a name="azure-stack"></a>Azure Stack

Azure Stack è una piattaforma cloud ibrida che consente di distribuire i servizi di Azure dal Data Center dell'organizzazione. Azure Stack è progettato per supportare nuove opzioni per le applicazioni moderne in scenari principali, ad esempio gli ambienti perimetrali e non connessi, o soddisfare requisiti di sicurezza e conformità specifici.

La figura 4-13 Mostra una panoramica della vera e propria piattaforma cloud ibrida offerta da Microsoft.

![Diagramma della piattaforma cloud ibrida Microsoft con Azure Stack e Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Figura 4-13.** Piattaforma cloud ibrida Microsoft con Azure Stack e Azure

Azure Stack è disponibile in due opzioni di distribuzione, per soddisfare le proprie esigenze:

- Sistemi integrati di Azure Stack

- Azure Stack Development Kit

### <a name="azure-stack-integrated-systems"></a>Sistemi integrati di Azure Stack

Azure Stack sistemi integrati sono offerti attraverso una partnership di Microsoft e dei partner hardware. La partnership crea una soluzione che offre un'innovazione basata sul cloud, bilanciata dalla semplicità di gestione. Poiché Azure Stack viene offerto come sistema integrato di hardware e software, si ottiene la giusta quantità di flessibilità e controllo, pur continuando ad adottare l'innovazione dal cloud. Azure Stack i sistemi integrati hanno una dimensione compresa tra 4 e 12 nodi e sono supportati congiuntamente dal partner hardware e da Microsoft. Usare Azure Stack sistemi integrati per implementare nuovi scenari per i carichi di lavoro di produzione.

### <a name="azure-stack-development-kit"></a>Azure Stack Development Kit

Microsoft Azure Stack Development Kit è una distribuzione a nodo singolo di Azure Stack, che è possibile utilizzare per valutare e ottenere informazioni sulle Azure Stack di. È anche possibile usare Azure Stack Development Kit come un ambiente di sviluppo, in cui è possibile sviluppare usando le API e gli strumenti coerenti con Azure. Azure Stack Development Kit non è destinato a essere utilizzato come ambiente di produzione.

### <a name="additional-resources"></a>Risorse aggiuntive

- **Cloud ibrido di Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Account del servizio Active Directory per i contenitori di Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Creare un contenitore con supporto Active Directory**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Gestione licenze Vantaggio Azure Hybrid**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Precedente](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Successivo](../walkthroughs-technical-get-started-overview.md)
